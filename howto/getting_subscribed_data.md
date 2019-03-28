# Getting Subscribed Data

When storage policies are configured for the data of your devices, both the temperature raw data uploaded to the Cloud and the data processed by the streaming engine will be stored in EnOS TSDB. You can invoke the corresponding API to get the stored data.

## EnOS SDK for Getting Subscribed Data

EnOS provides an API SDK to help you calling the EnOS service APIs and developing applications offline. To install the EnOS API SDK for Java, you can get the Maven dependency information of the SDK and add it to your development project. Detailed steps are as follows:

1. Open the Maven repository of the SDK at https://mvnrepository.com/artifact/com.envisioniot/enos-api/2.3.3.

2. Open your development environment, add the maven dependency for the SDK in your Java project. See the following example.

   ```
   <dependency>
       <groupId>com.envisioniot</groupId>
       <artifactId>enos-api</artifactId>
       <version>2.3.3</version>
       <!--You might need to change the version number as you need.-->
   </dependency>
   ```

Optionally, you can download the source code of the EnOS API SDK from [GitHub](https://github.com/EnvisionIot/enos-api-sdk-java) and install it in your development environment. 

For more information about how to work with EnOS SDK, see [Getting Started with EnOS SDKs](https://www.envisioniot.com/docs/app-development/en/latest/gettingstarted_sdk.html).

## SDK Reference

The reference documentation for each API can be found through **EnOS API** > **API Documents** in the EnOS Console. Summary of APIs is displayed in tables by API service categories. Click the **More** icon for each API to view details, including API function, calling method, requesting URL, parameter description, calling sample, and response sample.

.. image:: ../media/api_doc.png

For more information about how to use EnOS API, see [Getting Started with EnOS REST APIs](https://www.envisioniot.com/docs/app-development/en/latest/gettingstarted_api.html).

<!--end-->
