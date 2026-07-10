# ORGANIZADOR360
# BACKEND DEVELOPMENT GUIDELINES

Versão: 1.0
Status: Oficial
Data: 2026-07-10

---

# 1. Objetivo

Este documento estabelece os padrões oficiais para o desenvolvimento do backend do Organizador360.

Seu objetivo é garantir consistência arquitetural, qualidade de código, facilidade de manutenção e previsibilidade durante todo o ciclo de vida da aplicação.

Todas as implementações deverão seguir obrigatoriamente estas diretrizes.

---

# 2. Stack Oficial

Linguagem:
- Python 3.13+

Framework:
- FastAPI

Validação:
- Pydantic v2

ORM:
- SQLAlchemy 2.x

Migrações:
- Alembic

Banco:
- PostgreSQL 16+

Cache:
- Redis

Background Jobs:
- Celery

Testes:
- Pytest

Documentação:
- OpenAPI / Swagger

---

# 3. Estrutura Geral

O backend será organizado utilizando uma arquitetura modular.

Cada módulo deverá possuir responsabilidades bem definidas e independentes.

Estrutura base:

backend/
    app/
        core/
        shared/
        modules/
        database/
        workers/

---

# 4. Organização dos Módulos

Todo módulo deverá seguir exatamente a mesma organização.

Exemplo:

modules/

maintenance/

    domain/

    application/

    infrastructure/

    presentation/

    tests/

Nenhuma camada poderá ser removida.

---

# 5. Responsabilidade das Camadas

## Domain

Contém:

- Entidades
- Value Objects
- Interfaces
- Regras de negócio
- Eventos de domínio

Não possui dependências externas.

---

## Application

Responsável pelos casos de uso.

Exemplos:

CreateVehicle

UpdateVehicle

DeleteVehicle

ListVehicles

FindVehicle

Não conhece banco de dados.

Não conhece HTTP.

---

## Infrastructure

Implementa:

- SQLAlchemy
- Redis
- Serviços externos
- Armazenamento
- Adaptadores

---

## Presentation

Responsável por:

- Endpoints
- Schemas
- DTOs
- Serialização
- Controllers

---

## Tests

Contém:

- Testes Unitários
- Integração
- Fixtures
- Mocks

---

# 6. Controllers

Os controllers devem possuir apenas:

- Receber requisições
- Validar entrada
- Invocar o caso de uso
- Retornar resposta

É proibido implementar regra de negócio em controllers.

---

# 7. Casos de Uso

Cada operação deverá possuir um caso de uso específico.

Exemplo:

CreateMaintenance

UpdateMaintenance

DeleteMaintenance

FindMaintenance

ListMaintenance

Cada caso de uso deverá executar apenas uma responsabilidade.

---

# 8. Repositories

Repositories são responsáveis exclusivamente pelo acesso aos dados.

É proibido implementar regras de negócio nesta camada.

---

# 9. Entidades

Entidades representam conceitos do domínio.

Exemplo:

Vehicle

MaintenanceRecord

Reminder

Document

Subscription

Devem conter comportamento relacionado ao domínio.

---

# 10. DTOs

Utilizar DTOs distintos para:

Entrada

Saída

Atualização

Filtros

Nunca reutilizar o mesmo DTO para múltiplos propósitos quando houver diferenças semânticas.

---

# 11. Validação

Toda validação deverá ocorrer utilizando Pydantic.

Validações de domínio deverão permanecer na camada Domain.

---

# 12. Injeção de Dependências

Todas as dependências deverão ser injetadas.

É proibido instanciar serviços diretamente dentro dos casos de uso.

---

# 13. Tratamento de Exceções

Utilizar exceções específicas.

Exemplos:

ValidationException

NotFoundException

UnauthorizedException

ForbiddenException

ConflictException

BusinessRuleException

Nunca lançar Exception genérica.

---

# 14. Padronização das Respostas

Respostas de sucesso:

- status
- data
- metadata (quando aplicável)

Respostas de erro:

- status
- code
- message
- details
- timestamp

---

# 15. Paginação

Todas as listagens deverão suportar paginação.

Parâmetros padrão:

page

page_size

sort

order

search

---

# 16. Filtros

Filtros deverão ser opcionais.

Exemplos:

status

date_from

date_to

user_id

vehicle_id

---

# 17. Ordenação

Sempre suportar ordenação por campos autorizados.

Nunca aceitar nomes de colunas arbitrários enviados pelo cliente.

---

# 18. Transações

Operações que alteram múltiplos registros deverão utilizar transações.

Rollback automático em caso de falha.

---

# 19. Logs

Registrar:

- autenticação
- erros
- exceções
- integrações
- operações críticas

Nunca registrar:

- senhas
- tokens
- dados sensíveis

---

# 20. Cache

Utilizar Redis apenas quando houver benefício comprovado.

Toda política de invalidação deverá estar documentada.

---

# 21. Background Jobs

Utilizar Celery para:

- envio de notificações
- geração de relatórios
- processamento de arquivos
- sincronizações

Não utilizar jobs para operações rápidas.

---

# 22. Upload de Arquivos

Fluxo:

Upload

↓

Validação

↓

Armazenamento

↓

Persistência dos metadados

↓

Resposta

Arquivos nunca deverão ser armazenados diretamente no banco.

---

# 23. Segurança

Toda rota deverá definir explicitamente:

Autenticação obrigatória?

Permissões necessárias?

Escopo de acesso?

---

# 24. Versionamento da API

Versão inicial:

/api/v1/

Alterações incompatíveis deverão gerar nova versão.

---

# 25. Convenções de Código

Seguir PEP 8.

Utilizar type hints em todo o projeto.

Evitar funções com mais de 50 linhas.

Evitar classes excessivamente grandes.

Priorizar composição em vez de herança.

---

# 26. Testes

Todo caso de uso deverá possuir testes.

Priorizar:

- Unitários
- Integração
- API

---

# 27. Cobertura

Meta mínima:

90%

Cobertura abaixo do limite deverá impedir merge na branch principal.

---

# 28. Documentação

Toda funcionalidade deverá atualizar:

- OpenAPI
- Documentação do módulo
- Testes

Implementações sem documentação serão consideradas incompletas.

---

# 29. Checklist para Novos Endpoints

Antes de concluir uma funcionalidade verificar:

- Caso de uso criado
- DTOs criados
- Repository criado
- Testes implementados
- Documentação atualizada
- OpenAPI revisada
- Logs definidos
- Permissões configuradas
- Tratamento de erros implementado

---

# 30. Critérios de Qualidade

Todo código deverá ser:

Legível

Testável

Reutilizável

Documentado

Consistente

Modular

Seguro

---

# 31. Considerações Finais

O backend do Organizador360 deverá permanecer modular, previsível e de fácil manutenção.

Toda implementação deverá respeitar as responsabilidades de cada camada, evitando acoplamento desnecessário e preservando a arquitetura definida nos documentos oficiais.

Mudanças arquiteturais deverão ser registradas por meio de ADR antes da implementação.

---

# FIM DO DOCUMENTO