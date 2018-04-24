[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Hide reliance on the dual table](../../../../doc/coding/pl_sql/coding_style.md#HideDual)

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

This is a special case of [SQL-04: Put single-row fetches inside functions; never
hard-code a query in your block.] but is worth mentioning. The dual table is a
"dummy" table that is used by Oracle itself and by many developers to access
functionality in the SQL engine that is otherwise not available in PL/SQL.
Use of the dual table is, therefore (and by definition) a workaround or "kludge." We
all know we have to do these things, but we also know or hope that over time, we
will no longer have to do them. So hide your kludges behind a function or procedure
and then, when they are no longer needed, you can change the implementation
without affecting those usages.

#### Example:

Instead of:

```PLSQL
DECLARE
    my_id INTEGER;
BEGIN
    SELECT patient_seq.NEXTVAL INTO my_id
      FROM dual;
```

you should build yourself a function:

```PLSQL
CREATE OR REPLACE FUNCTION next_patient_id
    RETURN patient.patient_id%TYPE
IS
    retval patient.patient_id%TYPE;
BEGIN
    SELECT patient_seq.nextval
      INTO retval
      FROM dual;
    RETURN retval;
END;
```

And then you only need to write this to get your next primary key value:

```PLSQL
DECLARE
    my_id INTEGER;
BEGIN
    my_id := next_patient_id();
