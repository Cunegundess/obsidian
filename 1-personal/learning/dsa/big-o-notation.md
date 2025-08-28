denotar desempenho do algoritmo, não necessariamente uma medida de performance, mas sim de escalabilidade conforme o tamanho do input
pode ser usado para medir a complexidade temporal e complexidade espacial de um algoritmo

a complexidade temporal diz respeito ao tempo de execução - runtime
a complexidade espacial diz respeito ao quanto de espaço adicional a gente precisa alocar

sempre considerar o pior caso

# Principais Notations

**O(1)**: Significa tempo constante - memória constante. Independente do tamanho do input, ele tem o mesmo tempo de execução

**O(Log N)**: 
	- Conforme nosso input aumenta muito rápido, o nosso tempo de execução não aumenta tão rápido igual o input
	- Conforme o input aumenta exponencialmente, o tempo de execução aumenta linearmente
	- Exemplo de algoritmo com **O (Log N)** é a [[pesquisa-binaria]] ou binary search

**O(N)**: Temporal, ou seja, o tempo que o algoritmo leva cresce de forma proporcional ao tamanho do input

**O(N Log N)**:
	- Percorre todos os elementos do input **O(N)** e para cada um deles, faz algum processamento extra **O(Log N)** e assim sucessivamente (recursivamente)
	- Quase todos os algoritmos de sorting (quicksort, mergesort...), com exceção do bubblesort
	- Algoritmos DIVIDER AND CONQUER

**O(N²)**: 
	- Um loop dentro de um loop
	- Escala numa complexidade que para cada item do array ele checa todos os outros itens


# Referências
1. [Big O Notation | Estrutura de Dados e Algoritmos - Augusto Galego](https://app.hub.la/m/L8wi9vio7WPnWbmF8ZIO/p/MBnPacap)
2. [[notacao-big-o]]