# Configuring TSDB Storage
EnOS Time Series Database (TSDB) enables you to store and retrieve important and frequently-accessed business data. TSDB provides specific storage types for different types of business data. Each storage type has specific data storing and reading capability. You can define customized data storage policies based on your business needs. Currently, EnOS TSDB provides the following storage types:
- AI Raw Data
- AI Normalized Data
- DI Data
- Generic Data

## AI Raw Data
AI (analogy input) data consists of physical parameters like temperature, pressure, flow, etc. The values of these parameters are collected by various sensors, converted to electric signals by a transmitter, and transferred to the analogy input of the controller. To reflect real-time data changes, AI data generally has high ingestion frequency, usually by seconds, and thus having huge data size. In most business cases, the second-level raw data is usually normalized by minute-level processing, so this kind of second-level raw data does not need to be stored for a long time. EnOS TSDB storage supports storing second-level AI raw data, with the following requirements:
- **Storage limit**: Measure point data type must be AI type.
- **Retrieving data**: Supporting retrieving stored data by time range, with the `getAssetsAIRawData` API.

## AI Normalized Data
As described in the above section, the second-level raw data is usually normalized by minute-level processing in most business cases to reduce the data size. EnOS TSDB stores the normalized data separately and supports extra processing for the stored data. When you retrieve the minute-level normalized data with API, EnOS TSDB provides aggregation functions for further data processing.
- **Normalization processing**: When you select the **AI Normalized Data** storage type, the second-level suffix of the data timestamp will be removed when the AI data is stored in TSDB. Therefore, only the last-coming data record of a minute will be stored.
- **Aggregation functions**: The data size of minute-level normalized data is much smaller, so TSDB provides aggregation functions for developers to further process the stored data when retrieving data with the the `getAssetsAINormalizedData` API. Supported aggregation functions are as follows:
   -  **max**: Compare all valid record values in the specified time window and output the maximum value.
   -  **min**: Compare all valid record values in the specified time window and output the minimum value.
   -  **avg**: Calculate and output the average value of all valid record values in the specified time window.
   -  **sum**: Calculate and output the sum value of all valid record values in the specified time window.
   -  **cnt**: Count all valid record values in the specified time window and output the total number.

## DI Data
DI (digital Input) data is usually used for recording device status. For example, a sensor outputs the device running status, such as water flow switch and wind speed switch. The switch status is transferred to the controller and then converted to digital value 1 or 0, which can be used for logic analysis and computation. DI data is usually enumerable status values, and the frequency of data upload is not fixed. Generally, data is upload or stored only when device status changes. For DI data, EnOS TSDB provides separated storage and reading policy, with the following requirements:
- **Storage limit**: Measure point data type must be DI type.
- **Retrieving status change data**: Supporting retrieving device status change data. When you query DI data in a specific time range, if no DI is found at the start time, the `getAssetsStatusData` API will search forward for the nearest record. The nearest record will be returned if it is found in the search.

<!--

## PI数据

PI（Pulse Input）即脉冲量输入, 一般用于电能计量。PI量一般分为两种，一种是功率；一种是电表读数；TSDB提供这两类PI量的存储并基于这两类PI量计算电价的读取方式，具体详情如下：
- **存储限制**：只有测点类型是PI的数据+配置了PI流式计算任务的输出点才能进行PI数据存储。
- **读取能力**：目前只支持用户输入时间区间对“PI”类型数据的读取，对应的数据读取Open API 是[getAssetsProductionData](/xx)

-->

## Generic Data

When configuring device models, you can choose AI, DI, or Generic as the data type of a measure point. EnOS TSDB provides separate storage policy for generic data, with the following requirements:
- **Storage limit**: Measure point data type must be generic type.
- **Retrieving data**: Supporting retrieving stored data by time range, with the `getAssetsGenericData` API.

