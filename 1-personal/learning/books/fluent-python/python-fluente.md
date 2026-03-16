---
id: python-fluente
aliases:
  - python-fluente
tags: []
---

# python-fluente

> Eis um plano: se uma pessoa usar um recurso que você não entende, mate-a. É mais fácil que aprender algo novo,
> e em pouco tempos os únicos programadores sobreviventes usarão apenas um subconjunto minúsculo e fácil de entender
> de Python 0.9.6 <piscadela marota>
> *Tim Peters, lendário colaborador do CPython e autor do Zen de Python*

> Abstração Prematura é tão ruim quanto otimização prematura.

# Parte 1 - Estuturas de dados
## Capítulo 1. O modelo de dados de Python

- É a API que usamos para fazer nossos objetos lidarem bem com os recursos mais poderosos e característicos da linguagem

O interpretador de Python invoca métodos especiais para realizar operações básicas sobre os objetos, muitas vezes acionadas
por uma sintaxe especial (dunder methods). Por exemplo, a sintaxe `obj[key]` está amparada no método especial `__getitem__`.
Para resolver `my_collection[key]`, o interpretador chama `my_collection.__getitem__(key)`

> "É basicamente um estilo de mentalidade que visa aproveitar o máximo as funcionalidades da linguagem ao invés de criarmos nós mesmos"

## 1.2. Um baralho pythônico
