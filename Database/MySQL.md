---
tags:
  - database
---
## MySQL Explain
Exemplo de explain:

```sql
EXPLAIN SELECT * FROM employee WHERE id = 25;
```

| id | select_type | table | partitions | type | possible_keys | key | key_len | ref | rows | filtered | Extra |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | SIMPLE | ps_employee | NULL | const | PRIMARY,id_employee_passwd | PRIMARY | 4 | const | 1 | 100.00 | NULL |

### Type

#### eq_ref, const
Usa uma busca binária na B-Tree para encontrar uma única linha. O banco usa essa estratégia se a busca é numa primary_key ou a coluna tem uma constraint unique.

#### ref, range

Usa a B-Tree para chegar até os *leaf nodes* (Ver [[Livro SQL Performance Explained]], depois percorre os leaf nodes procurando pelo critério da busca.

#### index

Lê o índice todo (index full scan)

#### ALL

Lê toda a tabela (linhas e colunas) - full table scan

#### Using Index (in the “Extra” column)

Nesse caso a tabela não é acessada, pois o index tem todos os dados requeridos.

