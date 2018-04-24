[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Do not overload an exception with multiple errors unless the loss of information is intentional](../../../../doc/coding/pl_sql/coding_style.md#OverloadExceptions)

Don't declare one generic exception such as `bad_data` and then raise that exception under different circumstances. Users of your code will have trouble understanding precisely what caused the problem. Instead, declare a separate exception for each different kind of failure.
