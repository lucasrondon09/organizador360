# ORGANIZADOR360
# API DEVELOPMENT GUIDELINES

Versão: 1.0
Status: Oficial
Data: 2026-07-10

---

# 1. Objetivo

Este documento define os padrões oficiais para desenvolvimento, evolução e documentação da API do Organizador360.

Todas as APIs deverão seguir obrigatoriamente estas diretrizes.

---

# 2. Objetivos

A API deve ser:

- previsível
- consistente
- documentada
- segura
- versionada
- escalável
- fácil de consumir
- compatível com OpenAPI

---

# 3. Arquitetura

A comunicação ocorrerá exclusivamente através de HTTPS.

Cliente

↓

REST API

↓

Application Layer

↓

Domain Layer

↓

Repository

↓

Database

A API será Stateless.

---

# 4. Versionamento

Toda API será versionada.

Formato oficial:

```
/api/v1/
```

Exemplos:

```
GET /api/v1/users

GET /api/v1/vehicles

POST /api/v1/auth/login
```

Mudanças incompatíveis deverão gerar nova versão.

---

# 5. Convenção de URLs

Utilizar substantivos.

Correto:

```
/users

/vehicles

/documents
```

Evitar verbos.

Errado:

```
/getUsers

/createVehicle

/deleteReminder
```

---

# 6. Métodos HTTP

GET

Consultar recursos.

POST

Criar recursos.

PUT

Atualização completa.

PATCH

Atualização parcial.

DELETE

Exclusão lógica quando aplicável.

---

# 7. Convenções de Endpoints

Listagem

```
GET /vehicles
```

Consulta

```
GET /vehicles/{id}
```

Criação

```
POST /vehicles
```

Atualização

```
PUT /vehicles/{id}
```

Atualização parcial

```
PATCH /vehicles/{id}
```

Exclusão

```
DELETE /vehicles/{id}
```

---

# 8. Formato das Requisições

Utilizar JSON.

Content-Type:

```
application/json
```

Uploads utilizarão multipart/form-data.

---

# 9. Formato das Respostas

Resposta de sucesso

```json
{
  "success": true,
  "data": {},
  "meta": {}
}
```

Resposta de erro

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed.",
    "details": []
  }
}
```

---

# 10. Códigos HTTP

200 OK

201 Created

204 No Content

400 Bad Request

401 Unauthorized

403 Forbidden

404 Not Found

409 Conflict

422 Unprocessable Entity

429 Too Many Requests

500 Internal Server Error

---

# 11. Paginação

Todas as listagens deverão suportar paginação.

Parâmetros:

page

page_size

Resposta:

```json
{
  "data": [],
  "pagination": {
    "page": 1,
    "page_size": 20,
    "total_items": 250,
    "total_pages": 13
  }
}
```

---

# 12. Ordenação

Parâmetros:

sort

order

Exemplo:

```
GET /vehicles?sort=name&order=asc
```

---

# 13. Pesquisa

Parâmetro padrão:

```
search
```

Exemplo:

```
GET /vehicles?search=Corolla
```

---

# 14. Filtros

Filtros serão opcionais.

Exemplo:

```
GET /maintenance?vehicle_id=UUID

GET /documents?status=ACTIVE
```

---

# 15. Autenticação

Utilizar JWT.

Header:

```
Authorization: Bearer TOKEN
```

Rotas públicas serão explicitamente identificadas.

---

# 16. Refresh Token

A renovação do token ocorrerá através de endpoint específico.

Exemplo:

```
POST /api/v1/auth/refresh
```

---

# 17. Upload

Fluxo:

Cliente

↓

Upload

↓

Validação

↓

Armazenamento

↓

Persistência dos metadados

↓

Resposta

---

# 18. Download

Downloads deverão ser autenticados quando envolverem informações privadas.

---

# 19. Idempotência

Operações PUT deverão ser idempotentes.

POST poderá criar novos recursos.

PATCH atualizará apenas campos informados.

---

# 20. Rate Limiting

Aplicar limites para evitar abuso.

Estratégia baseada em:

IP

Usuário autenticado

Endpoints críticos

---

# 21. Timeout

Toda requisição deverá possuir timeout configurado.

Operações demoradas deverão ser enviadas para processamento assíncrono.

---

# 22. Logs

Registrar:

- método
- endpoint
- usuário
- duração
- status HTTP

Nunca registrar:

- senhas
- tokens
- dados sensíveis

---

# 23. OpenAPI

Toda rota deverá possuir documentação.

Descrição

Resumo

Parâmetros

Respostas

Exemplos

Schemas

---

# 24. Convenção de Nomes

URLs

snake-case ou kebab-case conforme padrão definido para o projeto.

JSON

camelCase

Exemplo:

```json
{
  "vehicleName": "Corolla",
  "lastMaintenanceDate": "2026-07-10"
}
```

---

# 25. Versionamento da Documentação

Toda alteração em endpoints deverá atualizar:

OpenAPI

Swagger

Documentação do módulo

Testes

---

# 26. Compatibilidade

Evitar alterações incompatíveis.

Quando inevitáveis:

Criar nova versão da API.

Manter suporte à versão anterior durante o período definido no roadmap.

---

# 27. Testes

Toda API deverá possuir:

- testes unitários
- testes de integração
- testes de contrato
- documentação atualizada

---

# 28. Segurança

Toda entrada deverá ser validada.

Sanitizar dados recebidos.

Utilizar HTTPS.

Implementar proteção contra:

- SQL Injection
- XSS
- CSRF (quando aplicável)
- Força Bruta
- Enumeração de usuários

---

# 29. Checklist para Novos Endpoints

Antes de finalizar um endpoint verificar:

- URL definida
- Método HTTP correto
- DTOs criados
- Caso de uso implementado
- Testes criados
- OpenAPI atualizado
- Permissões definidas
- Logs implementados
- Tratamento de erros validado

---

# 30. Critérios de Qualidade

Toda API deverá ser:

- consistente
- previsível
- documentada
- segura
- testável
- performática
- versionada

---

# 31. Considerações Finais

A API do Organizador360 representa o contrato oficial entre o backend e todos os consumidores da plataforma.

Toda implementação deverá seguir rigorosamente os padrões estabelecidos neste documento, preservando compatibilidade, segurança e facilidade de evolução.

Mudanças incompatíveis deverão ser aprovadas previamente e registradas através de ADR.

---

# FIM DO DOCUMENTO