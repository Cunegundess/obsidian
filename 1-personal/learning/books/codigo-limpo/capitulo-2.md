
## Use nomes que revelem o seu propósito

O nome de uma variável, função ou classe deve responder a todas as grandes questões. Ele deve lhe dizer porque existe, o que faz e como é usado. Se um nome requer um comentário, então ele não revela seu propósito

```java
int d; // tempo decorrido em dias
```

O nome `d` não revela nada. Ele não indica a ideai de tempo decorrido, nem de dias. Devemos escolher um nome que especifique seu uso para mensuração e a unidade usada

```java
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
```

Escolher nomes que revelem seu propósito pode facilitar bastante o entendimento e a alteração do código

#### Qual o propósito deste código?

```java
public List<int[]> getThem() {
	List<int[]> list1 = new ArrayList<int[]>();
	for (int[] x : theList) {
		if (x[0] == 4) {
			list1.add(x);
		}
	return list1;
	}
}
```


O problema não é a simplicidade do código, mas seu aspecto implícito, isto é, o contexto não está explícito no código. Devido a isso, é necessário que saibamos as respostas para questões como:

1. Que tipos de coisas estão em `theList`? 
2. Qual a importância de um item na posição zero na `theList`?
3. Qual a importância do valor 4?
4. Como eu usaria a lista retornada?

As respostas para tais questões não estão presentes no exemplo do código, mas poderiam.

Digamos que estejamos trabalhando num jogo do tipo "campo minado". Percebemos que o tabuleiro é uma lista de células chamada `theList`. Vamos renomeá-las para `gameBoard`. Cada quadrado no tabuleiro é representado por um vetor simples. Mais tarde, descobrimos que a posição zero armazena um valor de status e que o valor 4 significa "marcado com uma bandeirinha" 

Ao dar esses nomes explicativos, podemos melhorar consideravelmente o código:

```java
public List<int[]> getFlaggedCells() {
	List<int[]> flaggedCells = new ArrayList<int[]>();
	for (int[] cell : gameBoard) {
		if (cell[STATUS_VALUE] == FLAGGED) {
			flaggedCells.add(cell);
		}
	return flaggedCells;
	}
}
```


Podemos continuar e criar uma classe simples para as células, em vez de usar um vetor `intS`. Ela pode ter uma função com um nome que revele seu propósito (chamada `isFlagged`, ou seja, "está marcada com uma bandeirinha") para ocultas os números mágicos. O resultado é uma nova versão da função:

```java
public List<Cell> getFlaggedCells() {
	List<Cell> flaggedCells = new ArrayList<Cell>();
	for (Cell cell : gameBoard) {
		if (cell.isFlagged()) {
			flaggedCells.add(cell);
		}
	return flaggedCells;
	}
}
```

Com essas simples alterações de nomes, não fica difícil entender o que entender o que está acontecendo. Esse é o poder de escolher bons nomes