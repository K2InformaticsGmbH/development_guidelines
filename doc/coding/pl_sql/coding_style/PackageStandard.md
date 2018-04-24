[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use a standard format for packages that include comment headers for each type of element defined in the package](../../../../doc/coding/pl_sql/coding_style.md#PackageStandard)

Packages are likely to be the largest, most complex code elements of your application. The internal structure of a package (both the specification and the body) is usually composed of many different types of elements, including variables, userdefined types, functions, and procedures.

Your standard package format should help you organize the elements of a package, minimize the need for forward declarations, and make it easier for you to rapidly find constructs. Make the standard format available for developers either in a template file or by generating it upon command.

#### Example:

```PLSQL
CREATE OR REPLACE PACKAGE BODY name
IS
/*
PUT YOUR PACKAGE HEADER HERE
*/

/* Constants */

/* Variables */

/* Exceptions */

/* Types (records, collections, cursor variables) */

/* Private Programs */

/* Public Programs */

END name;
```
