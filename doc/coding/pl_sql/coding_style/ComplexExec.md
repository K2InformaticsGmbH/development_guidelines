[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Perform complex variable initialization in the executable section](../../../../doc/coding/pl_sql/coding_style.md#ComplexExec)

The exception section of a block can trap only errors raised in the executable section of that block. So if the code you run to assign a default value to a variable fails in the declaration section, that error is propagated unhandled out to the enclosing program. It's difficult to debug these problems, so, you must either:

- Be sure that initialization logic doesn't raise an error.
- Perform your initialization at the beginning of the executable section, preferably in a separate "init" program.
