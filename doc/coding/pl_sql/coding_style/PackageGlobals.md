[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Clean up data structures when your program terminates (successfully or with an error)](../../../../doc/coding/pl_sql/coding_style.md#PackageGlobals)

A global variable is a data structure that can be referenced outside the scope or block in which it's declared. In the following block, for example, the `l_publish_date` is global to the local `display_book_info` procedure:

```PLSQL
DECLARE
    l_publish_date DATE;
    ...
    PROCEDURE display_book_info IS
    BEGIN
        DBMS_OUTPUT.PUT_LINE (l_publish_date);
    END;
```

Globals are dangerous and should be avoided, because they create hidden "dependencies" or side-effects. A global doesn't have to be passed through the parameter list, so it's hard for you to even know that a global is referenced in a program without looking at the implementation.

Globals are most often defined in packages. If you declare a variable at the package level (not within any specific program), that variable exists and retains its value for the duration of your session.

The general solution to this problem is to pass the global as a parameter in your procedure and function; don't reference it directly within the program. Another general technique to keep in mind is to declare variables, cursors, functions, and other objects as "deeply" as possible (i.e., in the block nearest to where, or within which, that object will be used), in order to reduce the chance of unintended use by other sections of the code.

#### Instead of:

```PLSQL
CREATE OR REPLACE FUNCTION overdue_fine (
    isbn_in IN book.isbn%TYPE)
    RETURN NUMBER
IS
    l_days_overdue NUMBER;
BEGIN
    l_days_overdue := overdue_pkg.days_overdue (isbn_in, SYSDATE);
    RETURN (l_days_overdue * overdue_pkg.g_daily_fine);
END;
```

#### it should be:

```PLSQL
CREATE OR REPLACE FUNCTION overdue_fine (
    isbn_in IN book.isbn%TYPE,
    daily_fine_in IN NUMBER)
    RETURN NUMBER
IS
    l_days_overdue NUMBER;
BEGIN
    l_days_overdue := overdue_pkg.days_overdue (isbn_in, SYSDATE);
    RETURN (l_days_overdue * daily_fine_in);
END;
```
