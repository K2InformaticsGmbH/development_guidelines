[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Define multi-row cursors in packages so they can be used from multiple programs](../../../../doc/coding/pl_sql/coding_style.md#MultiRowFetch)

Create a package to hold all the multiple-row queries for a given business entity (which may be made up of one or more tables and views). You can then open, fetch, and close those cursors from multiple programs.

#### Example:

```PLSQL
PACKAGE book_pkg
IS
    CURSOR allbooks IS
        SELECT * FROM book;

    CURSOR books_by_category (
        category_in IN book.category%TYPE)
    IS
        SELECT * FROM book
        WHERE category = category_in;
```

and here is a use of a packaged cursor:

```PLSQL
BEGIN
    OPEN book_pkg.books_by_category (
        'THRILLER');
    LOOP
        FETCH book_pkg.books_by_category
         INTO thrillers_rec;
        ...
    END LOOP;
    CLOSE book_pkg.books_by_category;
END;
```
