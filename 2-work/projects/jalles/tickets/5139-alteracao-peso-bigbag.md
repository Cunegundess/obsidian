---
id: 2025-08-14-qui-5139-alteracao-peso-bigbag
aliases:
  - 5139-alteracao-peso-bigbag
  - ticket-5139-alteracao-peso-bigbag
tags:
  - ticket
  - status/aguardando-retorno-cliente
criado: 2025-08-14-qui 15:51
estimativa: 2025-08-22-sex 23:59
prioridade: alta
projeto: Jalles
status: novo
---
## Descrição
> Temos um processo na Jalles, onde quando existe perda de açúcar durante a pesagem de um BigBag é possível que os operadores sinalizem no ANYTASK
> que este Lote precisa ser repesado e o mesmo não deve ser sincronizado com o SAP.
> Estamos com um problema onde mesmo com essa opção não selecionada e o Big Enviado ao SAP é possível realizar a alteração do peso.
> Tem se uma mensagem falando que não é possível a alteração, porém ainda assim é executada.

> **Danillo**
> "Como não há nenhuma identificação visual indicando que um lote está disponível para ser pesado. Pode ter levado a um entendimento incorreto do Zaqueu
> pois ao adicionar um lote a uma nova pesagem ele vai estar aberto para uma nova pesagem até um evento de nova pesagem, e eles podem estar distantes
> cronologicamente,
> e também podem ser feitos por operadores diferentes levando a um desentendimento, realizando os testes em ambiente de dev, não conseguimos replicar o que foi > reportado
> **Sugestão:** Ativar o campinho para alteração manual no admin"

Realizei os testes e acompanhei o fluxo do bigbag com o debug, e não encontrei nenhum fator que contribua para o ocorrido citado no ticket. O form de fato faz a validação
da pesagem do bigbag e bloqueia a execução (como é esperado) e como ele dispara um erro (ValidationError), ele impede a execução assim não permitindo que o bigbag seja enviado para o sap
Sendo assim, o Anytask está tendo o comportamento esperado e nada de anormal ou bug está ocorrendo, vale uma conversa pra entender melhor o ocorrido
Como também vale pontuar que como não há nenhuma identificação visual indicando que um lote está disponível para ser pesado. Pode ter levado a um entendimento incorreto entre os operadores

## Passos de Implementação
- [ ] Passo 1

## Anotações
- [x] Relatar o que foi encontrado no ticket
- Coloquei para status esperando retorno do cliente e documentei o que foi encontrado no ticket
- Zaqueu testou em QAS e confirmou que nada foi encontrado de fato, pendente testes em PRD

### Links Relacionados
- [Ticket no Movidesk](https://proxionhelpdesk.movidesk.com/Ticket/Edit/5056)
- [Commit]()
