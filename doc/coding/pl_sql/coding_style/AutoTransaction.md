[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use autonomous transactions to isolate the effect of `COMMITs` and `ROLLBACKs`](../../../../doc/coding/pl_sql/coding_style.md#AutoTransaction)

Autonomous transaction allows you to make and save (or roll back) changes within a single PL/SQL block—without affecting the outer
or main transaction.

To make a PL/SQL block an autonomous transaction, simply include this statement in the declaration section of the block:

```PLSQL
PRAGMA AUTONOMOUS_TRANSACTION;
```

You can use this statement in any procedure and function and in any non-nested anonymous block.

#### Example:

```PLSQL
CREATE OR REPLACE PROCEDURE log_error (
    code IN INTEGER, msg IN VARCHAR2)
AS
    PRAGMA AUTONOMOUS_TRANSACTION;
BEGIN
    INSERT INTO error_log
        (errcode, errtext, created_on, created_by)
    VALUES
        (code, msg, SYSDATE, USER);
    
    COMMIT;
EXCEPTION
    WHEN OTHERS THEN ROLLBACK;
END;
```
