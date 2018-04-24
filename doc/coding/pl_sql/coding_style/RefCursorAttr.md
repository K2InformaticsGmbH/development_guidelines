[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Reference cursor attributes immediately after executing the SQL operation](../../../../doc/coding/pl_sql/coding_style.md#RefCursorAttr)

`INSERT`, `UPDATE`, and `DELETE` statements are all executed as "implicit cursors" in PL/SQL. You don't, in other words, explicitly declare, open, and process these kinds of statements. You simply issue the `INSERT`, `UPDATE`, or `DELETE` statement, and the underlying Oracle SQL engine takes care of the cursor management.

You can obtain information about the results of the implicit operation most recently executed in your session by checking any of the following cursor attributes:

Attribute | Returns
:-------- | :------
`SQL%ROWCOUNT` | Number of rows affected by the DML statement
`SQL%ISOPEN`   | Always `FALSE`, since the cursor is opened and then closed implicitly
`SQL%FOUND `   | Returns `TRUE` if the statement affects at least one row
`SQL%NOTFOUND` | Returns `FALSE` if the statement affects not at least one row

There is only one set of SQL% attributes in a session; they always reflect the last implicit operation performed. You should, therefore, keep to an absolute minimum the code that falls between the DML operation and the attribute reference. Otherwise, the value returned by the attribute might not correspond to the desired SQL statement, resulting in hard-to-resolve bugs.
