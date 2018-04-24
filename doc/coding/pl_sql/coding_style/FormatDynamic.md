[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Format dynamic SQL strings so they can be easily read and maintained](../../../../doc/coding/pl_sql/coding_style.md#FormatDynamic)

When building long and possibly complex dynamic SQL statements, you should apply the same formatting rules as are applied to static code.

These strings are often the result of multiple concatenations, so they start off being less readable than static code. Don't compound the problem by treating this dynamic SQL as simply a set of concatenated strings. Consider it, instead, as a "program" in and of itself and format it - as much as possible - in the same way.

Many experienced dynamic SQL developers build a "typical" query or block (expressing the pattern of code they want to run dynamically), and then turn it into a string, with all the linebreaks and indentation intact.

#### Example:

Here's an example of well-formatted PL/SQL code: my very long string is broken into individual pieces so that it can be indented nicely. This formatting also, unfortunately, pleads ignorant to recognizing the significance of that string's contents:

```PLSQL
DECLARE
    v_sql VARCHAR2 (32767);
BEGIN
    v_sql :=
        'DECLARE CURSOR curs_get_orders IS ' ||
        ' SELECT * FROM ord_order; BEGIN ' ||
        ' FOR v_order_rec IN curs_get_orders LOOP ' ||
        ' process_order(v_order_rec.order_id); ' ||
        ' END LOOP; END;';
    EXECUTE IMMEDIATE v_sql;
END;
/
```

Here are two alternative formattings of the same assignment. 

In the first, I continue to use concatenation, but I break up the string and use indentation to present the block of code according to my usual conventions. 

```PLSQL
v_sql :=
   'DECLARE '
||    'CURSOR curs_get_orders IS '
||       'SELECT * FROM ord_order; '
|| 'BEGIN '
||    'FOR v_order_rec IN curs_get_orders LOOP '
||       'process_order(v_order_rec.order_id); '
||    'END LOOP; '
|| 'END;';
```

In the second example, I write my block as a single string with embedded carriage returns displayed, to make sure it compiles correctly:

```PLSQL
v_sql :=
   'DECLARE
       CURSOR curs_get_orders IS
          SELECT *
          FROM ord_order;
    BEGIN
       FOR v_order_rec IN curs_get_orders LOOP
          process_order(v_order_rec.order_id);
       END LOOP;
    END';
```
