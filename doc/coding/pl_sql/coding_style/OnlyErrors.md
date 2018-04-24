[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Only `RAISE` exceptions for errors, not to branch execution control](../../../../doc/coding/pl_sql/coding_style.md#OnlyErrors)

The `RAISE` statement is an easy and powerful way to abort normal processing in a program and immediately "go to" the appropriate `WHEN` handler. You should, however, never use `RAISE` in this way. You should raise an exception only when an error has occurred, not to control program flow.
