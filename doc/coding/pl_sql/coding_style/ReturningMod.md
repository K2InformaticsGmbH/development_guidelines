[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `RETURNING` to retrieve information about modified rows](../../../../doc/coding/pl_sql/coding_style.md#ReturningMod)

The `RETURNING` clause, available in Oracle8 and above, allows you to retrieve information from rows you have just modified with an `INSERT`, `UPDATE`, or `DELETE` statement. This clause allows you to perform - in a single operation - what you would
previously have done in two operations (`INSERT`, then `SELECT`, for example).

#### Example:

Instead of writing code like this:

```PLSQL
INSERT INTO patient (patient_id, last_name, first_name)
    VALUES (patient_seq.NEXTVAL, 'FEUERSTEIN', 'STEVEN')
    RETURNING patient_id INTO l_patient_id;
```

You can also use the `RETURNING` clause in dynamic SQL and `FORALL` statements to obtain information about multiple rows affected by DML statements.
