# Web-Security-Writeups - PortSwigger SQLi Labs

## Lab 2: SQL Injection vulnerability allowing login bypass

**Objetivo:** Descobrir vulnerabilidade na função login.

**Vulnerabilidade encontrada:**
O campo `?username` e `password` estava concatenando direto no SQL. Ao injetar `'` deu erro 500.

**Meu processo:**
1. No campo username inseri o nome do administrador `Administrator` seguido da injeção `'--'.
2. No campo password inseri caracter aleatório porque será ignorado, e por fim consegui acesso.

**Payload final:**
```sql
'--
