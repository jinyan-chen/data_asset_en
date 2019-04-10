# Getting Stored Data with EnOS APIs

When storage policies are configured for the data of your devices, both the device raw data uploaded to the Cloud and the data processed by the streaming engine will be stored in EnOS TSDB. You can invoke the corresponding API to get the stored data.

## EnOS Data Service APIs

For each TSDB storage type, you can invoke a data service API to get the stored data. The function and usage of the data service APIs is described below.

| API Name                      | Function                                                     | Usage Note                                                   |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `getAssetsAIRawData`          | Get asset data stored as the **AI Raw Data** storage type in TSDB. | Query the stored data by combination of device model ID, asset IDs, measure point IDs, and time rage. |
| `getAssetsAINormalizedData`   | Get asset data stored as the **AI Normalized Data** storage type in TSDB. | Query the stored data by combination of device model ID, asset IDs, measure point IDs with data aggregation logic, aggregation time interval, and time range. Note that if data aggregation logic is NOT used, the value of the `interval` parameter must be 0. |
| `getAssetsStatusData`         | Get asset data stored as the **DI Data** storage type in TSDB. | Query the status change data of devices by combination of device model ID, asset IDs, measure point IDs, and time rage. |
| `getAssetsGenericData`        | Get asset data stored as the **Generic Data** storage type in TSDB. | Query the stored generic data by combination of device model ID, asset IDs, measure point IDs, and time rage. |
| `getAssetsRawDataByTimeRange` | Get asset data stored as the **AI Raw Data**, **DI Data**, and **Generic Data** storage types in TSDB. | Query the stored asset raw data by combination of device model ID, asset IDs, measure point IDs, and time rage. |

## EnOS API SDK for Java

EnOS provides an API SDK to help you calling the EnOS service APIs and developing applications offline. To install the EnOS API SDK for Java, you can get the Maven dependency information of the SDK and add it to your development project. Detailed steps are as follows:

1. Open the Maven repository of the SDK at https://mvnrepository.com/artifact/com.envisioniot/enos-api/2.3.3.

2. Open your development environment, add the maven dependency for the SDK in your Java project. See the following example.

   ```
   <dependency>
       <groupId>com.envisioniot</groupId>
       <artifactId>enos-api</artifactId>
       <version>2.3.3</version>
   </dependency>
   ```

Optionally, you can download the source code of the EnOS API SDK from [GitHub](https://github.com/EnvisionIot/enos-api-sdk-java) and install it in your development environment. 

For more information about how to work with EnOS SDK, see [Getting Started with EnOS SDKs](https://www.envisioniot.com/docs/app-development/en/latest/gettingstarted_sdk.html).

## Code Sample

The following code sample is for calling the `getAssetsAIRawData` API to get stored data in TSDB:

```
import com.envisioniot.enos.enosapi.api.request.dataservice.GetAssetsAIRawDataRequest;
import com.envisioniot.enos.enosapi.common.exception.EnOSApiException;
import com.envisioniot.enos.enosapi.common.response.EnOSPage;
import com.envisioniot.enos.enosapi.common.response.EnOSResponse;
import com.envisioniot.enos.enosapi.sdk.client.EnOSDefaultClient;

import java.util.List;
import java.util.Map;

public class demo {
    public static void main(String[] args) {
    String enosApiUrl = "api_service_url";
    String accessKey = "access_key";
    String secretKey = "secret_key";
    int connectTimeout = 5000;
    int readTimeout = 5000;
    String orgId = "organization_id";
    String modelId = "model_id";
    String assetIds = "asset_id";
    String measurepoints = "measure_point_id";
    String startTime = "2019-03-21T09:00:00-08:00";
    String endTime = "2019-03-26T09:12:00-08:00";
    int pageSize = 100;

    EnOSDefaultClient client = new EnOSDefaultClient(enosApiUrl, accessKey, secretKey, connectTimeout, readTimeout);
    GetAssetsAIRawDataRequest request = new GetAssetsAIRawDataRequest(orgId, modelId, assetIds, measurepoints, startTime, endTime, pageSize);

    try {
        EnOSResponse<EnOSPage<Map<String, Object>>> response = client.execute(request);
        System.out.println("REQUEST："+request.getUrlParams());

        if (response.getData() != null) {

            System.out.println("DATA：" + response.getData().getData());
        }
        System.out.println("STATUS：" + response.getStatus());
        System.out.println("MSG：" + response.getMsg());
        System.out.println("SUBMSG：" + response.getSubmsg());

        EnOSPage<Map<String, Object>> tmpMap = response.getData();

        if (tmpMap != null) {

            List<Map<String, Object>> re = tmpMap.getData();

            for (Map<String, Object> r : re) {
                System.out.println("timestamp:" + r.get("timestamp"));
                break;
            }
        }

    } catch (EnOSApiException e) {
        e.printStackTrace();
    }
  }
}
```

## API Reference

The reference documentation for each API can be found through **EnOS API** > **API Documents** in the EnOS Console. Summary of APIs is displayed in tables by API service categories. Click the **More** icon for each API to view details, including API function, calling method, requesting URL, parameter description, calling sample, and response sample.

.. image:: ../media/api_doc.png

For more information about how to use EnOS API, see [Getting Started with EnOS REST APIs](https://www.envisioniot.com/docs/app-development/en/latest/gettingstarted_api.html).

<!--end-->
