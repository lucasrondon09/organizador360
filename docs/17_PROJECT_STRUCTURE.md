# ORGANIZADOR360
# PROJECT STRUCTURE GUIDELINES

Versão: 1.0  
Status: Oficial  
Data: 2026-07-10

---

# 1. Objetivo

Este documento define a estrutura oficial do repositório Organizador360.

Seu objetivo é estabelecer responsabilidades para cada diretório, garantindo organização, escalabilidade e facilidade de manutenção.

Nenhum arquivo deverá ser criado fora da estrutura definida sem justificativa técnica.

---

# 2. Estrutura Geral do Projeto

Estrutura oficial:

```
organizador360/

├── .ai/

├── .github/

├── adrs/

├── api/

├── backend/

├── diagrams/

├── docker/

├── docs/

├── mobile/

├── prompts/

├── scripts/

├── README.md

├── ROADMAP.md

├── CHANGELOG.md

└── docker-compose.yml
```

---

# 3. Diretório .ai

Responsável pelas regras utilizadas por ferramentas de Inteligência Artificial.

Estrutura:

```
.ai/

├── MASTER_AI_RULES.md

├── BACKEND_AI_RULES.md

├── FLUTTER_AI_RULES.md

├── DATABASE_AI_RULES.md

├── API_AI_RULES.md

├── ARCHITECTURE_AI_RULES.md

├── SECURITY_AI_RULES.md

├── TESTING_AI_RULES.md

├── DEVOPS_AI_RULES.md

├── DOCUMENTATION_AI_RULES.md

└── MODULE_CREATION_TEMPLATE.md
```

---

Responsabilidade:

- padrões para IA;
- prompts internos;
- regras de geração;
- validações.

Nunca armazenar código da aplicação.

---

# 4. Diretório .github

Responsável pela automação do GitHub.

Estrutura:

```
.github/

├── ISSUE_TEMPLATE/

├── workflows/

└── PULL_REQUEST_TEMPLATE.md
```

---

Responsabilidade:

- CI/CD;
- validações automáticas;
- templates;
- automações.

---

# 5. Diretório ADRS

Responsável pelas decisões arquiteturais.

Estrutura:

```
adrs/

ADR-001-stack-tecnologica.md

ADR-002-arquitetura-modular.md
```

---

Utilizado para registrar:

- mudanças arquiteturais;
- decisões técnicas;
- justificativas.

---

# 6. Diretório API

Responsável pela documentação da API.

Estrutura:

```
api/

openapi.yaml
```

---

Responsabilidade:

- contrato da API;
- schemas;
- documentação OpenAPI.

Nunca conter implementação.

---

# 7. Diretório Backend

Responsável pelo código servidor.

Estrutura:

```
backend/

├── app/

├── docker/

├── scripts/

└── tests/
```

---

# 8. Backend/app

Código principal da aplicação.

Estrutura:

```
app/

├── core/

├── shared/

├── modules/

├── database/

├── workers/

└── main.py
```

---

## core

Responsável por:

- configurações;
- segurança;
- autenticação;
- recursos fundamentais.

---

## shared

Código reutilizado por múltiplos módulos.

Exemplos:

- helpers;
- exceptions;
- middlewares.

---

## modules

Contém funcionalidades do sistema.

Exemplo:

```
modules/

vehicles/

maintenance/

documents/

notifications/
```

---

Cada módulo segue:

```
module/

├── domain/

├── application/

├── infrastructure/

├── presentation/

└── tests/
```

---

# 9. Diretório Backend/tests

Testes backend.

Estrutura:

```
tests/

├── unit/

├── integration/

├── factories/

└── fixtures/
```

---

# 10. Diretório Mobile

Responsável pelo aplicativo Flutter.

Estrutura:

```
mobile/

├── assets/

├── lib/

└── test/
```

---

# 11. Mobile/lib

Estrutura:

```
lib/

├── core/

├── shared/

├── features/

├── routes/

├── theme/

├── services/

└── main.dart
```

---

# 12. Features Mobile

Cada funcionalidade deverá possuir:

```
feature/

├── pages/

├── widgets/

├── providers/

├── models/

├── repositories/

├── services/

└── states/
```

---

# 13. Diretório Docs

Responsável pela documentação oficial.

Estrutura:

```
docs/

├── documentos técnicos

├── modules/

└── templates/
```

---

# 14. Docs/modules

Documentação específica dos módulos.

Exemplo:

```
modules/

dashboard.md

maintenance.md

documents.md

notifications.md
```

---

Cada módulo deverá documentar:

- objetivo;
- regras;
- telas;
- API;
- banco;
- fluxos.

---

# 15. Docs/templates

Modelos oficiais.

Utilizados para:

- novos módulos;
- APIs;
- features;
- ADRs.

---

# 16. Diretório Diagrams

Responsável por diagramas.

Exemplos:

```
architecture.md

database.md

user-flows.md
```

---

Pode conter:

- Mermaid;
- modelos;
- fluxos.

---

# 17. Diretório Docker

Responsável por arquivos relacionados à infraestrutura.

Exemplos:

- containers;
- imagens;
- configurações.

---

# 18. Diretório Prompts

Responsável pelos prompts utilizados durante desenvolvimento.

Exemplo:

```
prompts/

feature-generation.md

code-review.md

documentation.md
```

---

# 19. Diretório Scripts

Scripts auxiliares.

Exemplos:

- instalação;
- manutenção;
- automação;
- migração.

---

# 20. Arquivos Principais

## README.md

Apresentação geral do projeto.

---

## ROADMAP.md

Planejamento futuro.

---

## CHANGELOG.md

Histórico de versões.

---

## docker-compose.yml

Orquestração dos serviços locais.

---

# 21. Regras Gerais

É proibido:

- criar pastas sem necessidade;
- duplicar documentos;
- misturar código e documentação;
- armazenar arquivos temporários;
- versionar segredos.

---

# 22. Nomenclatura

Diretórios:

snake_case

Arquivos:

snake_case

Documentos:

MAIÚSCULO quando forem documentos oficiais.

---

# 23. Evolução da Estrutura

Alterações estruturais deverão:

- possuir justificativa;
- avaliar impacto;
- registrar ADR quando necessário.

---

# 24. Organização para IA

Ao solicitar criação de código para IA:

Sempre informar:

- caminho do arquivo;
- responsabilidade;
- arquivos relacionados.

Exemplo:

```
Criar:

backend/app/modules/maintenance/domain/entity.py

Responsabilidade:

Entidade de domínio de manutenção.
```

---

# 25. Considerações Finais

A estrutura do repositório representa a organização arquitetural do Organizador360.

Manter essa estrutura é essencial para garantir:

- desenvolvimento escalável;
- colaboração eficiente;
- uso correto de IA;
- facilidade de manutenção.

---

# FIM DO DOCUMENTO