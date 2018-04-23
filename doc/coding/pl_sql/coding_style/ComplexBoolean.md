[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Replace complex expressions with Boolean variables and functions](../../../../doc/coding/pl_sql/coding_style.md#ComplexBoolean)

A Boolean expression evaluates to one of three values: `TRUE`, `FALSE`, or `NULL`. You can use Boolean variables and functions to hide complex expressions; the result is code that is virtually as readable as "straight" English—or whatever language you
use to communicate with other human beings.

#### Instead of

```PLSQL
IF total_sal BETWEEN 10000 AND 50000 AND
    emp_status (emp_rec.empno) = 'N' AND
    (MONTHS_BETWEEN
        (emp_rec.hiredate, SYSDATE) > 10)
THEN
    give_raise (emp_rec.empno);
END IF;
```

#### it should be

```PLSQL
DECLARE
    eligible_for_raise BOOLEAN :=
        total_sal BETWEEN 10000 AND 50000 AND
        emp_status (emp_rec.empno) = 'N' AND
        (MONTHS_BETWEEN
            (emp_rec.hiredate, SYSDATE) > 10);
BEGIN
    IF eligible_for_raise
    THEN
        give_raise (emp_rec.empno);
    END IF
```
