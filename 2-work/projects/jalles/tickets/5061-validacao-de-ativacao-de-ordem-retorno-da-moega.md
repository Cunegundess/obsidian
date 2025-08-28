---
id: 5061-validacao-de-ativacao-de-ordem-retorno-da-moega
aliases: []
tags:
  - card
  - ticket
criado: 2025-08-22-sexT14:56
---
## Descrição
- [ ] > **Zaqueu**: Precisamos de um campo de programação nas ordens do tipo Semi Acabado e Indústria,
onde se possível inserir data e hora ao qual no momento informado nestes campos a ordem se ativar automaticamente e desativar a ordem anterior.

No Anytask, será reaproveitado ou criado um campo de data e hora, para as ordens de semi acabado e indústria. Em que seja possível ativar automaticamente uma OP
e também desativar a OP anterior. Se esse campo não for preenchido, segue o fluxo normal

> **Definição final do Zaqueu**: Em conversa com o Saymon iremos utilizar o campo já existente "Data de iniício" ignorando a data enviada pelo SAP. 
Sendo assim esse campo viria sempre em branco no ANYTASK e somente após o preenchimento ele seria encotrado pelo JOB para ativação da ordem no dia e hora previstos.

## Passos
- [x] Verificar se pode reaproveitar o campo `start_date = row["DATA_INI"]`
- [x] Adicionar no list display a dt ini e dt update formatado

## Anotações
- Commit criado e ticket atualizado dia 25/07/25

### Links Relacionados
- [Ticket no Movidesk](https://proxionhelpdesk.movidesk.com/Ticket/Edit/5061)
- [Commit](https://gitlab.com/proxion/jalles-machado/alianca/-/commit/a5dd4e85c7aae4bbae26d5229a0dd5686d5760b5)

