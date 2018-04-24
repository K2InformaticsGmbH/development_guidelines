[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use named notation to clarify, self-document, and simplify module calls](../../../../doc/coding/pl_sql/coding_style.md#NamedNotation)

PL/SQL allows you to specify the name of a parameter along with its value in a parameter list by using this format:

```PLSQL
parameter name => value
```

This is called named notation. With named notation, you can change the order in which you supply arguments; you can also skip over `IN` arguments with default values.

Use named notation whenever you make a call to a program that has any of the following characteristics:

- It has a long, confusing parameter list.
- It's used infrequently, meaning that there is little familiarity with it or its parameter list.
- It has default values for multiple `IN` parameters.
- In some cases, it actually requires named notation due to the parameter list design of overloaded programs (as is necessary with the built-in package, `DBMS_OBFUSCATION_TOOLKIT`).
