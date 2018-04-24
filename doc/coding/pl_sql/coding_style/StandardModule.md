[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Standardize module structure using function and procedure templates](../../../../doc/coding/pl_sql/coding_style.md#StandardModule)

Once you adopt a set of guidelines for how developers should write procedures and functions, you need to help those developers follow their best practices. The bottom line is that guidelines will be followed if you make it easier to follow them than to ignore them.

For module standards, you can use either of the following approaches:

- Create a static template file that contains the generic logical structure for a procedure and/or function. Developers then copy that file to their own file, "de-genericize" the template by performing search and replace operations on placeholder strings with their own specific values (such as table names), and modify it from there.
- Use a program (one that you've written or a commercially available tool) that generates the code you want. This approach can be more flexible and can save you time, depending on how sophisticated a generator you use/create.

#### Example `FUNCTION` Template:

```PLSQL
CREATE OR REPLACE FUNCTION <name> (
    <parm>_in IN <datatype>
)
    RETURN <datatype>
/*
|| STANDARD COPYRIGHT STATEMENT HERE
|| Author:
|| File:
*/
IS
    retval <datatype> := <default value>;;
BEGIN
    -- Put your code here
    RETURN retval;
EXCEPTION
    WHEN OTHERS
    THEN
        err.handle;
END <name>;
```
