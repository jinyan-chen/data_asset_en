# Configuring Data Storage
This guide introduces how to quickly configure data storage with the Storage Policy service and retrieve the stored data with EnOS Open APIs.



## Prerequisites

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

For instructions on creating and configuring models, see [Creating a Model](https://www.envisioniot.com/docs/device-connection/en/latest/howto/model/creating_model.html).

## Procedure

The steps for configuring data storage policies and retrieving stored data are as follows:
- Create a storage group
- Configure and save a storage policy
- Retrieving and aggregate data with Open API

## Step 1. Create a storage policy group
Log in EnOS Console and select the **Storage Policy** module. Click **New Group** to create a storage policy group. Enter the group name, select a group model (select *testModel* for this guide), and click **OK** to save the storage group configuration.

## Step 2. Configure storage policy
After the storage group is created, you can see all the TSDB storage policy options listed under the storage group tab. Select the **AI Normalized Data** policy for this guide. On the **Edit Storage Policy** page, complete the following configuration:
- **Storage Time**: Select the data storage time (for example, 1 month). 
- **Select Points**: Select models and corresponding measure points. Data of the selected measure point will be stored according the storage policy configuration. Select the *test_raw* point of the *testModel* model for this guide.

Click **OK** to save the storage policy configuration. The system will store the data of the *test_raw* measure point according to the configuration. For this guide, the second-level suffix of the data timestamp will be removed when the AI data is stored in TSDB. Therefore, only the last-coming data record of a minute will be stored.

## Step 3. Retrieve stored data with API

Use the *getAssetsAINormalizedData* API to retrieve the stored normalized data of the measure point. For more information about EnOS Open APIs, see [Calling EnOS REST APIs](https://www.envisioniot.com/docs/app-development/en/latest/call_enos_api.html).