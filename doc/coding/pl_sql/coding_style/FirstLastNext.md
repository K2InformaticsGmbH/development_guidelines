[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Scan collections using `FIRST`, `LAST`, and `NEXT` in loops](../../../../doc/coding/pl_sql/coding_style.md#FirrstLastNext)

A collection in PL/SQL is like a single-dimensional array. A collection differs from an array, however, in that two of the three types of collections (nested tables and index-by tables) can be sparse, which means that the defined rows in the collection need not be sequentially defined. You can, in other words, assign a value to row 10 and a value to row 10,000, and no rows will exist between those two.

If you scan a collection with a `FOR` loop and the collection is sparse, the `FOR` loop tries to access an undefined row and raise a `NO_DATA_FOUND` exception. Instead, use the `FIRST` and `NEXT` methods to scan forward through a collection, and use `LAST` and `PRIOR` to scan backwards
