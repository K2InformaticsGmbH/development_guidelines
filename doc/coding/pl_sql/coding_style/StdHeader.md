[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Standardize module and program headers](../../../../doc/coding/pl_sql/coding_style.md#StdHeader)

While you should generally keep comments to a minimum in your code, it's extremely important to create and keep current a standard header for all programs. This header should contain, at a minimum, the following elements:

- **Version, author, and copyright information**: What is the version of the code? Who wrote the program, who owns the program, etc.
- **Access information**: Where is the program stored? On disk in a file? Within the database under a certain schema?
- **Overview**: What does this program do?
- **Dependencies**: What does this program need to have defined, or have access to, in order to run properly?
- **Algorithms**: Are any algorithms of special note used in the program? If so, specify them and/or supply a more detailed description of the theory of operation (if there is one).
- **Scope**: What application module(s) was the program written for (if it's not a generic library-type of program)? Frequently, packages are backend components of a system with a complex frontend. For example, a set of packages might comprise the Payroll subsystem.
- **Modification history**: What modifications have been made to the program? Include a line entry for each change to the program, showing who, when, and what. Put the entries in date-descending order, so that the most recent change is at the top.
- **Exceptions**: What errors might be raised by the program?

Define this header after the `IS` or `AS` keyword in your program definition. For example:

```PLSQL
CREATE OR REPLACE PROCEDURE my_procedure
IS
/*
... header text
*/
```

#### Template header:

```PLSQL
/*
<VERSION>1.0.5</VERSION>
<FILENAME>stdhdr.pkg</FILENAME>
<AUTHOR>Stefan Ochsenbein</AUTHOR>
<SUMMARY>API to standard headers in code</SUMMARY>
<COPYRIGHT>K2 Informatics GmbH, 2000-2018</COPYRIGHT>

<OVERVIEW>
Rather than simply document a standard header
for programs, this package offers a package-based
API so that you can easily extract information
stored in the header.
</OVERVIEW>

<DEPENDENCIES>
ALL_SOURCE data dictionary view
</DEPENDENCIES>

<EXCEPTIONS>None</EXCEPTIONS>

Modification History
Date       By        Modification
---------- --------- -------------------------------
<MODIFICATIONS>
06/30/2017 SOC       Change to XML-compatible syntax
06/07/2016 SOC       Program created
</MODIFICATIONS>
*/
```
