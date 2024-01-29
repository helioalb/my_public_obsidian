---
title: SQL Performance Explained
link: https://use-the-index-luke.com/sql/table-of-contents
tags:
  - database
---
O index pode ser comparado ao indice remissivo dos livros: O que tem lá não altera o conteúdo original do livro. É informação redundante. Porém, está ordenado por algum critério (ordem alfabética) e cada entrada aponta para o local onde o conteúdo original está.

O que difere o indice do livro com um index no banco de dados é o dinamismo. Enquanto no livro não é possível adicionar ou remover novos dados (a não ser que seja na próxima edição), no banco de dados, a cada adição/remoção o indice é reorganizado.

No caso do banco de dados, para que seja possível inserir novas entradas ao index com baixo custo, usa-se [[Doubly Linked List]].

## Index leaf nodes

Pense em blocos com com índices ordenados. Pense também que cada bloco desses é um node de uma [[Doubly Linked List]]. Isso são os **Index leaf nodes** . Cada linha do bloco aponta para os dados reais na tabela
Cada linha dentro do bloco contém o indice e o endereço fisico da linha onde se encontra os dados completos ao qual o indice se refere.
Exemplo:

![[database_blocks.png]]
Diferente do índice, que usa a [[Doubly Linked List]] como parte da estrutura, a tabela usa [[Heap Structure]]

## Search tree (B-tree = Balanced tree)

Ao procurar por um leaf node, poderíamos percorrer a [[Doubly Linked List]], no entanto, numa tabela com muitas entradas (bilhões, por exemplo) isso é inviável (imagine que o leaf node procurado é o último da lista). Para isso, a estrutura de [[Binary Search Trees]] (principalmente a B-tree) é mais útil. Veja o exemplo:
![[binary-search-tree.png]]

## Index lookup
Um index lookup envolve três passos: Percorrer a árvore, seguir o leaf node chain ([[Doubly Linked List]]), pegar o dado na tabela.

O "percorrer a árvore", que tem um limite superior (se a árvore tem profundidade 5, por exemplo, esse é o máximo de passos que vão existir na busca.)

Com exceção do "percorrer a árvore", que tem um limite superior, as etapas podem ter muitas operações (percorrer muito da [[Doubly Linked List]] e buscar vários dados no disco). Com isso é possível perceber que, mesmo com índice, a busca ainda pode ser lenta.

## Cláusula where

Uma cláusula where mal escrita é  primeiro ingrediente para queries lentas.

```
obs: a primary key de uma tabela tem um índice. Mesmo que não tenhamos feito um CREATE INDEX ...
```


## Function based index
FBI - Function-based index

Exemplo:

```sql
CREATE INDEX emp_up_name ON employees (UPPER(last_name));
```
