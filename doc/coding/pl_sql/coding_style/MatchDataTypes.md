[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Match datatypes to computational usage](../../../../doc/coding/pl_sql/coding_style.md#MatchDataTypes)

- Use `NUMBER` only with a specified precision.
- Don't use `CHAR` and `VARCHAR`.
- Don't use `VARCHAR2` with a hard-coded maximum length - use `%TYPE` and `SUBTYPE` instead.
- Use `PLS_INTEGER` for integer values in the range of -2147483647 ... 2147483647.
