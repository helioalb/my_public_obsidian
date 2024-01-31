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

## Concatenated index

Importante: Um index concatenado é APENAS UM índice para múltiplas colunas.

Exemplo:

| employee_id | subsidiary_id | employee |
| ---- | ---- | ---- |
| 1 | 20 | Fulano |
| 1 | 30 | Ciclano |
| 2 | 20 | Beltrano |

As chaves do índice vão ser algo do tipo `employee_id:subsidiary_id`. Exemplo: `1:20`, `1:30`, `2:20`. Ou `subsidiary_id:employee_id` . Exemplo: `20:1`, `30:1`, `20:2`.

### Exemplo lista telefônica

Para a tabela (phones) abaixo:

| last_name | first_name | phone |
| ---- | ---- | ---- |
| Alecrim | Ana | 111 |
| Alecrim | Helio | 222 |
| Alecrim | Maria | 333 |
| Alecrim | Mercedes | 444 |
| Baoba | Antonio | 555 |
| Baoba | Bruna | 666 |
| Baoba | Claudio | 777 |
| Baoba | Davi | 888 |
| Baoba | Maria | 999 |
| Campos | Elder | 000 |

Se o índice fosse `last_name:first_name`:

| index |
| ---- |
| Alecrim:Ana |
| Alecrim:Helio |
| Alecrim:Maria |
| Alecrim:Mercedes |
| Baoba:Antonio |
| Baoba:Bruna |
| Baoba:Claudio |
| Baoba:Davi |
| Baoba:Maria |
| Campos:Elder |

Busca com os dois termos:

```sql
SELECT phone FROM phones WHERE first_name='Helio' AND last_name='Alecrim';
```

Nesse caso a busca seria só no **index** (sem full table scan)


Busca feita somente pelo primeiro nome:

```sql
SELECT phone FROM phones WHERE first_name='Helio';
```

Nesse caso o índice não serve para nada, então um full scan table será necessário.

Aqui é que a busca é como se fosse na lista telefônica.

Imagina que a lista está assim:

Alecrim, Ana
Alecrim, Helio
Alecrim, Maria
Alecrim, Mercedes
Baoba, Antonio
Baoba, Bruna
Baoba, Claudio
Baoba, Davi
Baoba, Maria
Campos, Elder

Se quisermos encontrar todas as "Marias",  temos que "olhar" linha a linha. O índice, nesse caso, não serve para nada.

Porém, se invertermos a ordem das colunas, o índice passa a ser útil. Veja

Ana, Alecrim
Antonio, Baoba
Bruna, Baoba
Claudio, Baoba
Davi, Baoba
Elder, Campos
Helio, Alecrim
Maria, Alecrim
Maria, Baoba
Mercedes, Alecrim

A ordem com que o índice concatenado é criado diferencia a eficiência no momento da busca.
## Function based index
FBI - Function-based index

Exemplo:

```sql
CREATE INDEX emp_up_name ON employees (UPPER(last_name));
```
