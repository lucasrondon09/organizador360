# ORGANIZADOR360
# AI DEVELOPMENT GUIDE

Versão: 1.0  
Status: Oficial  
Data: 2026-07-10

---

# 1. Objetivo

Este documento define como ferramentas de Inteligência Artificial devem ser utilizadas durante o desenvolvimento do Organizador360.

O objetivo é permitir maior produtividade mantendo:

- qualidade;
- segurança;
- consistência;
- arquitetura definida;
- controle humano das decisões.

---

# 2. Princípio Fundamental

A IA é uma ferramenta de aceleração.

A IA:

- sugere;
- gera;
- analisa;
- documenta;
- revisa.

A IA não:

- define arquitetura sem aprovação;
- altera padrões existentes;
- cria soluções fora do projeto;
- substitui validação humana.

---

# 3. Contexto Obrigatório

Antes de gerar qualquer código, a IA deverá conhecer:

## Documentação base

Obrigatório consultar:

```
docs/

00_PROJECT_CONSTITUTION.md

01_PRODUCT_REQUIREMENTS.md

02_BUSINESS_RULES.md

03_PRODUCT_VISION.md

05_ARCHITECTURE.md

06_SYSTEM_DESIGN.md

07_DATABASE.md

08_BACKEND_GUIDELINES.md

09_FRONTEND_GUIDELINES.md

10_API_GUIDELINES.md

11_SECURITY.md

12_DESIGN_SYSTEM.md

13_UX_GUIDELINES.md
```

---

# 4. Regras Gerais para IA

A IA deverá:

- respeitar arquitetura existente;
- reutilizar componentes;
- evitar duplicação;
- seguir padrões definidos;
- criar testes;
- documentar alterações.

---

# 5. Proibições

A IA não deverá:

- criar novas tecnologias sem aprovação;
- alterar estrutura de pastas;
- modificar padrões arquiteturais;
- remover funcionalidades existentes;
- criar dependências desnecessárias.

---

# 6. Processo Oficial de Desenvolvimento com IA

Fluxo:

```
Requisito

↓

Análise IA

↓

Plano de implementação

↓

Aprovação humana

↓

Código

↓

Testes

↓

Revisão

↓

Merge
```

---

# 7. Antes de Criar Código

A IA deverá responder:

1. Qual módulo será alterado?

2. Qual problema será resolvido?

3. Quais arquivos serão criados?

4. Quais arquivos serão alterados?

5. Existe impacto no banco?

6. Existe impacto na API?

7. Existem riscos?

---

# 8. Criação de Novos Módulos

Antes de criar um módulo:

Consultar:

```
.ai/MODULE_CREATION_TEMPLATE.md
```

O módulo deverá possuir:

- documentação;
- regras de negócio;
- estrutura backend;
- estrutura mobile;
- testes;
- API.

---

# 9. Geração de Backend

Ao criar código backend a IA deverá seguir:

Obrigatório:

- FastAPI;
- arquitetura modular;
- Repository Pattern;
- Use Cases;
- Pydantic;
- SQLAlchemy;
- testes.

---

# 10. Geração de Frontend

Ao criar Flutter:

Obrigatório:

- Feature First;
- Riverpod;
- GoRouter;
- Design System;
- estados completos;
- testes.

---

# 11. Alterações no Banco

A IA deverá:

- criar migration;
- explicar impacto;
- validar relacionamentos;
- criar índices quando necessário.

Nunca alterar banco diretamente.

---

# 12. Criação de APIs

Toda API criada deverá possuir:

- endpoint;
- DTO;
- validação;
- autenticação;
- documentação OpenAPI;
- testes.

---

# 13. Geração de Testes

Toda implementação deverá gerar testes.

A IA deve considerar:

## Cenários positivos

Exemplo:

Cadastro realizado corretamente.

---

## Cenários negativos

Exemplo:

Dados inválidos.

---

## Casos extremos

Exemplo:

Datas inválidas.

---

# 14. Revisão por IA

A IA poderá revisar:

## Código

- qualidade;
- padrões;
- segurança.

## Arquitetura

- acoplamento;
- inconsistências.

## Testes

- cobertura;
- cenários ausentes.

---

# 15. Prompt Padrão de Desenvolvimento

Todo prompt deverá seguir:

```
CONTEXTO

Você está trabalhando no projeto Organizador360.

ARQUITETURA

Respeite os documentos oficiais.

OBJETIVO

Descreva a funcionalidade.

REGRAS

Informe restrições.

ENTREGA

Informe arquivos esperados.
```

---

# 16. Prompt para Nova Feature

Modelo:

```
Analise a criação da feature:

[NOME]

Antes de gerar código:

1. explique a arquitetura necessária;
2. liste arquivos criados;
3. liste arquivos alterados;
4. informe impactos;
5. aguarde aprovação.
```

---

# 17. Prompt para Código

Modelo:

```
Implemente a funcionalidade aprovada.

Siga:

- arquitetura definida;
- padrões do projeto;
- testes obrigatórios.

Não altere estruturas existentes sem autorização.
```

---

# 18. Prompt para Revisão

Modelo:

```
Faça uma revisão técnica.

Avalie:

- arquitetura;
- segurança;
- performance;
- testes;
- padrões.

Liste problemas encontrados.
```

---

# 19. Controle de Alterações

Toda alteração gerada por IA deverá possuir:

- descrição;
- arquivos modificados;
- justificativa;
- testes realizados.

---

# 20. Documentação Automática

A IA deve auxiliar na atualização:

- README;
- documentação técnica;
- changelog;
- OpenAPI.

---

# 21. Uso de Diferentes IAs

O projeto pode utilizar:

- ChatGPT;
- Claude;
- Gemini;
- Manus;
- GitHub Copilot;
- outras ferramentas.

Todas deverão seguir este documento.

---

# 22. Memória de Projeto

A IA deve utilizar como memória:

```
.ai/

MASTER_AI_RULES.md

BACKEND_AI_RULES.md

FLUTTER_AI_RULES.md

DATABASE_AI_RULES.md

ARCHITECTURE_AI_RULES.md
```

---

# 23. Validação Humana

Toda implementação deverá ser validada por um responsável.

A validação inclui:

- funcionamento;
- segurança;
- arquitetura;
- testes.

---

# 24. Segurança no Uso de IA

Nunca enviar para ferramentas externas:

- senhas;
- tokens;
- dados reais de usuários;
- informações privadas.

---

# 25. Evolução do Processo

Este guia deverá evoluir conforme:

- novas ferramentas;
- novos aprendizados;
- melhorias no fluxo.

---

# 26. Considerações Finais

O uso de Inteligência Artificial no Organizador360 tem como objetivo acelerar o desenvolvimento mantendo padrões profissionais.

A IA deve funcionar como um membro auxiliar da equipe de engenharia, seguindo regras claras e respeitando decisões arquiteturais.

---

# FIM DO DOCUMENTO