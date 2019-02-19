# Storage Policy Overview

With the Storage Policy service, EnOS provides a variety of data storage options for users based on their data storage and reading requirements. Data is stored by categories (data type and storage time), thus reducing data storage costs and enhancing data reading efficiency.

## Features
- **TSDB**: EnOS Time Series Database supports storing important and frequently-accessed data by data types. Asset AI type data, normalized AI type data, DI type data, PI type data, and generic data can be stored separately, and the data storage time can be customized (1 month, 3 months, or 1 year). The data stored in each database can be retrieved by a specific Open API.
- **Archive DB**: The Archive database supports storing historical asset data with huge size for a longer time. Data stored in the archive DB can be used for further analysis and generating reports.
- **Open API**: Open APIs are provided for retrieving data stored with different storage policies. When reading data, the APIs can also run specific functions to process the retrieved data, thus improving the data processing efficiency.

## Advantages
- Customized data storage time
- Separate storage by data types
- Open APIs for reading stored data

## Usage Limit
- xx
- xx
- xx
