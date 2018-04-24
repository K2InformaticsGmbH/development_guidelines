[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `COUNT` only when the actual number of occurrences is needed](../../../../doc/coding/pl_sql/coding_style.md#CountOnly)

Don't use the `COUNT` function to answer either of the following questions:

- Is there at least one row matching certain criteria?
- Is there more than one row matching certain criteria?

Instead, use an explicit cursor inside a function. 

You should use `COUNT` only when you need to answer the question: "How many rows match a certain criteria?"

#### Example:

Suppose I have been asked to write a program that returns `TRUE` if there is at least
one book in a given category. 

##### Instead of:

I could write it like this:

```PLSQL
CREATE OR REPLACE FUNCTION atleastone (
    category_in IN book.category%TYPE)
    RETURN BOOLEAN
IS
    numbooks INTEGER;
BEGIN
    SELECT COUNT(*) INTO numbooks
      FROM book
     WHERE category = category_in;
    
    RETURN (numbooks > 0);
END;
```

##### it should be:

```PLSQL
CREATE OR REPLACE FUNCTION at_least_one (
    category_in IN book.category%TYPE)
    RETURN BOOLEAN
IS
    retval BOOLEAN;

    CURSOR category_cur
        SELECT 1
          FROM book
         WHERE category = category_in;
BEGIN
    OPEN category_cur;
    FETCH category_cur INTO category_rec;
    retval := category_cur%FOUND;
    CLOSE category_cur;

    RETURN retval;
END;
```

