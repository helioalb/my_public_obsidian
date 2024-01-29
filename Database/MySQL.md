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
Usa uma busca binária na B-Tree. O banco usa essa estratégia se a busca é numa primary_key ou a coluna tem uma constraint unique.

