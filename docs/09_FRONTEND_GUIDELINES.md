# ORGANIZADOR360
# FRONTEND DEVELOPMENT GUIDELINES

Versão: 1.0
Status: Oficial
Data: 2026-07-10

---

# 1. Objetivo

Este documento estabelece os padrões oficiais para o desenvolvimento do aplicativo Flutter do Organizador360.

Seu objetivo é garantir consistência visual, organização da base de código, previsibilidade na implementação, facilidade de manutenção e excelente experiência para o usuário.

Todas as implementações deverão seguir obrigatoriamente estas diretrizes.

---

# 2. Stack Oficial

Framework

- Flutter

Linguagem

- Dart

Gerenciamento de Estado

- Riverpod

Navegação

- GoRouter

HTTP

- Dio

Persistência Local

- Hive

Notificações

- Firebase Cloud Messaging

Formatação

- intl

Testes

- flutter_test
- integration_test
- mocktail

---

# 3. Objetivos

O aplicativo deverá ser:

- rápido
- simples
- intuitivo
- consistente
- reutilizável
- modular
- acessível
- escalável

---

# 4. Organização da Aplicação

A aplicação será organizada por funcionalidades (Feature First).

Cada funcionalidade será independente das demais.

Estrutura lógica:

core/

shared/

features/

services/

widgets/

theme/

config/

routes/

---

# 5. Estrutura das Features

Toda Feature deverá seguir o mesmo padrão.

Exemplo:

maintenance/

pages/

widgets/

providers/

models/

repositories/

services/

states/

---

# 6. Responsabilidade das Camadas

Pages

Responsáveis apenas pela composição da interface.

Não implementam regras de negócio.

---

Widgets

Componentes reutilizáveis.

Devem ser pequenos e possuir única responsabilidade.

---

Providers

Gerenciam estado e comunicação com os casos de uso.

---

Repositories

Responsáveis pelo acesso à API.

Nunca implementam regras de negócio.

---

Models

Representação dos dados recebidos da API.

---

Services

Responsáveis por funcionalidades compartilhadas.

Exemplos:

- armazenamento
- notificações
- autenticação
- localização

---

# 7. Navegação

Toda navegação utilizará GoRouter.

Rotas deverão ser centralizadas.

É proibido utilizar navegação direta entre telas sem passar pelo roteador oficial.

---

# 8. Gerenciamento de Estado

Todo gerenciamento de estado utilizará Riverpod.

Evitar estados globais desnecessários.

Cada Feature deverá possuir seus próprios Providers.

---

# 9. Comunicação com Backend

Toda comunicação ocorrerá através do Dio.

Não realizar chamadas HTTP diretamente em Widgets ou Pages.

Fluxo:

Page

↓

Provider

↓

Repository

↓

API

↓

Resposta

---

# 10. Tratamento de Erros

Erros deverão ser tratados de forma consistente.

Categorias:

- validação
- autenticação
- autorização
- conexão
- servidor
- desconhecido

Mensagens técnicas nunca serão exibidas ao usuário.

---

# 11. Validação de Formulários

Toda validação deverá ocorrer antes do envio ao backend.

Validações críticas serão repetidas no backend.

---

# 12. Persistência Local

Utilizar Hive para:

- preferências
- cache
- configurações
- sessão

Nunca armazenar informações sensíveis em texto puro.

---

# 13. Autenticação

Fluxo:

Login

↓

Receber JWT

↓

Armazenamento seguro

↓

Interceptor

↓

Renovação automática do token

↓

Logout quando necessário

---

# 14. Interceptors

Toda comunicação HTTP deverá utilizar interceptors para:

- autenticação
- renovação de token
- logs
- tratamento de erros
- timeout

---

# 15. Design System

Toda interface seguirá o Design System oficial.

Não criar estilos diretamente dentro das telas.

Utilizar sempre:

- cores padronizadas
- tipografia oficial
- componentes reutilizáveis
- espaçamentos padronizados

---

# 16. Componentes Compartilhados

Sempre reutilizar componentes.

Exemplos:

Botões

Cards

Dialogs

Bottom Sheets

SnackBars

Campos de texto

Indicadores de carregamento

---

# 17. Responsividade

O aplicativo deverá adaptar-se a:

- smartphones
- tablets
- telas dobráveis (quando aplicável)

Evitar medidas fixas.

---

# 18. Tema

Todo o aplicativo utilizará ThemeData centralizado.

Não definir cores diretamente em Widgets.

---

# 19. Acessibilidade

Garantir:

- contraste adequado
- tamanho mínimo para toque
- textos legíveis
- suporte a leitores de tela
- navegação consistente

---

# 20. Internacionalização

Toda string exibida ao usuário deverá suportar internacionalização.

Nunca utilizar textos fixos diretamente nos Widgets.

---

# 21. Performance

Evitar:

- rebuilds desnecessários
- listas sem paginação
- consultas repetidas
- widgets excessivamente grandes

Priorizar Lazy Loading sempre que possível.

---

# 22. Offline

A aplicação deverá funcionar parcialmente sem conexão.

Quando aplicável:

- cache local
- sincronização futura
- fila de operações

---

# 23. Upload de Arquivos

Fluxo:

Selecionar arquivo

↓

Validar

↓

Enviar

↓

Acompanhar progresso

↓

Atualizar interface

---

# 24. Notificações

Utilizar Firebase Cloud Messaging.

Todas as notificações deverão possuir:

- título
- mensagem
- ação
- identificação do módulo

---

# 25. Testes

Toda Feature deverá possuir:

- testes de widgets
- testes unitários
- testes de integração (quando necessário)

---

# 26. Convenções de Código

Seguir Effective Dart.

Utilizar:

- nomes descritivos
- classes pequenas
- métodos curtos
- composição
- tipagem forte

Evitar duplicação de código.

---

# 27. Tratamento de Estados

Toda tela deverá contemplar:

- carregando
- sucesso
- vazio
- erro

Nunca deixar estados indefinidos.

---

# 28. Checklist para Nova Feature

Antes de concluir uma Feature verificar:

- Rotas criadas
- Providers criados
- Repository implementado
- Models criados
- Testes implementados
- Strings internacionalizadas
- Componentes reutilizados
- Design System respeitado
- Documentação atualizada

---

# 29. Critérios de Qualidade

Toda Feature deverá ser:

- intuitiva
- rápida
- reutilizável
- acessível
- testável
- consistente
- documentada

---

# 30. Considerações Finais

O aplicativo Organizador360 deverá oferecer uma experiência consistente, previsível e de alta qualidade.

Todas as implementações deverão respeitar os padrões definidos neste documento, preservando a arquitetura da aplicação e garantindo evolução sustentável ao longo do tempo.

Mudanças estruturais deverão ser registradas por meio de ADR antes da implementação.

---

# FIM DO DOCUMENTO