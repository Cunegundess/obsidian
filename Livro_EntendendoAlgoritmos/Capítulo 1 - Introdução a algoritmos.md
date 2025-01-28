
## Pesquisa Binária

A ideia desse algoritmo é começar a pesquisa pelo meio de um array / lista ordenada e a partir desse meio, verificar se o item é maior ou menor (alto ou baixo)
1. Caso maior, o algoritmo repete o mesmo passo na parte final do array
2. Caso menor, o algoritmo repete o mesmo passo na parte inicial do array 

```python
def pesquisa_binaria(lista, item): 
	baixo = 0 # (1.)
	alto = len(lista) - 1 # (1.) 

	while baixo <= alto: # (2.)
		meio = (baixo + alto) / 2 # (3.)
		chute = lista[meio]

		if chute == item: # (4.)
			return meio

		if chute > item: # (5.)
			alto = meio - 1
		else: # (6.)
			baixo = meio + 1

	return None # (7.)


minha_lista = [1, 3, 5, 7, 9] # (8.)

print(pesquisa_binaria(minha_lista, 3)) # => 1 (9.)
print(pesquisa_binaria(minha_lista, -1)) # => None (10.)
```


1. `baixo` e `alto` acompanham a parte da lista que você está procurando
2. Enquanto ainda não conseguiu chegar a um único elemento
3. Verifica o elemento central
4. Acha o item
5. O Chute foi muito alto
6. O Chute foi muito baixo
7. O item não existe
8. Vamos testá-lo
9. Lembre-se, as listas começam no 0. O próximo endereço tem índice 1
10. `None` significa nulo em Python. Ele indica que o item não foi encontrado


## Notação Big O

A notação Big O informa o quão rápido é um algoritmo. Por exemplo, imagine que você tem uma lista de tamanho `n`. O tempo de execução na notação Big O é `O(n)`. Onde estão os segundos? Eles não existem, a notação Big O não fornece o tempo em segundos. Ela permite que você compare o número de operações. Ela informa o quão rapidamente um algoritmo cresce

## A notação Big O estabelece o tempo de execução para a pior hipótese

Suponha que você utilize uma pesquisa simples para procurar o nome de uma pessoa em uma agenda telefônica. A pesquisa simples tem tempo de execução `O(n)`, o que significa que na pior das hipóteses terá verificado cada nome da agenda telefônica. Na melhor ou pior das hipóteses, a pesquisa simples tem tempo de execução `O(n)`.

1. A rapidez de um algoritmo não é medida em segundos, mas pelo crescimento do número de operações
2. Em vez disso, discutimos sobre o quão rapidamente o tempo de execução de um algoritmo aumenta conforme o número de elementos aumenta
3. O tempo de execução em algoritmos é expresso na notação Big O
4. `O(log n)` é mais rápido que `O(n)`, e `O(log n)` fica ainda mais rápido conforme a lista aumenta