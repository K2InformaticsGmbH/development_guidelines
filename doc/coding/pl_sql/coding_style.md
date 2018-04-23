[Development Guidelines](../../../README.md) / [Coding](../../../README.md#coding) / [PL/SQL](../../../README.md#coding_pl_sql)

## [Coding Style](../../../README.md#coding_pl_sql_coding_style)

#### Coding Style and Conventions

- Standardize module and program headers. [(Details)](coding_style/StdHeader.md) <a name="StdHeader"></a>
- Tag module `END` statements with module names. [(Details)](coding_style/TagEND.md) <a name="TagEnd"></a>
- Use block and loop labels. [(Details)](coding_style/UseLabels.md) <a name="UseLabels"></a>

#### Variables and Data Structures

- Anchor variables to database datatypes using `%TYPE` and `%ROWTYPE`. [(Details)](coding_style/AnchorTypes.md) <a name="AnchorTypes"></a>
- Beware of and avoid implicit datatype conversions. [(Details)](coding_style/NoImplicit.md) <a name="NoImplicit"></a>
- Centralize `TYPE` definitions in package specifications. [(Details)](coding_style/CentralizeTypes.md) <a name="CentralizeTypes"></a>
- Clean up data structures when your program terminates (successfully or with an error). [(Details)](coding_style/CleanUpDS.md) <a name="CleanUpDS"></a>
- Do not hard-code `VARCHAR2` lengths. [(Details)](coding_style/HardcodeVarchar2.md) <a name="HardcodeVarchar2"></a>
- Do not overload data structure usage. [(Details)](coding_style/OverloadDS.md) <a name="OverloadDS"></a>
- Expose package globals using "get and set" modules. [(Details)](coding_style/ExposeGetSet.md) <a name="ExposeGetSet"></a>
- Match datatypes to computational usage. [(Details)](coding_style/MatchDataTypes.md) <a name="MatchDataTypes"></a>
- Package application-named literal constants together. [(Details)](coding_style/PackAppConst.md) <a name="PackAppConst"></a>
- Perform complex variable initialization in the executable section. [(Details)](coding_style/ComplexExec.md) <a name="ComplexExec"></a>
- Remove unused variables and code. [(Details)](coding_style/RemoveUnused.md) <a name="RemoveUnused"></a>
- Replace complex expressions with Boolean variables and functions. [(Details)](coding_style/ComplexBoolean.md) <a name="ComplexBoolean"></a>
- Use `CONSTANT` declarations for variables whose values do not change. [(Details)](coding_style/UseConstant.md) <a name="UseConstant"></a>
- Use `SUBTYPE` to standardize application-specific datatypes. [(Details)](coding_style/UseSubtype.md) <a name="UseSubtype"></a>
- Use package globals judiciously and only in package bodies. [(Details)](coding_style/PackageGlobals.md) <a name="PackageGlobals"></a>

#### Control Structures

- Move static expressions outside of loops and SQL statements. [(Details)](coding_style/StaticLoop.md) <a name="StaticLoop"></a>
- Never `EXIT` or `RETURN` from `WHILE` and `FOR` loops. [(Details)](coding_style/NeverExit.md) <a name="NeverExit"></a>
- Never declare the `FOR` loop index. [(Details)](coding_style/NeverForLoop.md) <a name="NeverForLoop"></a>
- Replace and simplify `IF` statements with Boolean expressions. [(Details)](coding_style/IfByBoolean.md) <a name="IfByBoolean"></a>
- Scan collections using `FIRST`, `LAST`, and `NEXT` in loops. [(Details)](coding_style/FirstLastNext.md) <a name="FirstLastNext"></a>
- Use `ELSIF` with mutually exclusive clauses. [(Details)](coding_style/ElseIfMutually.md) <a name="ElseIfMutually"></a>
- Use `IF`...`ELSIF` only to test a single, simple condition. [(Details)](coding_style/ElseIfSimple.md) <a name="ElseIfSimple"></a>
- Use a simple loop to avoid redundant code required by a `WHILE` loop. [(Details)](coding_style/SimpleLoop.md) <a name="SimpleLoop"></a>
- Use a single `EXIT` in simple loops. [(Details)](coding_style/SimpleExit.md) <a name="SimpleExit"></a>
- Use anonymous blocks within `IF` statements to conserve resources. [(Details)](coding_style/AnonymousIf.md) <a name="AnonymousIf"></a>

#### Exception Handling

- Set guidelines for application-wide error handling before you start coding. [(Details)](coding_style/ExceptionGuide.md) <a name="ExceptionGuide"></a>

#### Writing SQL in PL/SQL


#### Program Construction


#### Package Construction


#### Built-in Packages



