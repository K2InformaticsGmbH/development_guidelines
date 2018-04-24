[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Parameterize explicit cursors](../../../../doc/coding/pl_sql/coding_style.md#ParamExplCursors)

Cursors return information, just as functions do, and they can accept parameters just as functions do (but only `IN` parameters). By defining your explicit cursors to accept parameterized values, these cursors are more easily reused in different circumstances and programs. This added value becomes most apparent when you define cursors in package specifications.

#### Example:

Instead of this

```PLSQL
DECLARE
    CURSOR r_and_d_cur IS
        SELECT last_name FROM employee
         WHERE department_id = 10;
BEGIN
    OPEN r_and_d_cur;
```

move your cursor to a package:

```PLSQL
CREATE OR REPLACE PACKAGE dept_info_pkg
IS
    CURSOR name_cur (dept IN INTEGER) IS
        SELECT last_name FROM employee
         WHERE department_id = dept;
```

and then open it like this:

```PLSQL
DECLARE
    r_and_d_dept CONSTANT PLS_INTEGER := 10;
BEGIN
    open dept_info_pkg.name_cur (r_and_d_dept);
