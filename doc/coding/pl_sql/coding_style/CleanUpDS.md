[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Clean up data structures when your program terminates (successfully or with an error)](../../../../doc/coding/pl_sql/coding_style.md#CleanUpDS)

PL/SQL does an awful lot of cleanup for you, but there are many scenarios in which it's absolutely crucial for you to take your own cleanup actions.

The best way to do this is to standardize on a local cleanup procedure that is to be included in each program. Call this program both at the end of the executable section and in each exception handler `WHEN` clause.

#### Instead of:

```PLSQL
CREATE OR REPLACE PROCEDURE busy_busy
IS
    fileid UTL_FILE.file_type;
    dyncur PLS_INTEGER;
BEGIN
    dyncur := DBMS_SQL.open_cursor;
    OPEN book_pkg.all_books_by ('FEUERSTEIN');
    fileid := UTL_FILE.fopen (
        '/apps/library', 'bestsellers.txt', 'R');
.    ..
EXCEPTION
    WHEN NO_DATA_FOUND
    THEN
        err.log;
        RAISE;
END;
```

#### it should be:

```PLSQL
CREATE OR REPLACE PROCEDURE busy_busy
IS
    fileid UTL_FILE.file_type;
    dyncur PLS_INTEGER;
     
    PROCEDURE cleanup IS
    BEGIN
        IF book_pkg.all_books_by%ISOPEN
        THEN
            CLOSE book_pkg.all_books_by;
        END IF;

    DBMS_SQL.CLOSE_CURSOR (dyncur);

    UTL_FILE.FCLOSE (fileid);
END;

BEGIN
    dyncur := DBMS_SQL.open_cursor;
    OPEN book_pkg.all_books_by ('FEUERSTEIN');
    fileid := UTL_FILE.fopen (
        '/apps/library', 'bestsellers.txt', 'R');
    ...
    cleanup;
EXCEPTION
    WHEN NO_DATA_FOUND
    THEN
        err.log;
        cleanup;
        RAISE;
END;
```
