# 📘Sudoku Game – Java 21

Este projeto é uma implementação de um jogo de Sudoku em Java 21, executado totalmente pelo terminal.
O foco do código está no uso de estruturas de dados modernas, recursos atuais da linguagem e separação clara de responsabilidades utilizando Orientação a Objetos.

## 🧠 Objetivo do Projeto

Criar um jogo de Sudoku funcional utilizando conceitos fundamentais da linguagem, incluindo:

- Map para interpretar o tabuleiro inicial via argumentos (args)

- List<List<Space>> para modelar a matriz 9×9

- Recursos modernos do Java 21

- Classes responsáveis pelo jogo e pelo tabuleiro

- Entrada e controle do jogo via console

## 🧩 Como o tabuleiro é criado (usando args)

O jogo permite definir um tabuleiro inicial através dos argumentos passados no main.

Cada argumento segue o formato:

i,j=valor;fixo


Exemplo:

0,0=5;true
0,1=3;true
4,4=7;false


Esses argumentos são convertidos para um Map<String, String>:

    final var positions = Stream.of(args)
    .collect(toMap(
        k -> k.split(";")[0], // chave
        v -> v.split(";")[1]  // valor
    ));

✔ Vantagens:

Permite montar qualquer Sudoku inicial sem alterar o código.

Facilita testes e reuso.

O Map permite acesso rápido às células pré-definidas.

## 🗂️ Estrutura do Tabuleiro (List<List<Space>>)

O tabuleiro principal é modelado como:

List<List<Space>> spaces = new ArrayList<>();


Cada linha contém uma lista de Space, totalizando uma matriz 9x9.

Cada Space armazena:

expectedValue (valor correto)

currentValue (valor inserido pelo jogador)

fixed (se o número é inicial e não pode ser alterado)

✔ Vantagens:

Estrutura clara e flexível para representar o Sudoku

Encapsula as regras de cada célula

Facilita validação de linhas, colunas e quadrantes

## 🚀 Recursos do Java 21 Utilizados

O projeto aproveita diversas melhorias modernas da linguagem:

✔ var

Simplifica declarações e melhora legibilidade:

    var option = -1;

✔ switch moderno

    switch(option) {
    case 1 -> startGame(positions);
    case 2 -> inputNumber();
    case 3 -> removeNumber();
    ...
    }

✔ Streams + Collectors

Usado para transformar os args em Map dinamicamente:

    Stream.of(args).collect(toMap(...))

✔ Classes bem separadas (boa prática de OOP)

## 🎮 Funcionalidades do Jogo

O código implementa todas as funções básicas de um Sudoku:

▶ 1. Iniciar o jogo

Cria o tabuleiro com base nos argumentos e popula os espaços fixos.

▶ 2. Inserir números

O usuário escolhe a posição e o valor.

▶ 3. Remover números

Só remove valores que não são fixos.

▶ 4. Mostrar tabuleiro

O uso de um template (BoardTemplate) garante organização visual.

▶ 5. Analisar o estado do jogo

Confere:

- linhas,

- colunas,

- quadrantes,

- e se há erros.

▶ 6. Finalizar

Valida se o Sudoku foi completamente resolvido:

- Se sim: mostra mensagem final.

- Se não: informa erros.

▶ 7. Limpar o jogo

Mantém somente os valores fixos e apaga os inseridos.

## 🏗️ Arquitetura

- Main → controla o menu e fluxo do jogo

- Board → gerencia todos os espaços e regras

- Space → representa cada célula do tabuleiro

- BoardTemplate → formatação visual

Essa separação deixa o código:

- mais limpo,

- testável,

- escalável.


## 📚 Tecnologias & Conceitos Aplicados

- Java 21

- Orientação a Objetos

- Programação baseada em listas

- Uso de Map para construção dinâmica

- Manipulação de args

- Streams API

- Switch moderno

- Sistema de templates no console

## ✔ Conclusão

Este projeto demonstra de forma prática como construir um jogo estruturado com Java 21, usando conceitos essenciais da linguagem e aplicando boas práticas de arquitetura.
O Sudoku funciona inteiramente pelo console, mas com uma estrutura robusta e flexível para futuras expansões — como interface gráfica ou validações mais avançadas.
