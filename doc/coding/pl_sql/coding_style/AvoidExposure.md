[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Avoid hard-coded exposure of error handling by using standard, declarative procedures](../../../../doc/coding/pl_sql/coding_style.md#AvoidExposure)

The best way to achieve consistent, high-quality error handling throughout your application is to offer a set of predefined procedures that do the basic plumbing of error handling: record the error information if desired, propagate the exception, and so on.

It's crucial then to make certain that development team members always and only use these procedures in their `WHEN` clauses.

#### Example:

```PLSQL
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        err.handle (
            'No company for id ' || TO_CHAR (v_id),
            log => TRUE,
            reraise => FALSE);
    WHEN OTHERS THEN
        err.handle (log => TRUE, reraise => TRUE);
```
