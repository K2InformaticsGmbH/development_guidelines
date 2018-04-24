[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Handle exceptions that cannot be avoided but can be anticipated](../../../../doc/coding/pl_sql/coding_style.md#HandleAvoided)

If you are writing a program in which you can predict that a certain error will occur, you should include a handler in your code for that, allowing for a graceful and informative failure.

The form that this failure takes doesn't, by the way, necessarily need to be an exception. When writing functions, you may well decide that in the case of certain exceptions, you will want to return a value such as `NULL`, rather than allow an exception to propagate out of the function.
