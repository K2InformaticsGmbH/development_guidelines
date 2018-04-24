[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `NOCOPY` to minimize overhead when collections and records are [`IN`] `OUT` parameters](../../../../doc/coding/pl_sql/coding_style.md#NocopyParameter)

When you pass arguments through the parameter list of a program, those arguments can be passed by reference or by value:

- By reference means that the data structure manipulated inside the program points to the same location in memory that holds the value of the argument.
- By value means that the value of the argument is copied into the data structure of the program, and then copied back out to the argument data structure if no exception occurs.

Parameter passing in PL/SQL by default follows these rules:

- `IN` arguments are passed by reference.
- `OUT` and `IN OUT` arguments are passed by value.

This means that when you pass a large data structure (such as a collection, a record, or an instance of an object type) as an `OUT` or `IN OUT` parameter, your application can experience performance and memory degradation due to all this copying.

If you experience such degradation, you can consider two options:

- Use the `NOCOPY` hint to ask the PL/SQL compiler to not make a copy of your data structure.
- "Globalize" the data structure, so that instead of passing that large, complex structure as an argument, you reference it directly within the program.
