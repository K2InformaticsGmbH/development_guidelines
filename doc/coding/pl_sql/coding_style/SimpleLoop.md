[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use a simple loop to avoid redundant code required by a `WHILE` loop](../../../../doc/coding/pl_sql/coding_style.md#SimpleLoop)

Generally, you should use a simple loop if you always want the body of the loop to
execute at least once. You use a WHILE loop if you want to check before executing
the body the first time. Since the WHILE loop performs its check "up front," the
variables in the boundary expression must be initialized. The code to initialize is
often the same code needed to move to the next iteration in the WHILE loop. This
redundancy creates a challenge in both debugging and maintaining the code: how do
you remember to look at and update both?

If you find yourself writing and running the same code before the WHILE loop and at
end of the WHILE loop body, consider switching to a simple loop.

#### Instead of:

```PLSQL
DECLARE
    l_fine PLS_INTEGER := 0;
    l_date DATE := SYSDATE;
    l_overdue_count NUMBER;
BEGIN
    l_overdue_count :=
        overdue_pkg.countem (borrower_id => borrower_in, l_date);
    WHILE (l_overdue_count > 0 AND l_fine < 10)
    LOOP
        update_fine_info (l_date, l_one_day_fine);
        l_fine := l_fine + l_one_day_fine;
        l_date := l_date + 1;
        l_overdue_count :=
            overdue_pkg.countem (borrower_id => borrower_in, l_date);
    END LOOP;
```

#### it should be:

```PLSQL
DECLARE
    l_fine PLS_INTEGER := 0;
    l_date DATE := SYSDATE;
    l_overdue_count NUMBER;
BEGIN
LOOP
    EXIT WHEN 
        (l_overdue_count <= 0 OR l_fine >= 10)
    update_fine_info (l_date, l_one_day_fine);
    l_fine := l_fine + l_one_day_fine;
    l_date := l_date + 1;
    l_overdue_count :=
        overdue_pkg.countem (borrower_id => borrower_in, l_date);
END LOOP;
```
