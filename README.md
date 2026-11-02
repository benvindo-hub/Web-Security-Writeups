# Web-Security-Writeups - PortSwigger SQLi Labs

## Lab 3: SQL Injection UNION attack, determining the number of columns returned by the query

**Objetivo:** Descobrir o número total de colunas através do filtro de categoria.

**Vulnerabilidade encontrada:**
no parâmetro `?Category=` estava concatenando direto no SQL. Ao injetar `'` deu erro 500.

**Meu processo:**
1. Descobri o número de colunas com `'+UNION+SELECT+NULL,NULL,NULL,NULL--' são 3 colunas.

**Payload final:**
```sql
'+UNION+SELECT+NULL,NULL,NULL,NULL--
