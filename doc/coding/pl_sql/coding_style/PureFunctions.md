[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Keep functions pure by avoiding [`IN`] `OUT` parameters](../../../../doc/coding/pl_sql/coding_style.md#PureFunctions)

The whole point of a function is to return a value (whether it's a single, scalar value or a composite, such as a record or a collection). If you also return data back through the parameter list with `OUT` or `IN OUT` arguments, the purpose and usage of the function is obscured. Oracle also places restrictions on how you can use functions that have `OUT` and `IN OUT` parameters - namely, you can't call that function from within a SQL statement.

If you need to return multiple pieces of information, take one of the following approaches:

- **Return a record or collection of values**: Make sure to publish the structure of your record or collection (the `TYPE` statement) in a package specification so that developers can understand and use the function more easily. Note that you can't call this function in a SQL statement if it returns a record or index-by table.

- **Break up the single function into multiple functions, all returning scalar values**: With this approach, you can call the functions from within SQL statements.

- **Change your function into a procedure**: Unless you need to call a function to return this information, just change it to a procedure returning multiple pieces of information.
