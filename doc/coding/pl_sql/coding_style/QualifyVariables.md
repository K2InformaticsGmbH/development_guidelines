[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Qualify PL/SQL variables with their scope names when referenced inside SQL statements](../../../../doc/coding/pl_sql/coding_style.md#QualifyVariables)

You could declare a variable that has the same name as a table, a column, or a view. The PL/SQL compiler won't get confused, but you might, and your SQL statements inside PL/SQL might not work as intended. So you should always make sure that there is no ambiguity between SQL and PL/SQL identifiers. The best way to do this is to qualify all references to PL/SQL variables with their scope name.

#### Example:

Consider the following block:

```PLSQL
CREATE OR REPLACE PROCEDURE show_fav_flavor (
    pref_type IN VARCHAR2)
IS
    pref VARCHAR2(100);
BEGIN
    SELECT preference 
      INTO pref
      FROM personal_preferences PP
     WHERE PP.pref_type = pref_type;
    pl (pref);
END;
```

You might think that the WHERE clause restricts the query to only those rows where pref_type equals the value passed in through the parameter. In fact, it's no different logically than "1 = 1". SQL always takes precedence over PL/SQL when resolving identifiers.

#### Solution:

Always qualify references to PL/SQL elements inside the SQL statement, as in:

```PLSQL
· SELECT preference 
    INTO pref
·   FROM personal_preferences PP
   WHERE PP.pref_type = show_fav_flavor.pref_type;
```
