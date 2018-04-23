[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Anchor variables to database datatypes using `%TYPE` and `%ROWTYPE`](../../../../doc/coding/pl_sql/coding_style.md#AnchorTypes)

When you declare a variable using `%TYPE` or `%ROWTYPE`, you "anchor" the type of that data to another, previously defined element. If your program variable has the same datatype as a column in a table or view, use `%TYPE` to define it from that column. If your record has the same structure as a row in a table or view, use `%ROWTYPE` to define it from that table.
