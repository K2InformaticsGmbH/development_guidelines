[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use package body persistent data structures to cache and optimize data-driven processing](../../../../doc/coding/pl_sql/coding_style.md#BodyPersistent)

When you declare data inside a package but not within any individual procedure or function in the package, that data persists for your entire session. A package-level collection, for example, retains its values (say, 1000 rows of data) until you `DELETE` one or more rows from the collection, close your connection, or recompile the package.

This data persistence means you can use package data as a "local" cache - local to that single session/user. The System Global Area (SGA) acts as a cache for all users and greatly improves overall database performance. Your own session-specific cache can improve your application performance. You can cache at multiple levels:

- A single value, such as the name of the current user
- A record of values, such as the default configuration for the current user
- An entire collection or list of values, such as the result set of a query that must be processed multiple times

Regardless of the complexity of data, the conditions and steps for caching are similar:

- The data must be static for the duration of the session. It's possible to come up with ways to update the cache, but such efforts are likely to cancel out performance gains.
- You need to declare the data structures inside the package body so that you can manage their contents and integrity.
- You also need to build access programs to those data structures so that even inside the package body, you manipulate the cache through a well-defined interface.
