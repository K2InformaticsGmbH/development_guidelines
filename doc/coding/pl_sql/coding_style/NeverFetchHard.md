[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Fetch into cursor records, never into a hard-coded list of variables](../../../../doc/coding/pl_sql/coding_style.md#NeverFetchHard)

Whenever you fetch data from a cursor, whether it's an explicit cursor or a cursor variable, you should fetch into a record defined from that cursor with `%ROWTYPE`.

#### Example:

```PLSQL
DECLARE
    scifi_rec book_pkg.books_by_category%ROWTYPE;
BEGIN
    OPEN book_pkg.books_by_category ('SCIFI');
    FETCH book_pkg.books_by_category INTO
        scifi_rec;
```
