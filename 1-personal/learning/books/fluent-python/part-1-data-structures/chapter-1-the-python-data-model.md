> Premature abstraction is as bad as premature optimization

**REPL:** read-eval-print loop
[Code Repository - GitHub](https://github.com/fluentpython/example-code-2e)

# Python Data Model
It is the API that are used to make the objects play well with the most idiomatic language features (**Pythonic**). 

You can think of the data model as a description of Python as a framework. It formalizes the interfaces of the building blocks of the language itself

>**Google NotebookLM**
>O modelo de Dados Python é a API que se utiliza para que os objetos definidos pelo usuário interajam bem com os recurso idiomáticos da linguagem

When using a framework, we spend a lot of time coding methods that are called by the framework. The same happens when we leverage the Python Data Model to build new classes. The Python interpreter invokes special methods to perform basic object operations, often triggered by special syntax. The special method names are always written with leading and trailing double underscores

>**Google NotebookLM**
>A essência de trabalhar com o Modelo de Dados é implementar métodos especiais (também chamados de *dunder methods*). O interpretador Python invoca esses métodos especiais para executar operações básicas, que são frequentemente acionadas por sintaxes especiais

We implement special methods when we want our objects to support and interact with fundamental language constructs such as Collections, Attribute Access, Interation (including asynchronous), Operator overloading, Function and method invocation, String representation and formatting, Asynchronous programming, Object creation and destruction, Managed contexts

> **Google NotebookLM**
> Ao implementar métodos especiais, seus objetos se comportam como os tipos embutidos, permitindo um estilo de codificação expressivo que é considerado Pythonic. Duas vantagens principais são:
> 
> 1. **Nomes Padrão:** Os usuários das suas classes não precisam memorizar nomes de métodos arbitrários para operações padrão
> 2. **Aproveitamento da Biblioteca Padrão:** Torna-se mais fácil tirar proveito da rica biblioteca padrão do Python, evitando a reinvenção da roda

## Pythonic Card Deck

















