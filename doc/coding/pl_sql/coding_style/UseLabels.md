[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use block and loop labels](../../../../doc/coding/pl_sql/coding_style.md#UseLabels)

Use a label directly in front of loops and nested anonymous blocks:
- To name that portion of code and thereby self-document what it's doing
- So you can repeat that name with the `END` statement of that block or loop

This is especially important when you have multiple nestings of loops as in the following:

```PLSQL
LOOP
    <body>
    WHILE <condition>
    LOOP
        <while body>
    END LOOP;    
END LOOP;
```

#### Example:

```PLSQL
CREATE OR REPLACE PROCEDURE display_book_usage
IS
BEGIN
    <<best_seller_review>>
    DECLARE
        CURSOR yearly_analysis_cur IS SELECT ...;
        CURSOR monthly_analysis_cur IS SELECT ...;
    BEGIN
        <<yearly_analysis>>
        FOR book_rec IN yearly_analysis_cur (2000)
        LOOP
            <<monthly_analysis>>
            FOR month_rec IN
                monthly_analysis_cur (
                    yearly_analysis_cur%rowcount)
            LOOP
            ... lots of month-related code ...
            END LOOP monthly_analysis;
            ... lots of year-related code ...
        END LOOP yearly_analysis;
    END best_seller_review;
END display_book_usage;
```
