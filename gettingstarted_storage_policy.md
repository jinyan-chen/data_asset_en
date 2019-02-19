# Configuring Data Storage
This guide introduces how to quickly configure data storage with the Storage Policy service and retrieve the stored data.



## Prerequisites

- An account to log in EnOS Console.
- Access permission to the Storage Policy module.
- Device connection is completed, and the devices are uploading data to EnOS.



## About This Task

**Goal**

The goal of this guide is to store the AI type raw data of the *test_raw* measure point in TSDB as minute-level data, and then invoke an API to get the maximum value of the *test_raw* point every 5 minutes in a specific time range.

**Data Preparation**

Model configuration: Detailed information about the (*testModel*) used for this guide is as follows:

Feature Type|Name|Identifier|Point Type |Data Type	
---|---|---|---|---
Measure Point	 | test_raw | test_raw|AI |DOUBLE

For instructions on creating and configuring models, see [Creating a Model](https://www.envisioniot.com/docs/device-connection/en/latest/model/creating_model).

## Procedure

The steps for configuring data storage policies and retrieving stored data are as follows:
- Create a storage group
- Configure and release a storage policy
- Retrieving and aggregate data with Open API

## Step 1. Create a storage group
Log in EnOS Console and select the **Storage Policy** module. Click **New Group** to create a storage group. Enter the group name, select an asset model (select *testModel* for this guide), and save the storage group configuration.

## 第二步：配置存储策略并发布Step 2.
创建好分组后，选择TSDB，可看到TSDB下提供的几种不同类型的存储，本教程需选择*AI分钟级规整数据*，点击进入该策略之后，需进行如下配置：
- 存储时长：可按需配置存储时长，比如1个月；
- 存储测点：选择需要存储的模型测点，本教程选择*testModel*下的*test_raw*这个测点；
内容配置完成后，点击发布按钮即可完成策略配置的保存和发布，系统会根据新的配置对数据进行存储。

## 第三步：使用Open API获取聚合数据Step 3.
使用AI分钟级规整数据对应的Open API *getAssetsAINormalizedData*可获取刚刚存储的测点数据。Open API的使用请参考[调用 EnOS REST API](https://www.envisioniot.com/docs/app-development/zh_CN/latest/call_enos_api.html)。