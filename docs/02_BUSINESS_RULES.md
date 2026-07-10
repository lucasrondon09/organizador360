# ORGANIZADOR360
# BUSINESS RULES

Versão: 1.0  
Status: Oficial  
Data: 2026-07-10

---

# 1. Objetivo

Este documento define todas as regras de negócio do Organizador360.

As regras aqui descritas possuem prioridade sobre decisões de implementação.

Caso exista conflito entre código e este documento, este documento deve prevalecer.

---

# 2. Definições

## Regra de Negócio

Uma regra de negócio define como o sistema deve se comportar.

Ela não depende de linguagem de programação.

Ela não depende de banco de dados.

Ela não depende de interface.

---

# 3. Princípios Gerais

O sistema deve sempre priorizar:

- simplicidade
- previsibilidade
- segurança
- consistência
- histórico

---

Nenhuma informação importante deverá ser perdida sem confirmação explícita do usuário.

---

# 4. Usuários

## BR-001

Todo usuário deve possuir:

- identificador único
- nome
- e-mail
- senha (quando aplicável)
- data de criação
- status

---

## BR-002

O e-mail deve ser único.

---

## BR-003

Usuários desativados não podem autenticar.

---

## BR-004

Exclusão de conta deverá respeitar LGPD.

Os dados poderão ser:

- removidos
- anonimizados

conforme política definida.

---

# 5. Planos

Existirão inicialmente dois planos.

## Free

## Premium

---

## BR-005

Todo novo usuário inicia no plano Free.

---

## BR-006

Mudanças de plano nunca podem causar perda definitiva de dados.

Caso o usuário ultrapasse os limites do plano Free:

Os dados permanecerão armazenados.

Novos registros poderão ser bloqueados.

---

# 6. Histórico

## BR-007

Toda alteração relevante deve possuir histórico.

Sempre que possível registrar:

- usuário
- data
- ação

---

# 7. Exclusões

## BR-008

Antes de excluir informações importantes o sistema deve solicitar confirmação.

---

## BR-009

Sempre que possível utilizar Soft Delete.

---

# 8. Notificações

## BR-010

Nenhuma notificação poderá ser enviada após o usuário desativá-la.

---

## BR-011

Todo alerta deve possuir:

- origem
- categoria
- prioridade
- data
- usuário

---

## BR-012

Alertas vencidos poderão permanecer no histórico.

---

# 9. Arquivos

## BR-013

Arquivos enviados devem possuir:

- proprietário
- data
- tipo
- tamanho

---

## BR-014

Arquivos nunca deverão ficar públicos.

---

# 10. Dashboard

## BR-015

O Dashboard deve apresentar apenas informações relevantes.

Nunca exibir informações vazias apenas para preencher espaço.

---

## BR-016

O Dashboard deve ser personalizado conforme os módulos utilizados.

---

# 11. Módulo Histórico de Manutenção

## BR-100

Cada veículo pertence a apenas um usuário.

---

## BR-101

Um usuário pode possuir vários veículos.

---

## BR-102

Cada manutenção pertence a apenas um veículo.

---

## BR-103

Toda manutenção deve possuir data.

---

## BR-104

Valor da manutenção é opcional.

---

## BR-105

Comprovantes são opcionais.

---

## BR-106

O usuário pode criar categorias personalizadas.

---

## BR-107

Uma manutenção pode gerar automaticamente um próximo alerta.

Exemplo:

Troca de óleo.

Próxima troca:

5.000 km.

---

## BR-108

O sistema deve permitir alertas por:

- data
- quilometragem
- horas de uso

---

## BR-109

Excluir uma manutenção não exclui o veículo.

---

# 12. Central de Vencimentos

## BR-200

Uma conta pode ser:

- única
- recorrente

---

## BR-201

Recorrências suportadas:

- mensal
- bimestral
- trimestral
- semestral
- anual
- personalizada

---

## BR-202

Uma conta pode possuir parcelas.

---

## BR-203

Uma conta paga deve permanecer no histórico.

Nunca deve ser removida automaticamente.

---

## BR-204

Contas vencidas continuam visíveis até serem quitadas ou arquivadas.

---

# 13. Documentos

## BR-300

Todo documento pertence a um usuário.

---

## BR-301

Documentos podem possuir validade.

---

## BR-302

Caso exista validade:

O sistema deve permitir alertas.

---

## BR-303

Fotos e PDFs são opcionais.

---

# 14. Garantias (Futuro)

## BR-400

Produtos poderão possuir:

- nota fiscal
- manual
- garantia
- assistência técnica

---

# 15. Auditoria

## BR-500

Ações críticas devem ser registradas.

Exemplo:

- login
- alteração de senha
- alteração de e-mail
- exclusões
- upgrade de plano

---

# 16. Sincronização

## BR-600

O sistema deverá funcionar com sincronização futura entre dispositivos.

Nenhuma regra poderá impedir essa evolução.

---

# 17. Offline

## BR-601

O aplicativo deverá permitir operação offline sempre que possível.

A sincronização ocorrerá posteriormente.

---

# 18. Internacionalização

## BR-700

Todo texto exibido ao usuário deverá suportar tradução.

Nenhum texto poderá ficar fixo no código.

---

# 19. Segurança

## BR-800

Toda informação sensível deve trafegar criptografada.

---

## BR-801

Nunca armazenar senha em texto.

---

## BR-802

Tokens devem possuir tempo de expiração.

---

# 20. Evolução

Toda nova funcionalidade deverá responder:

- Qual problema resolve?

- Qual regra de negócio adiciona?

- Qual impacto possui?

- Pode reutilizar regras existentes?

Antes de criar novas regras, verificar se alguma regra existente pode ser reaproveitada.

---

# FIM DO DOCUMENTO