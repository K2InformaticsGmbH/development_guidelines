[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Package application-named literal constants together](../../../../doc/coding/pl_sql/coding_style.md#PackAppConst)

Never place a hard-coded literal, such as "Y" or 150 in your code. Instead, create a package to hold these values and publish a name to be used in place of the literals. You will probably find it best to:
- Define constants that are referenced throughout your application in a single,
central package.
- Define constants that are more specific to a single area of functionality within
the package that encapsulates that functionality.
