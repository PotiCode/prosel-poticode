---
layout: training
title: HTML
permalink: /capacitacoes/html/
---


> Material de apoio para aula. Cobre desde os conceitos básicos de marcação até as regras de semântica moderna.

---

## 1. O que é o HTML?

O **HTML** (HyperText Markup Language) é a linguagem de marcação padrão para criar páginas web. É importante entender que ele **não é uma linguagem de programação**, pois não possui lógica condicional ou loops; ele serve para dar **significado** e **estrutura** aos dados.

* **Hipertexto**: Refere-se aos links que conectam páginas entre si.
* **Marcação**: O uso de etiquetas (tags) para "anotar" o conteúdo.

---

## 2. Anatomia de um Elemento

A maioria dos elementos HTML segue este padrão básico:

1. **Tag de Abertura** (`<p>`): Indica onde o elemento começa.
2. **Conteúdo**: O texto ou imagem que será exibido.
3. **Tag de Fechamento** (`</p>`): Indica o fim do elemento (marcado pela barra `/`).
4. **Atributos**: Informações extras dentro da tag de abertura.
   * Exemplo: `<a href="https://google.com">Link</a>` (onde `href` é o atributo).

---

## 3. A Estrutura Básica (O "Esqueleto")

Todo arquivo HTML deve começar com esta estrutura para ser interpretado corretamente pelos navegadores:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título da minha aula</title>
</head>
<body>
    </body>
</html>

```

### Detalhamento dos Componentes:

* **DOCTYPE**: Avisa ao navegador que estamos usando a versão HTML5.
* **HTML lang="pt-br"**: Define o idioma da página para tradutores e acessibilidade.
* **META charset="UTF-8"**: Permite a exibição correta de caracteres como acentos e cedilha.
* **META name="viewport"**: Essencial para a responsividade (ajuste automático em celulares).
* **HEAD**: Área técnica. Contém metadados, título da aba e links para CSS (invisível ao usuário).
* **BODY**: O corpo do site. Tudo o que for colocado aqui será visível no navegador.

---

## 4. Tags de Conteúdo Frequentes

### 4.1 Títulos e Textos

* **h1 até h6**: Títulos em ordem de importância. Use apenas um `<h1>` por página.
* **p**: Define um parágrafo.
* **strong**: Destaca o texto em negrito (importância semântica).
* **em**: Texto em itálico (ênfase).

### 4.2 Listas

* **ul**: Lista não ordenada (com marcadores/bolinhas).
* **ol**: Lista ordenada (numerada 1, 2, 3...).
* **li**: Item de lista (obrigatório dentro de `<ul>` ou `<ol>`).

### 4.3 Mídias e Links

* **a href="URL"**: Cria um link para outra página ou arquivo.
* **img src="caminho" alt="descrição"**: Insere uma imagem.
* *O atributo `alt` é fundamental para acessibilidade.*



---

## 5. Semântica: Por que é importante?

A semântica ajuda o Google (SEO) e leitores de tela a entenderem a função de cada parte do seu layout. As principais tags são:

* **header**: Cabeçalho principal.
* **nav**: Contém os menus de navegação.
* **main**: Conteúdo principal e central da página.
* **article**: Um conteúdo independente, como um post de blog.
* **section**: Uma seção temática dentro da página.
* **aside**: Conteúdo lateral relacionado (barras laterais).
* **footer**: Rodapé com contatos e créditos.

---

## 6. Formulários (Interação)

Essenciais para coletar dados dos usuários:

* **form**: O container que engloba os campos.
* **label**: O rótulo que explica o que digitar (ex: "E-mail:").
* **input**: O campo de entrada (tipos: text, email, password, submit).

---

## 7. Conceitos-chave para Revisão

* [ ] HTML é linguagem de programação ou de marcação?
* [ ] Qual a função do `<head>` em comparação ao `<body>`?
* [ ] Por que o atributo `alt` nas imagens é obrigatório?
* [ ] O que é uma tag semântica e por que usá-la?
* [ ] Qual a diferença prática entre `<ul>` e `<ol>`?

---

> **Referências de Estudo**
> * **MDN Web Docs**: A documentação oficial da Mozilla para desenvolvedores.
> * **W3C**: O consórcio que mantém os padrões da Web.
> * **Livro**: *HTML e CSS: projete e construa websites* (Jon Duckett).
> 
> 

```

```
