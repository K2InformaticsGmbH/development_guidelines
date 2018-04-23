[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Do not overload data structure usage](../../../../doc/coding/pl_sql/coding_style.md#OverloadDS)

When you declare a variable, you should give it a name that accurately reflects its purpose in a program. If you then use that variable in more than one way ("recycling"), you create confusion and, very possibly, introduce bugs.

The solution is to declare and manipulate separate data structures for each distinct requirement.
