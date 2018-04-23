[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `ELSIF` with mutually exclusive clauses](../../../../doc/coding/pl_sql/coding_style.md#ElseIfMutually)

When you need to write conditional logic that has several mutually exclusive clauses (in other words, if one clause is `TRUE`, no other clause evaluates to `TRUE`), use the `ELSIF` construct:

```PLSQL
IF condA THEN
    ...
ELSIF condB THEN
    ...
ELSIF condN THEN
    ...
ELSE
    ...
END IF;
```
