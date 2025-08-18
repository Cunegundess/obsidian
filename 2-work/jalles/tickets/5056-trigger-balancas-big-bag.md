---
id: 2025-08-15-sex-5056-trigger-balancas-big-bag
aliases:
  - 5056-trigger-balancas-big-bag
  - ticket-5056-trigger-balancas-big-bag
tags:
  - ticket
  - status/novo
criado: 2025-08-15-sex 11:28
estimativa: ""
prioridade: media
projeto: Jalles
status: Em análise Técnica
---
## Descrição
>E conversa com o técnico Saymon, explicado uma necessidade de termos opção de habilitar e desabilitar a trigger por balanças quando não vermos a necessidade de subir informações para nosso banco de dados. Hoje temos apenas uma trigger para todos os equipamentos. Hoje na balança de big bag localizada no CDA 3 existe vários tipos de produtos e clientes para atender na produção. E quando a necessidade dessa troca de produto é necessário limpeza de linha por arraste de produto justamente pela balança de big bag. Sendo assim termos a opção de habilitar e desabilitar a trigguer via anydesk, quando houver necessidade.

> **Saymon**
> Será adicionado um atributo de status da balança no Anytask. A API que recebe os dados vai validar se o registro deve ou não ser salvo no BD.

## Passos de Implementação
- [x] Encontrar onde está esse trigger
  - Trigger é uma "procedure" do mssql
- [x] Criar condicionais para checar se a balança está ativa
- [ ] Debugar as condicionais que foram testadas (mandar os POST no endpoint que está descrito na função)

## Anotações
- Acredito que o if que checa os status da balança devem ser validados na função da production/views
  - def create_new_appointment_bigbag(json_content): linha 646
  - def new_appointment(request, new_appointment_type): linha 539 (onde faz o POST)

### Links Relacionados
- [Ticket no Movidesk](https://proxionhelpdesk.movidesk.com/Ticket/Edit/5056)
- [Commit]()
