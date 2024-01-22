---
title: SQL Performance Explained
link: https://use-the-index-luke.com/sql/table-of-contents
tags:
  - database
---
O index pode ser comparado ao indice remissivo dos livros: O que tem lá não altera o conteúdo original do livro. É informação redundante. Porém, está ordenado por algum critério (ordem alfabética) e cada entrada aponta para o local onde o conteúdo original está.

O que difere o indice do livro com um index no banco de dados é o dinamismo. Enquanto no livro não é possível adicionar ou remover novos dados (a não ser que seja na próxima edição), no banco de dados, a cada adição/remoção o indice é reorganizado.

No caso do banco de dados, para que seja possível inserir novas entradas ao index com baixo custo, usa-se [[Doubly Linked List]].