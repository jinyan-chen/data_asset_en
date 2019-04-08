# Multi-Point Aggregation Template
In IoT business scenarios, the data of a measure point might be calculated from the data of other measurement points of the same device. For example, *point_C = point_A + point_B*. In which, *point_A* and *point_B* are measure points for ingesting asset raw data. EnOS Stream Analytics provides a Multi-Point Aggregation template to enable data calculation among multiple measure points of the same device. 

## Features
1. Supporting calculation among multiple measure points of the same device.
2. Data processing triggered by the data arrival of a measure point or by fixed frequency.
3. Supporting timing interpolation strategy (if the data of a measure point does not arrive when calculation starts, the latest data of the measure point will be used for calculation).
4. Supporting associated calculation with master data.
5. Strong syntax for calculation expressions.
6. Autocomplete feature works for all the defined models, measure points, and attributes.

<!--

## Data Sources

The data involved in the calculation must belong to the same device model. The variables in the calculation expression can be measure points and attributes of the model. When writing the data processing expression, you must use measure points and attributes that have been declared as data sources. The conditions for configuring data sources are as follows:

- Multiple models are supported
- Multiple measure points and attributes in a model are supported

-->

## Triggering Mode

The Multi-Point Aggregation template currently supports triggering data processing by a measure point or by fixed frequency.

**Triggering by point**

When designing a data processing strategy record, you need to select a measure point as the triggering point. Each time when the data of this measure point arrives, the data processing task will be triggered. The data time stamp of the triggering point will be used as the time stamp of the output record.

If the data of a measure point does not arrive when a data processing task is triggered, the latest data record of the measure point will be used for calculation. This is called **Timing Interpolation**.   

**Triggering by frequency**

The data processing task is triggered by the specified frequency. The system time of EnOS Streaming Engine is used for controlling the trigger. When each data processing task starts, the latest data of measure points will be used for calculation.  

## Data Processing Strategy
When the triggering mode is "Point", the configuration of a data processing strategy record is as follows:

- **Output Point**: The measure point that receives the output value of the data processing expression. Supported data types include int, float, string, and bool (other types will be converted to string).
- **Output Logic**: The data processing expression. For supported syntax of the expression, see [Multi-Point Aggregation Expression Syntax](../reference/statement_syntax).
- **Triggering Point**: The measure point that triggers the data processing strategy. The triggering point, output point, and the measure points and attributes used in the data processing expression must belong to the same model. The triggering point cannot be the output point.

When the triggering mode is "Frequency", the configuration of a data processing strategy record is as follows:

- **Output Point**: The measure point that receives the output value of the data processing expression. Supported data types include int, float, string, and bool (other types will be converted to string).
- **Output Logic**: The data processing expression.










