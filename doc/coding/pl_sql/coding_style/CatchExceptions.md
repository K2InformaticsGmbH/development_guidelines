[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Catch all exceptions and convert to meaningful return codes before returning to non-PL/SQL host programs](../../../../doc/coding/pl_sql/coding_style.md#CatchExceptions)

Suppose that you are calling PL/SQL programs from Visual Basic, Powerbuilder, Java, or some other language. These non-Oracle development languages may not understand, or be able to handle, PL/SQL exceptions very gracefully. In this situation, you may need to pass back error status (code and message) with at least some of your programs.

You should do this only on an "exception" basis - as needed. The best way to do it is to overload the original program in your package with another of the same name and two additional parameters.

#### Example:

Suppose you need to call overdue.analyze_status both from within the Oracle RDBMS (i.e., from another stored procedure) and from within a Visual Basic application. You can use package overloading to offer the "same" program with a different interface:

```PLSQL
CREATE OR REPLACE PACKAGE overdue
IS
    PROCEDURE analyze_status (
        title_in IN book.title%TYPE,
        start_date_in IN DATE := SYSDATE);

    overdue.analyze_status (
        title_in IN book.title%TYPE,
        start_date_in IN DATE := SYSDATE,
        error_code OUT INTEGER,
        error_msg OUT VARCHAR2);
```
