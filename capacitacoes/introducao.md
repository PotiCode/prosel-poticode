---
layout: training
title: Introdução — Módulo 1
permalink: /capacitacoes/introducao/
materiais:
  - titulo: "Slides — Introdução"
    arquivo: "introducao-slides.pdf"
    tipo: PDF
    descricao: "Apresentação com os conceitos principais do módulo"
  - titulo: "Exercícios Práticos"
    arquivo: "introducao-exercicios.zip"
    tipo: ZIP
    descricao: "Lista de exercícios para praticar em casa"
---

## TAD x ED

Tipos Abstratos de Dados (TAD) definem *o que* uma estrutura faz — suas operações e comportamentos — sem se preocupar com *como* está implementada. Estruturas de Dados (ED) são as implementações concretas desses tipos.

## Ponteiros e Iteradores

Ponteiros armazenam endereços de memória e permitem acesso direto a dados. Iteradores generalizam esse conceito para qualquer estrutura, fornecendo uma interface uniforme para percorrê-la sem expor detalhes internos.

## Estruturas de Dados Lineares

Estruturas lineares organizam os elementos em sequência. As principais são:

- **Array** — acesso direto por índice, tamanho fixo
- **Lista ligada** — tamanho dinâmico, percurso sequencial
- **Pilha** — LIFO (último a entrar, primeiro a sair)
- **Fila** — FIFO (primeiro a entrar, primeiro a sair)

## Tipos Abstratos de Dados

Um TAD é definido por um conjunto de valores e operações. Exemplo: a **Pilha** como TAD define `push`, `pop` e `peek` — a implementação pode usar array ou lista ligada sem alterar o contrato.
