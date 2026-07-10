# ORGANIZADOR360
# MODULE SPECIFICATION
# SUBSCRIPTIONS - PLANOS E ASSINATURAS

Versão: 1.0  
Status: Oficial  
Data: 2026-07-10

---

# 1. Objetivo do Módulo

O módulo Subscriptions tem como objetivo gerenciar o modelo comercial do Organizador360.

Ele controla:

- planos disponíveis;
- assinatura dos usuários;
- pagamentos;
- permissões;
- recursos liberados.

---

# 2. Modelo de Negócio

O Organizador360 utilizará o modelo:

```
Freemium

+

Premium Subscription
```

---

# 3. Objetivo Estratégico

Permitir:

- entrada fácil de novos usuários;
- conversão para usuários pagantes;
- receita recorrente;
- crescimento sustentável.

---

# 4. Planos Iniciais

## Plano Free

Objetivo:

Aquisição de usuários.

Recursos:

- cadastro básico;
- quantidade limitada de veículos;
- histórico limitado;
- alertas básicos.

---

## Plano Premium

Objetivo:

Monetização.

Recursos:

- veículos ilimitados;
- histórico completo;
- documentos;
- armazenamento ampliado;
- alertas avançados;
- recursos inteligentes.

---

# 5. Plano Futuro

## Família

Permitir:

- múltiplos usuários;
- compartilhamento;
- gestão familiar.

---

# 6. Entidade Subscription

Campos:

```
id

user_id

plan_id

status

start_date

end_date

renewal_date

payment_provider

external_subscription_id

created_at

updated_at
```

---

# 7. Entidade Plan

Campos:

```
id

name

description

price

billing_period

features

active

created_at

updated_at
```

---

# 8. Status da Assinatura

Estados:

```
ACTIVE

TRIAL

PAUSED

CANCELLED

EXPIRED
```

---

# 9. Fluxo de Assinatura

```
Usuário

↓

Escolhe plano

↓

Pagamento

↓

Confirmação

↓

Ativação

↓

Liberação de recursos
```

---

# 10. Período de Teste

Possibilidade:

```
7 dias Premium grátis
```

Objetivo:

Aumentar conversão.

---

# 11. Controle de Recursos

O sistema deverá verificar:

Exemplo:

Usuário Free:

```
Máximo:
2 veículos
```

Usuário Premium:

```
Ilimitado
```

---

# 12. Feature Flags

Recursos deverão ser controlados por:

```
Feature Permission
```

Exemplo:

```
DOCUMENT_OCR

PREMIUM_ALERTS

UNLIMITED_VEHICLES
```

---

# 13. Regras de Negócio

## RN01

Todo usuário possui um plano.

---

## RN02

Usuário sem assinatura válida utiliza plano gratuito.

---

## RN03

Recursos Premium devem validar permissão antes do acesso.

---

## RN04

Cancelamento não remove dados existentes.

---

## RN05

Expiração retorna usuário para limitações do plano gratuito.

---

# 14. Integração Pagamentos

Plataformas:

## Android

Google Play Billing

---

## iOS

App Store Subscription

---

## Futuro Web

Possíveis:

- Stripe;
- Mercado Pago;
- outros gateways.

---

# 15. API

## Planos disponíveis

```
GET /api/v1/plans
```

---

## Assinatura atual

```
GET /api/v1/subscription
```

---

## Alterar plano

```
POST /api/v1/subscription/change
```

---

## Cancelar

```
POST /api/v1/subscription/cancel
```

---

## Restaurar compra

```
POST /api/v1/subscription/restore
```

---

# 16. Interface Mobile

Telas:

---

## Planos

Exibir:

- benefícios;
- preço;
- comparação.

---

## Minha Assinatura

Exibir:

- plano atual;
- validade;
- recursos.

---

## Upgrade

Fluxo:

```
Usuário Free

↓

Conhece benefício

↓

Assina Premium
```

---

# 17. Componentes Flutter

Widgets:

```
PlanCard

FeatureList

SubscriptionBadge

UpgradeBanner

PaymentButton
```

---

# 18. Experiência do Usuário

O aplicativo deve:

- destacar valor;
- evitar bloqueios agressivos;
- permitir uso gratuito inicial.

---

# 19. Métricas

Acompanhar:

## Conversão

Usuários Free → Premium

---

## Receita

- assinaturas ativas;
- MRR;
- churn.

---

## Uso

- recursos mais utilizados;
- pontos de conversão.

---

# 20. Indicadores SaaS

Métricas futuras:

## MRR

Monthly Recurring Revenue

---

## ARR

Annual Recurring Revenue

---

## Churn Rate

Cancelamentos.

---

## LTV

Valor do cliente.

---

# 21. Inteligência Artificial

Futuro:

IA poderá sugerir:

"Você utiliza frequentemente documentos e alertas. O plano Premium pode ajudar com automações."

---

# 22. Segurança

Obrigatório:

- validar pagamentos;
- evitar manipulação local;
- confirmar assinatura no servidor;
- proteger dados financeiros.

---

# 23. Testes Necessários

Backend:

- criação de plano;
- validação assinatura;
- expiração;
- permissões.

Mobile:

- exibição planos;
- fluxo compra;
- restauração.

---

# 24. Critérios de Aceitação

O módulo estará pronto quando:

- planos forem cadastrados;
- usuário possuir assinatura;
- permissões funcionarem;
- recursos premium forem protegidos.

---

# 25. Roadmap do Módulo

## Versão 1.0

- planos;
- controle de acesso;
- assinatura manual.

---

## Versão 1.1

- Google Play;
- App Store.

---

## Versão 1.2

- período teste;
- cupons.

---

## Versão 2.0

- plano família;
- marketplace;
- parceiros.

---

# 26. Considerações Finais

O módulo Subscriptions representa a camada comercial do Organizador360.

Ele permitirá transformar uma aplicação útil em um negócio sustentável baseado em receita recorrente.

---

# FIM DO DOCUMENTO