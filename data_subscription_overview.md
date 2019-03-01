# Data Subscription

EnOS Data Subscription function improves the API calling efficiency of applications with active data push, which supports subscription to real-time asset data, asset alert data, and asset meta data.

Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, applications call APIs only when there are pushed data, thus improving API calling efficiency and reducing costs.

## Features

- **Multiple data source subscription**: Data subscription service supports multiple data sources such as real-time asset data, asset alert data, etc.
- **Visualized configuration**: A GUI is available for you to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription topics.
- **Data subscription SDK**: Java SDK is provided for you to consume subscribed data in your applications.

## Advantages

- Decoupling data production and data consumption
- Rich set of data filtering conditions (organization, model, measure point, and asset)
- Cross-organization data subscription (through service account)
- Supporting "at-least-once" message delivery semantics
- "Pulling subscribed data" consumption model, supporting traffic control of the consumer
- Supporting consumer groups (a topic can be consumed by multiple consumers repeatedly)

## Usage Limit

- At most 5 subscription topics are supported for an organization.
- Each topic has 2 partitions, that is, each topic allows at most 2 consumers at the same time.
- Currently, a consumer can consume 1 topic only.
- By default, data are stored in the topic for 3 days.
