[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `WHEN OTHERS` only for unknown exceptions that need to be trapped](../../../../doc/coding/pl_sql/coding_style.md#WhenOthers)

Don't use `WHEN OTHERS` to grab any and every error. If you know that a certain exception might be raised, include a handler for that specifically.
