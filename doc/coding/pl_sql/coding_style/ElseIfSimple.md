[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `IF`...`ELSIF` only to test a single, simple condition](../../../../doc/coding/pl_sql/coding_style.md#ElseIfSimple)

You should write your IF statements in such a way as to keep them as straightforward and understandable as possible. For example, expressions are often more readable and understandable when they are stated in a positive form. Consequently, you are probably better off avoiding the `NOT` operator in conditional expressions.

A notable exception to this best practice is when you need to negate a large `AND` expression in order to find out efficiently
whether one value out of a group is different.
