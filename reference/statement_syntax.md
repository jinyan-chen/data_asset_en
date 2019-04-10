# Multi-Point Aggregation Expression Syntax

The supported syntax for the processing logic expressions is described in the following table:

.. list-table::
   :widths: 20 20 60

   * - Expression Symbol
     - Function
     - Description
   * - $
     - Variable selector
     - The format is `​${ variable }`, in which `variable` can be a model, a measure point, or an attribute of a model.
   * - if...else
     - Conditional statement
     - If the condition is true, the statement runs a code. If the condition is false, the statement runs another code. The format of the statement is: `if (condition) { the code to be run when condition is true} else { the code to be run when condition is false}`.
   * - if...else if...else
     - Conditional statement
     - Run one of multiple codes by different conditions. The format of the statement is: `if (condition 1) { the code to be run when condition 1 is true} else if (condition 2) { the code to be run when condition 2 is true} else { the code to be run when conditions 1 and 2 are false}`.
   * - "::"
     - Namespace identifier
     - Refer to the C++ syntax. The format of the statement is: `class name (model)` :: `class member (measure point / attribute)`.
   * - "+ - * /"
     - Arithmetic operators
     -
   * - "! && |"
     - Logical operators
     -

.. note:: Multi-Point Merge expressions support Scala syntax, but do not support loop statements like for and while.

## Variable Autocomplete Feature

Automatic detection and completion of variables in the logic expression is enabled. When you write the logic expression, the system automatically detects all models, measure points, and attributes in the organization. See the following sample:

.. image:: ../media/autocomplete.gif

## Expression Example
```scala
if(${turbine::wind_speed} > 50) {
    ${turbine::power}+10
} 
else {
    ${turbine::power}-10
}
```

The function of the above expression is: If `wind_speed` is greater than 50, the output is `power+10`. Otherwise, the output is `power-10`. 



<!--end-->