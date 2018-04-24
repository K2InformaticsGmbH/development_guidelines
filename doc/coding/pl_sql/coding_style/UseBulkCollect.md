[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `BULK COLLECT` to improve performance of multi-row queries](../../../../doc/coding/pl_sql/coding_style.md#UseBulkCollect)

Recognizing that you often need to return large numbers of rows from the database, Oracle offers the `BULK COLLECT` clause for queries. When you use `BULK COLLECT`, you retrieve multiple rows of data in a single request to the RDBMS. The
data is then deposited into a series of collections.

#### Example:

To use `BULK COLLECT`, you need to declare collections to hold all the retrieved data. Then, preface your `INTO` clause with the `BULK COLLECT` keywords, and you are done:

```PLSQL
CREATE OR REPLACE PROCEDURE process_employees
    (deptno_in IN dept.deptno%TYPE)
RETURN emplist_t
IS
    TYPE numTab IS TABLE OF emp.empno%TYPE;
    TYPE charTab IS TABLE OF emp.ename%TYPE;
    TYPE dateTab IS TABLE OF emp.hiredate%TYPE;
    enos numTab;
    names charTab;
    hdates dateTab;
BEGIN
    SELECT empno, ename, hiredate
      BULK COLLECT INTO enos, names, hdates
      FROM emp
     WHERE deptno = deptno_in;
    
    ...
END process_employees;
```

Or, if you are using an explicit cursor:

```PLSQL
BEGIN
    OPEN emp_cur INTO emp_rec;
    FETCH emp_cur BULK COLLECT INTO enos, names, hdates;
```
