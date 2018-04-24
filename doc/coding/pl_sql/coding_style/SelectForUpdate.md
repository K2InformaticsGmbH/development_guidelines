[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Specify columns to be updated in a `SELECT FOR UPDATE` statement](../../../../doc/coding/pl_sql/coding_style.md#SelectForUpdate)

Use the `SELECT FOR UPDATE` statement to request that locks be placed on all rows identified by the query. This is done when you know you will change some or all of those rows, and you don't want another session to change them out from under you. Specify the columns to be updated so that 

(a) anyone reading the code knows the intentions of your program, and 

(b) if your query contains a join of more than one table, Oracle will lock only the rows in those tables that contain any of the specified columns.
