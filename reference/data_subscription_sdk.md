# Data Subscription SDK Reference
After completing the data subscription configuration, you can use the data subscription SDK to retrieve the subscribed data. The data subscription SDK reference is as follows:

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
/* service */
EosClient eosClient = new EosClient(host, port, accessKey, accessSecret);
IDataService dataService = eosClient.getDataService();

/* handler */
IDataHandler dataHandler = new IDataHandler(){
    @Override
    public void dataRead(StreamMessage message) {
        System.out.println(message);
    }
};

/* subscribe */
dataService.subscribe(dataHandler, subId);

/* subscribe with consumer group */
dataService.subscribe(dataHandler, subId, consumerGroup);
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
/* service */
EosClient eosClient = new EosClient(host, port, accessKey, accessSecret);
IAlertService alertService = eosClient.getAlertService();

/* handler */
IAlertHandler alertHandler = new IAlertHandler (){
    @Override
    public void alertRead(Event alert) {
        System.out.println(alert);
    }
};

/* subscribe */
alertService.subscribe(alertHandler, subId);

/* subscribe with consumer group */
alertService.subscribe(alertHandler, subId, consumerGroup);
```

<!--end-->
