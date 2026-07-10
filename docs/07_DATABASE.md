# ORGANIZADOR360
# DATABASE STANDARDS

Versão: 1.0
Status: Oficial
Data: 2026-07-10

---

# 1. Objetivo

Este documento define os padrões oficiais para modelagem, implementação, evolução e manutenção do banco de dados do Organizador360.

Todas as tabelas, índices, relacionamentos e migrations deverão seguir obrigatoriamente as regras aqui estabelecidas.

Este documento é a referência oficial para qualquer implementação relacionada ao banco de dados.

---

# 2. Banco Oficial

Sistema Gerenciador:

PostgreSQL

Versão mínima:

16

ORM Oficial:

SQLAlchemy 2.x

Migrações:

Alembic

---

# 3. Objetivos

A estrutura do banco deve priorizar:

- Integridade dos dados
- Performance
- Simplicidade
- Escalabilidade
- Facilidade de manutenção
- Auditoria
- Evolução contínua

---

# 4. Convenções Gerais

## Idioma

Todo o banco será desenvolvido utilizando inglês.

Exemplos:

users

vehicles

maintenance_records

subscriptions

notifications

documents

---

## Convenção

Utilizar sempre:

snake_case

---

## Tabelas

Utilizar nomes no plural.

Exemplos:

users

vehicles

notifications

maintenance_records

---

## Colunas

Sempre em snake_case.

Exemplos:

created_at

updated_at

deleted_at

first_name

last_login_at

---

## Chaves Primárias

Toda tabela utilizará:

id UUID

---

## Foreign Keys

Utilizar sempre:

<entity>_id

Exemplos:

user_id

vehicle_id

document_id

subscription_id

---

# 5. Estrutura Base das Tabelas

Toda tabela deverá possuir, sempre que aplicável:

id

created_at

updated_at

deleted_at

created_by

updated_by

deleted_by

---

## id

Tipo:

UUID

Não utilizar IDs sequenciais.

---

## created_at

Timestamp UTC.

Obrigatório.

---

## updated_at

Timestamp UTC.

Atualizado automaticamente.

---

## deleted_at

Utilizado para Soft Delete.

Nulo quando o registro estiver ativo.

---

## created_by

Identificador do usuário responsável pela criação.

---

## updated_by

Usuário responsável pela última alteração.

---

## deleted_by

Usuário responsável pela exclusão lógica.

---

# 6. Soft Delete

Todas as entidades de negócio utilizarão Soft Delete.

Exceções deverão ser documentadas através de ADR.

---

# 7. Auditoria

As seguintes operações deverão ser auditadas:

INSERT

UPDATE

DELETE

LOGIN

LOGOUT

ALTERAÇÃO DE SENHA

ALTERAÇÃO DE E-MAIL

ALTERAÇÃO DE PLANO

---

# 8. Tipos de Dados

Texto curto

VARCHAR

---

Texto longo

TEXT

---

Booleano

BOOLEAN

---

Inteiros

INTEGER

BIGINT

Quando necessário.

---

Valores monetários

NUMERIC(12,2)

Nunca utilizar FLOAT para valores financeiros.

---

Datas

TIMESTAMP WITH TIME ZONE

Sempre armazenadas em UTC.

---

Arquivos

Apenas metadados.

Nunca armazenar arquivos binários no banco.

---

# 9. Índices

Criar índices apenas quando houver justificativa técnica.

Priorizar índices em:

foreign keys

campos de busca

campos de autenticação

datas utilizadas em filtros

---

# 10. Constraints

Toda tabela deverá possuir:

Primary Key

Foreign Keys

Unique Keys

Check Constraints quando necessário.

---

# 11. Relacionamentos

Utilizar:

1:1

1:N

N:N

Sempre através de tabelas intermediárias.

Nunca utilizar listas serializadas em colunas.

---

# 12. Integridade Referencial

Todas as Foreign Keys deverão possuir comportamento explícito.

Exemplos:

RESTRICT

CASCADE

SET NULL

A decisão deverá ser documentada durante a modelagem.

---

# 13. Migrations

Todas as alterações ocorrerão exclusivamente através do Alembic.

É proibido alterar o banco manualmente em ambiente de produção.

---

## Convenção de nomes

As migrations deverão possuir nomes descritivos.

Exemplo:

create_users_table

add_vehicle_color

create_notifications_table

---

# 14. Seed

Dados iniciais deverão ser separados das migrations.

Seeds serão utilizados para:

configurações

categorias padrão

permissões

planos

parâmetros

---

# 15. Performance

Evitar:

SELECT *

Consultas desnecessárias

JOINs excessivos

Consultas dentro de loops

---

# 16. Normalização

Priorizar Terceira Forma Normal (3FN).

Desnormalizações somente quando houver ganho comprovado de desempenho.

---

# 17. Nomenclatura

Primary Key

pk_<table>

Exemplo:

pk_users

---

Foreign Key

fk_<table>_<referenced_table>

Exemplo:

fk_vehicles_users

---

Índice

idx_<table>_<column>

Exemplo:

idx_users_email

---

Unique

uq_<table>_<column>

---

Check

chk_<table>_<column>

---

# 18. Dados Sensíveis

Nunca armazenar:

senhas em texto

tokens permanentes

segredos

chaves privadas

Senhas deverão utilizar algoritmo seguro de hash.

---

# 19. Versionamento

Toda alteração estrutural deverá gerar nova migration.

Nunca editar migrations já executadas em produção.

---

# 20. Backup

A estratégia deverá permitir:

backup completo

backup incremental

restauração pontual

testes periódicos de recuperação

---

# 21. Escalabilidade

A modelagem deverá permitir:

particionamento futuro

replicação

balanceamento de leitura

arquivamento de históricos

---

# 22. Convenções para Novas Tabelas

Antes da criação de qualquer tabela, responder:

Qual módulo é proprietário?

Qual problema resolve?

Possui auditoria?

Possui Soft Delete?

Necessita índice?

Possui relacionamento?

Existe tabela semelhante?

---

# 23. Modelo Base de Entidade

Toda entidade deverá seguir, preferencialmente, o padrão:

id

created_at

updated_at

deleted_at

created_by

updated_by

deleted_by

status

---

Campos específicos serão adicionados conforme o domínio da entidade.

---

# 24. Responsabilidades

A modelagem deverá ser simples, previsível e consistente.

Toda decisão estrutural deverá priorizar manutenção e evolução futura da plataforma.

---

# 25. Considerações Finais

Este documento estabelece os padrões obrigatórios para toda a camada de persistência do Organizador360.

Nenhuma tabela, migration ou alteração estrutural deverá ser implementada em desacordo com estas diretrizes.

Mudanças que afetem os padrões definidos deverão ser registradas através de ADR e aprovadas antes da implementação.

---

# FIM DO DOCUMENTO