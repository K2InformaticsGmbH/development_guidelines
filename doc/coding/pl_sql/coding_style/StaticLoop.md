[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Move static expressions outside of loops and SQL statements](../../../../doc/coding/pl_sql/coding_style.md#StaticLoop)

A common mistake is to put code that is static or unchanging for each iteration of the loop inside the body. When you can identify such situations, extract the static code, assign the outcomes of that code to one or more variables, and then reference those variables inside the loop.

#### Instead of:

```PLSQL
CREATE OR REPLACE PROCEDURE summarize_reviews (
    summary_title_in IN VARCHAR2,
    isbn_in IN book.isbn%TYPE)
IS
    CURSOR review_cur IS
        SELECT text,
               TO_CHAR (SYSDATE, 'MM/DD/YYYY') today
          FROM book_review
         WHERE isbn = isbn_in;
BEGIN
    FOR review_rec IN review_cur
    LOOP
        IF LENGTH (review_rec.text) > 100
        THEN
            review_rec.text := SUBSTR (review_rec.text, 1, 100);
        END IF;
        review_pkg.summarize (UPPER (summary_title_in),
                              today,
                              UPPER (review_rec.text));
    END LOOP;
END;
/
```

#### it should be:

```PLSQL
CREATE OR REPLACE PROCEDURE summarize_reviews (
    summary_title_in IN VARCHAR2,
    isbn_in IN book.isbn%TYPE)
IS
    l_summary book_types.summary_t := UPPER (summary_title_in);
    l_today CONSTANT DATE := TRUNC (SYSDATE);
    CURSOR review_cur IS
        SELECT UPPER (SUBSTR (text, 1, 100)) text
          FROM book_review
         WHERE isbn = isbn_in;
    BEGIN
        FOR review_rec IN review_cur
        LOOP
            review_pkg.summarize (l_summary, l_today, review_rec.text);
    END LOOP;
END;
/
```
