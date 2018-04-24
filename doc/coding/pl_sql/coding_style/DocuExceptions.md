[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Document all package exceptions by module in package specifications](../../../../doc/coding/pl_sql/coding_style.md#DocuExceptions)

Different programs may well raise different exceptions. You need to communicate this information clearly to users of your code so they know what to expect and what to code for. PL/SQL doesn't offer a structured way to do this as part of the language (Java, for example, does precisely that). So you need to come up with a standard convention for including such documentation in your code.

#### Example:

The following package specification offers one simple example of how you might document the exceptions individual programs might raise:

```PLSQL
CREATE OR REPLACE PACKAGE overdue
IS
    PROCEDURE analyze_status (...);
        /* analyze_status can raise:
        overdue.excessive_lateness
        overdue.fetch_out_of_sequence
        */
    FUNCTION count_by_borrower (...)
        RETURN INTEGER;
        /* count_by_borrower can raise:
        NO_DATA_FOUND
        borrower.does_not_exist
        */
```
