[Development Guidelines](../../../README.md) / [Coding](../../../README.md#coding) / [PL/SQL](../../../README.md#coding_pl_sql)

## [Coding Style](../../../README.md#coding_pl_sql_coding_style)

#### Coding Style and Conventions

- Standardize module and program headers. [(Details)](coding_style/StdHeader.md) <a name="StdHeader"></a>
- Tag module `END` statements with module names. [(Details)](coding_style/TagEND.md) <a name="TagEnd"></a>
- Use block and loop labels. [(Details)](coding_style/UseLabels.md) <a name="UseLabels"></a>

#### Variables and Data Structures

- Anchor variables to database datatypes using `%TYPE` and `%ROWTYPE`. [(Details)](coding_style/AnchorTypes.md) <a name="AnchorTypes"></a>
- Do not hard-code `VARCHAR2` lengths. [(Details)](coding_style/HardcodeVarchar2.md) <a name="HardcodeVarchar2"></a>
- Match datatypes to computational usage. [(Details)](coding_style/MatchDataTypes.md) <a name="MatchDataTypes"></a>
- Use `SUBTYPE` to standardize application-specific datatypes. [(Details)](coding_style/UseSubtype.md) <a name="UseSubtype"></a>
