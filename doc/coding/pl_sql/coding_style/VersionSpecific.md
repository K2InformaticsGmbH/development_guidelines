[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Insulate applications from Oracle version sensitivity using version-specific implementations](../../../../doc/coding/pl_sql/coding_style.md#VersionSpecific)

Many organizations need to write code that will run on different Oracle versions. There are two approaches you might follow in this situation:

- Use "lowest common denominator" features that are available in all versions.
- Use the best and most appropriate features available in each version.

If you take the first approach, you can maintain just one version of code, but you will also sacrifice significant functionality and performance advantages. If you take the second approach, you can avoid maintaining multiple copies of the code by (a) using packages to isolate those differences, and (b) relying on the separation of package specification and body to "execute around" compilation errors.

Here are the basic steps you need to take to achieve this effect:

1. Extract all version-specific logic into separate package bodies, separated by database version.
2. Create a function that returns the current Oracle version.
3. Modify or create the main (public) package to call each of the version-specific programs, based on the current Oracle version.
4. Compile and use the code in each different database version.

This last point is, in a way, the most interesting. You see, at least one of your package bodies will actually fail to compile—and you won't care! But that doesn't matter at all, because (a) the package specification compiles, and that's all the outer package needs for it to compile, and (b) the code in the body that didn't compile will never be called.
