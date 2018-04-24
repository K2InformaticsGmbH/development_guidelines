[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use a cursor `FOR` loop to fetch all rows in a cursor unconditionally](../../../../doc/coding/pl_sql/coding_style.md#CursorForLoop)

The cursor `FOR` loop construct is a wonderful addition to the PL/SQL language, reflecting the tight integration between SQL and PL/SQL. Use it whenever you need to fetch every single row identified by the cursor, but don't use it if you have to conditionally exit from the loop.

#### Example:

```PLSQL
DECLARE
    CURSOR sef_books_cur IS
        SELECT title, total_count
          FROM book_sales
         WHERE author = 'FEUERSTEIN, STEVEN';
BEGIN
    FOR rec IN sef_books_cur
    LOOP
        pl (rec.title || ': ' || rec.total_count || ' copies');
    END LOOP;
END;
```
