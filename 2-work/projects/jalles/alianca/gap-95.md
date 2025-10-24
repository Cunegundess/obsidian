---
id: gap-95
aliases: []
tags: []
---

# anotacao
ultimo numeracao é o id do item da remessa
a primeira numeracao é o codigo da dt
http://localhost/app/picking_remessa_item_big_bag/0000128474/bigbag/1339/

- [x] nessa tela, adicionar ao form campo qty
- [x] criar novo model (consumo_parcial_bag_expedicao) que armazena lote, data, consumo em kg
- [x] toda vez que salvar verificar o peso original do lote informado se existe desse lote no consumo_parcial_bag_expedicao, tipo saldo
- [x] verificar se o peso informado é menor doq o salvo, se sim, deixa salvar
- [x] se o campo de qty tiver vazio, quer dizer que vai usar o lote inteiro
- [x] se preencher, tem que ser com qty menor que o saldo (ou lote cheio ou o quanto já foi subtraido)
