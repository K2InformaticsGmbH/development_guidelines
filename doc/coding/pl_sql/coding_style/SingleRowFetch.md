[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Put single-row fetches inside functions; never hard-code a query in your block](../../../../doc/coding/pl_sql/coding_style.md#SingleRowFetch)

Always put your single-row query inside a function, and then call the function to return the information you need (whether it's a scalar value, an entire record, or even a collection) through the `RETURN` clause.

#### Example:

Instead of writing code like this:

```PLSQL
BEGIN
    SELECT title INTO l_title -- HARD-CODED
      FROM book               -- QUERY...
     WHERE isbn =isbn_in;     -- BAD IDEA!
```

you should create a function, ideally within a "table encapsulation package":

```PLSQL
PACKAGE te_book
IS
    FUNCTION title (isbn_in IN book.isbn%TYPE)
        RETURN book.title%TYPE;
```

Now your application code looks like this:

```PLSQL
BEGIN
    l_title := te_book.title (isbn_in);
```
