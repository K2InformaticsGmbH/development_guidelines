[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use incremental `COMMITs` to avoid rollback segment errors when changing large numbers of rows](../../../../doc/coding/pl_sql/coding_style.md#IncrementalCommit)

It's very easy to issue an `UPDATE` statement that can (theoretically) change one million rows or 10 million rows. It's more of a challenge to get that statement to succeed without running out of rollback segment space. And these errors are often hard to predict, because they depend on the volume of data for a specific run.

If you have this problem, you should switch to incremental commits: issue a `COMMIT` statement every 1,000 or 10,000 rows—whatever level works for your rollback segments.

#### Example:

You can declare a counter variable and update the variable with each execution of the loop body. If you process data from within a cursor `FOR` loop, you can also take advantage of the built-in `%ROWCOUNT` attribute, as shown here:

```PLSQL
DECLARE
    c_commit_plateau CONSTANT PLS_INTEGER := 10000;

    CURSOR my_cur
    IS
        SELECT *
        FROM my_table;
BEGIN
    FOR my_rec IN my_cur
    LOOP
        INSERT INTO temp_data VALUES (my_rec.id);
        IF (MOD (my_cur%rowcount, c_commit_plateau) = 0)
        THEN
            COMMIT WORK;
        END IF;
    END LOOP;
    COMMIT WORK;
END;
```

You can also build an API to the PL/SQL `COMMIT` statement that automatically handles incremental commits and adds value (logging, on-off toggles) to `COMMIT`.
