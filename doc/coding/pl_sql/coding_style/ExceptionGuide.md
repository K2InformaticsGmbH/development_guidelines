[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Set guidelines for application-wide error handling before you start coding](../../../../doc/coding/pl_sql/coding_style.md#ExceptionGuide)

It's impractical to define `EXCEPTION` sections in your code after the fact—in other words, after the programs have been written. The best way to implement application-wide, consistent error handling is to use a standardized package that contains at least the following elements:

- Procedures that perform most exception-handling tasks, such as writing to an error log.
- A raise program that hides the complexity of `RAISE_APPLICATION_ERROR` and application-specific error numbers.
- A function that returns error message text for a given error number.
