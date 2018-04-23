[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Never `EXIT` or `RETURN` from `WHILE` and `FOR` loops](../../../../doc/coding/pl_sql/coding_style.md#NeverExit)

The `WHILE` and `FOR` loops include "boundary conditions" that determine:

- When and if a loop should execute at all
- When a loop should stop executing

If you use the `EXIT` or `RETURN` statements inside a `WHILE` or `FOR` loop, you cause an unstructured termination from the loop. The resulting code is hard to trace and debug.
