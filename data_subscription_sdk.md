# Data Subscription SDK Reference
## Real-time Data Subscription
**Subscription Client Class: EOSClient**

Function|Description|Parameter|Response
---|---|---|---
EosClient(String host,int port,String accessKey,String secret)	 | Initiate constructed function. |host: Subscription service host; port; accesskey; secret: secret of the accesskey|EosClient instance
getDataService()	 | Get real-time data subscription service instance. |N/A|IDataService instance

**Real-time Data Subscription Service Class: IDataService**

Function|Description|Parameter|Response
---|---|---|---
subscribe（IDataHandler dataHandler,String subId）	 | Get subscribed real-time data of subID. |dataHandler: Data processing object; subId: Subscription ID|null
subscribe(IDataHandler dataHandler,String subId,String consumerGroup);	 |Get subscribed real-time data of subID and define the consumer group. The  "consumerGroup" parameter specifies the consumer group of the current client. The clients in a same group process subscribed data together, which improves the capability of data processing. Note that a message can be consumed by only 1 client in a consumer group. |dataHandler: Real-time data processing object; subId: Subscription ID; consumerGroup: Consumer group (If null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the value of "consumerGroup").|null

**Real-time Data Handling Class: IDataHandler**

Function|Description|Parameter|Response
---|---|---|---
dataRead(MeasurePoint point) | Read the subscribed real-time data. |point: Subscribed measure point|null



## Alert Data Subscription

**Subscription Client Class: EOSClient**

Function|Description|Parameter|Response
---|---|---|---
EosClient(String host,int port,String accessKey,String secret)	 | Initiate constructed function. |host: Subscription service host; port; accesskey; secret: secret of the accesskey|EosClient instance
getAlertService()	 | Get alert data subscription service instance. |N/A|IIAlertService instance

**Alert Data Subscription Service Class: IAlertService**

Function|Description|Parameter|Response
---|---|---|---
subscribe（IAlertHandler alertHandler,String subId）	 | Get subscribed alert data of subID (this subscription client belongs to the default consumer group). |alertHandler: Data processing object; subId: Subscription ID|null
subscribe(IAlertHandler alertHandler,String subId,String consumerGroup); |Get subscribed real-time data of subID and define the consumer group. The  "consumerGroup" parameter specifies the consumer group of the current client. The clients in a same group process subscribed data together, which improves the capability of data processing. Note that a message can be consumed by only 1 client in a consumer group. |alertHandler: Alert data processing object; subId: Subscription ID; consumerGroup: Consumer group (If null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the value of "consumerGroup").|null

**Alert Data Handling Class: IAlertHandler**

Function|Description|Parameter|Response
---|---|---|---
alertRead(Alert alert) | Read the subscribed alert data. |alert: Subscribed alert data|null


