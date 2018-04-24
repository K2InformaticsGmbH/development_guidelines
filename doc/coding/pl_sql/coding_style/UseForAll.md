[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `FORALL` to improve performance of collection-based DML](../../../../doc/coding/pl_sql/coding_style.md#UseForAll)

Recognizing that you often need to modify (insert, delete, or update) large numbers of rows in the database from within PL/SQL, Oracle offers the `FORALL` statement. This statement can dramatically improve your DML performance by reducing the number of "context switches" between the PL/SQL statement executor and the SQL engine.

Consider using `FORALL` whenever you perform a DML operation within a loop.

#### Example:

The following cursor `FOR` loop performs many individual row updates:

```PLSQL
BEGIN
    FOR book_rec IN book_pkg.book_cur
    LOOP
        UPDATE borrowings
            SET borrow_date = SYSDATE
                borrower_id = book_rec.user_id
        WHERE isbn = book_rec.isbn;
    END LOOP;
END;
```

Now I use `FORALL` to accomplish the same thing, but with a single pass to the SQL engine and RDBMS:

```PLSQL
DECLARE
    TYPE books_t IS TABLE OF borrower.user_id%TYPE;
    books books_t := books_t( );
    TYPE isbns_t IS TABLE OF book.isbn%TYPE;
    isbns isbns _t := isbns_t( );
BEGIN
    FOR book_rec IN book_pkg.book_cur
    LOOP
        books.EXTEND;
        isbns.EXTEND;
        books(books.LAST) := book_rec.user_id;
        isbns(isbns.LAST) := book_rec.isbn;
    END LOOP;

    FORALL indx IN books.FIRST .. books.LAST
        UPDATE borrowings
            SET borrow_date = SYSDATE
                borrower_id = books(indx)
          WHERE isbn = isbns(indx);
END;
```

Notice that I still need the cursor `FOR` loop to populate my collections. The time it takes to do this, however, is usually more than offset by the improvements in `UPDATE` processing.
