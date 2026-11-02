# Web-Security-Writeups - PortSwigger SQLi Labs

## Lab 1: SQL Injection vulnerability in WHERE clause allowing retrieval of hidden data 

**Objetivo:** Listar todos os produtos através do filtro de categoria.

**Vulnerabilidade encontrada:**
O parâmetro `?category=` estava concatenando direto no SQL. Ao injetar `'` deu erro 500.

**Meu processo:**
1. Testei `'` para descobrir se existe injeção.
2. Depois de descobrir injetei `'+OR+1=1-- e consegui listar todos os produtos, incluindo categorias que eles não conhecem 

**Payload final:**
```sql
'+OR+1=1--
