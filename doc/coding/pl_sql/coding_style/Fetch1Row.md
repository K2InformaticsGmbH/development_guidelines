[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Never use a cursor `FOR` loop to fetch just one row](../../../../doc/coding/pl_sql/coding_style.md#Fetch1Row)

If you have a single-row query, you can use a cursor `FOR` loop, but it's misleading. A cursor `FOR` loop is designed to fetch all (multiple) rows from a cursor.
