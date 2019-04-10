# Data Subscription SDK Reference
After completing the data subscription configuration, you can use the data subscription SDK to retrieve the subscribed data. The data subscription SDK reference is as follows:

## Dependency

Before using the EnOS SDK for data subscription, add the following dependency to your Java project file:

```
<dependency>
  <groupId>com.envisioniot</groupId>
  <artifactId>enos-subscribe</artifactId>
  <version>2.0.0</version>
</dependency>
<dependency>
  <groupId>com.google.code.gson</groupId>
  <artifactId>gson</artifactId>
  <version>2.8.0</version>
</dependency>
<dependency>
  <groupId>log4j</groupId>
  <artifactId>log4j</artifactId>
  <version>1.2.16</version>
</dependency>
```



## Real-time Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host,int port,String accessKey,String accessSecret)
     - Initiate constructed function.
     - + host: Subscription service host
       + port
       + accessKey
       + accessSecret: Secret of the accessKey
     - EosClient instance
   * - getDataService()
     - Get real-time data subscription service instance.
     - N/A
     - IDataService instance

### Real-time Data Subscription Service Class: IDataService

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IDataHandler dataHandler,String subId)
     - Get subscribed real-time data of subID.
     - + dataHandler: Data processing object
       + subId: Subscription ID
     - null
   * - subscribe(IDataHandler dataHandler,String subId,String consumerGroup)
     - Get subscribed real-time data of subID and define the consumer group. The  "consumerGroup" parameter specifies the consumer group of the current client. The clients in a same group process subscribed data together, which improves the capability of data processing. Note that a message can be consumed by only 1 client in a consumer group.
     - + dataHandler: Real-time data processing object
       + subId: Subscription ID
       + consumerGroup: Consumer group (If null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the value of "consumerGroup").
     - null

### Real-time Data Handling Class: IDataHandler

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - dataRead(MeasurePoint point)
     - Read the subscribed real-time data.
     - point：Subscribed measure point data
     - null

### Code Sample

```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.data.IDataHandler;
import com.envisioniot.sub.client.data.IDataService;
import com.envisioniot.sub.common.exception.SubscribeException;
import com.envisioniot.sub.common.model.dto.StreamMessage;

public class sample {

    public static void main(String[] args) throws SubscribeException {
        String host = "subscription_server";
        int port = 9001;
        String accessKey = "access_key";
        String secretKey = "secret_key";
        String subId = "subscription_id";
        String consumerGroup = "consumer_group"; 

        /* Service */
        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);
        IDataService dataService = eosClient.getDataService();

        /* Handler */
        IDataHandler dataHandler = new IDataHandler(){

            public void dataRead(StreamMessage message) {
                System.out.println(message);
            }
        };

        /* Subscribe */
        dataService.subscribe(dataHandler, subId);
        
        /* Subscribe with consumer group (optional) */
        dataService.subscribe(dataHandler, subId, consumerGroup);

    }
}
```

.. note:: The `host` and `port` of the subscription server vary with the cloud region and instance. For private cloud instances, contact your Envision project manager or support representative to get the host and port information.

## Alert Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host,int port,String accessKey,String accessSecret)
     - Initiate constructed function.
     - + host: Subscription service host
       + port
       + accessKey
       + accessSecret: Secret of the accessKey
     - EosClient instance
   * - getAlertService()
     - Get alert data subscription service instance.
     - N/A
     - IAlertService instance


### Alert Data Subscription Service Class: IAlertService

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IAlertHandler alertHandler,String subId)
     - Get subscribed alert data of subID (this subscription client belongs to the default consumer group).
     - + alertHandler: Data processing object
       + subId: Subscription ID
     - null
   * - subscribe(IAlertHandler alertHandler,String subId,String consumerGroup)
     - Get subscribed real-time data of subID and define the consumer group. The  "consumerGroup" parameter specifies the consumer group of the current client. The clients in a same group process subscribed data together, which improves the capability of data processing. Note that a message can be consumed by only 1 client in a consumer group.
     - + alertHandler: Alert data processing object
       + subId: Subscription ID
       + consumerGroup: Consumer group (If null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the value of "consumerGroup").
     - null


### Alert Data Handling Class: IAlertHandler

.. list-table::
   :widths: 20 40 30 10

   * - Function
     - Description
     - Parameter
     - Response
   * - alertRead(Alert alert)
     - Read the subscribed alert data.
     - alert: Subscribed alert data
     - null

### Code Sample

```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.data.IDataHandler;
import com.envisioniot.sub.client.data.IDataService;
import com.envisioniot.sub.common.exception.SubscribeException;
import com.envisioniot.sub.common.model.dto.StreamMessage;

public class sample {

    public static void main(String[] args) throws SubscribeException {
        String host = "subscription_server";
        int port = 9001;
        String accessKey = "access_key";
        String secretKey = "secret_key";
        String subId = "subscription_id";
        String consumerGroup = "consumer_group"; 

        /* Service */
        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);
        IAlertService alertService = eosClient.getAlertService();

        /* Handler */
        IAlertHandler alertHandler = new IAlertHandler (){
            @Override
            public void alertRead(Alert alert) {
                System.out.println(alert);
            }
        };

        /* Subscribe */
        alertService.subscribe(alertHandler, subId);
        
        /* Subscribe with consumer group (optional) */
        alertService.subscribe(alertHandler, subId, consumerGroup);

    }
}
```

<!--end-->
