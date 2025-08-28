---
id: 2025-08-15-sex-5056-trigger-balancas-big-bag
aliases:
  - 5056-trigger-balancas-big-bag
  - ticket-5056-trigger-balancas-big-bag
tags:
  - ticket
criado: 2025-08-15-sex 11:28
estimativa: ""
prioridade: media
projeto: Jalles
status: Aguardando retorno do cliente
---
## Descrição
>E conversa com o técnico Saymon, explicado uma necessidade de termos opção de habilitar e desabilitar a trigger por balanças quando não vermos a necessidade de subir informações para nosso banco de dados. Hoje temos apenas uma trigger para todos os equipamentos. Hoje na balança de big bag localizada no CDA 3 existe vários tipos de produtos e clientes para atender na produção. E quando a necessidade dessa troca de produto é necessário limpeza de linha por arraste de produto justamente pela balança de big bag. Sendo assim termos a opção de habilitar e desabilitar a trigguer via anydesk, quando houver necessidade.

> **Saymon**
> Será adicionado um atributo de status da balança no Anytask. A API que recebe os dados vai validar se o registro deve ou não ser salvo no BD.

## Passos de Implementação
- [x] Encontrar onde está esse trigger
  - Trigger é uma "procedure" do mssql
- [x] Criar condicionais para checar se a balança está ativa
- [x] Debugar as condicionais que foram testadas (mandar os POST no endpoint que está descrito na função)

## O que foi feito
Criei condicionais para validar se a balança está ativa ou não e também adicionei o campo `is_active` do model `DefaultBigBagProductionSettings` no admin

- Condicional adicionada nas funções `create_new_appointment_industry` e `create_new_appointment_bigbag` - views.py:
```python
def create_new_appointment_industry(json_content):
  # Valida se a balança industrial é "Toledo Fluxo"
  industry_terminal = DefaultBigBagProdutionSettings.objects.get(name=get_weight_terminal)
  if not industry_terminal.is_active:
      return

def create_new_appointment_bigbag(json_content):
  terminal_is_active = DefaultBigBagProdutionSettings.objects.get(weight_terminal=value)
  if not terminal_is_active.is_active:
      return

```

## Anotações
- Acredito que o if que checa os status da balança devem ser validados na função da production/views
  - def create_new_appointment_bigbag(json_content): linha 646
  - def new_appointment(request, new_appointment_type): linha 539 (onde faz o POST)

- Aguardar o saymon fazer o deploy, assim eu atualizo o ticket
  - Ticket atualizado e aguardando testes

### Links Relacionados
- [Ticket no Movidesk](https://proxionhelpdesk.movidesk.com/Ticket/Edit/5056)
- [Commit](https://gitlab.com/proxion/jalles-machado/alianca/-/commit/e0cde3a865d6c45ba09c350e2e4d2f80712eed85)
