[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Limit execution section sizes to a single page using modularization](../../../../doc/coding/pl_sql/coding_style.md#LimitSize)

You write code for the real world. It's really complicated. Fifty or sixty lines? You're lucky if your programs are less than 500 lines! Well, it's not a matter of complexity; it's more an issue of how you handle that complexity.

If your executable sections go on for hundreds of lines, with a loop starting on page 2 and ending on page 6 and so on, you will have a hard time "grasping the whole" and following the logic of the program.

An alternative is to use step-wise refinement (a.k.a. "top down decomposition"): don't dive into all the details immediately. Instead, start with a general description (written in actual code, mind you) of what your program is supposed to do. Then implement all subprogram calls in that description following the same method.

The result is that at any given level (PL/SQL block) of refinement, you can take in and easily comprehend the full underlying logic at that level. This technique is also referred to as "divide and conquer."
