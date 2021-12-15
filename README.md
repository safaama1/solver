# Solver
An implementation to a solver that gets a list of variables with a range of definitions and constraints, and finds all possible solutions. 
For example the next pair of input and output:

`var x : 0 .. 9;`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`x=0, y=3`<br />
`var y : 0 .. 9;`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;===>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`x=1, y=2`<br />
`x + y is 3;`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`x=3, y=0`<br />
`x - y is not 1;`<br />
<br />
The input of the solver is organized as follows:
1. The input file contains 0 or more commands, with each command being a variable definition or constraint.
2. Variable definition is in the following format:
`var <variable_name> “:” <range_from> “..” <range_to> “;”`
  - `<variable_name>` is one letter in the lower case, i.e. [a-z].
  - The definition range of the variable is all integers in the defined range including the first and last value.
  - The two ends of the definition range are non-negative integers [0-9]+ (`<range_from>` and `<range_to>`)
3. The constraint has the following format:
`<expression> (is | is not) <number> “;”`
  - `<expression>` is some expression with the addition, subtraction and multiplication operations (+, -, *), with the usual order of operations (multiplication before addition         and subtraction), with left associativity, and with the option to put round parentheses (). 
    The atoms of the expression are non-negative integers + [0-9], and variable names [a-z]. 
