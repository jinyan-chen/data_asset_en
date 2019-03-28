# Configuring TSDB Storage Type
EnOS Time Series Database (TSDB) enables you to store and retrieve important and frequently-accessed business data. TSDB provides specific storage types for different types of business data. Each storage type has specific data storing and reading capability. You can define customized data storage policies based on your business needs. Currently, EnOS TSDB provides the following storage types:
- AI Raw Data
- AI Normalized Data
- DI Data
- Generic Data

## Configuring AI Raw Data Storage Type
AI (analogy input) data consists of physical parameters like temperature, pressure, flow, etc. The values of these parameters are collected by various sensors, converted to electric signals by a transmitter, and transferred to the analogy input of the controller. To reflect real-time data changes, AI data generally has high ingestion frequency, usually by seconds, and thus having huge data size. In most business cases, the second-level raw data is usually normalized by minute-level processing, so this kind of second-level raw data does not need to be stored for a long time. 

Features of the AI Raw Data storage type are as follows:

| Feature              | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| Data type            | AI type data only (the data type is selected when defining a measure point) |
| Data source          | Measure point raw data uploaded to the cloud (or normalized data processed by the streaming engine) |
| Storage time         | Based on business needs (it is recommended to select a short storage time due to the huge data size) |
| API for reading data | `getAssetsAIRawData` (getting the stored AI raw data of certain measure points of specified assets in a time range) |

Take the following steps to configure AI Raw Data storage type:

1. Open the **Storage Policy** page and select the created storage policy group.

2. Move the cursor on the **AI Raw Data** storage type and click the **Edit** icon to open the **Edit Storage Policy** page.

3. From the **Storage Time** drop down list, select the storage time for your data.

4. Select models and the corresponding measure points for which the data storage policy serves.

5. Click **OK** to save the storage policy. See the following example.

   .. image:: media/storage_policy_config_1.png

## Configuring AI Normalized Data Storage Type
As described in the above section, the second-level raw data is usually normalized by minute-level processing in most business cases to reduce the data size. EnOS TSDB stores the normalized data separately and supports extra processing for the stored data. When you retrieve the minute-level normalized data with API, EnOS TSDB provides aggregation functions for further data processing.

Features of the AI Normalized Data storage type are as follows:

| Feature                  | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Data type                | AI type data only (the data type is selected when defining a measure point) |
| Data source              | Normalized data processed by the streaming engine (or measure point raw data uploaded to the cloud) |
| Normalization processing | If the data source is AI raw data, the second-level suffix of the data timestamp will be removed when the data is stored in TSDB. Therefore, only the last-coming data record of a minute will be stored. |
| Storage time             | Based on business needs (can be a longer time due to the smaller data size) |
| API for reading data     | `getAssetsAINormalizedData` (getting the stored minute-level normalized AI data of certain measure points of specified assets in a time range) |
| Aggregation functions    | TSDB provides aggregation functions for further processing the stored data when retrieving data with the `getAssetsAINormalizedData` API. Supported aggregation functions are `cnt`, `avg`, `sum`, `max`, `min`, `first`, and `last`. Note that if data aggregation logic is NOT used, the value of the `interval` parameter must be 0. |

The configuration of the **AI Normalized Data** storage type is similar with that of the **AI Raw Data** storage type. See the following example.

.. image:: media/storage_policy_config_2.png

## Configuring DI Data Storage Type
DI (digital Input) data is usually used for recording device status. For example, a sensor outputs the device running status, such as water flow switch and wind speed switch. The switch status is transferred to the controller and then converted to digital value 1 or 0, which can be used for logic analysis and computation. DI data is usually enumerable status values, and the frequency of data upload is not fixed. Generally, data is upload or stored only when device status changes. For DI data, EnOS TSDB provides separated storage and reading policy.

Features of the DI Data storage type are as follows:

| Feature              | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| Data type            | DI type data only (the data type is selected when defining a measure point) |
| Data source          | Measure point raw data uploaded to the cloud                 |
| Storage time         | Based on business needs (can be a long time due to the small data size) |
| API for reading data | `getAssetsStatusData` (Getting the status change data of specified assets in a time range. If no DI is found at the start time, the `getAssetsStatusData` API will search forward for the nearest record. The nearest record will be returned if it is found in the search.) |

The configuration of the **DI Data** storage type is similar with that of the **AI Raw Data** storage type.

<!--

## PI数据

PI（Pulse Input）即脉冲量输入, 一般用于电能计量。PI量一般分为两种，一种是功率；一种是电表读数；TSDB提供这两类PI量的存储并基于这两类PI量计算电价的读取方式，具体详情如下：
- **存储限制**：只有测点类型是PI的数据+配置了PI流式计算任务的输出点才能进行PI数据存储。
- **读取能力**：目前只支持用户输入时间区间对“PI”类型数据的读取，对应的数据读取Open API 是[getAssetsProductionData](/xx)

-->

## Configuring Generic Data Storage Type

When configuring device models, you can choose AI, DI, or Generic as the data type of a measure point. EnOS TSDB provides separate storage policy for generic data.

Features of the Generic Data storage type are as follows:

| Feature              | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| Data type            | Generic type data only (the data type is selected when defining a measure point) |
| Data source          | Measure point raw data uploaded to the cloud                 |
| Storage time         | Based on business needs                                      |
| API for reading data | `getAssetsGenericData` (getting the generic data of certain measure points of specified assets in a time range.) |

The configuration of the **Generic Data** storage type is similar with that of the **AI Raw Data** storage type.

<!--end-->