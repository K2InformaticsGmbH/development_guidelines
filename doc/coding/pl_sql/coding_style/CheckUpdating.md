[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Check `SQL%ROWCOUNT` when updating or removing data that "should" be there](../../../../doc/coding/pl_sql/coding_style.md#CheckUpdating)

The `SQL%ROWCOUNT` cursor attribute returns the numbers of rows affected by the most recent `INSERT`, `UPDATE`, or `DELETE` statement executed in your session. Check this value to verify that the action completed properly. (Note that updates and deletes don't raise an exception if no rows are affected.)
