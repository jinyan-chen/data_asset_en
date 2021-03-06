# Developing a Data Aggregation Stream
The general process of developing a data aggregation stream is as follows:

1. Create a data aggregation stream
2. Configure the data aggregation stream with necessary parameters
3. Save and release the data aggregation stream online
4. Run and monitoring the status of the data aggregation stream

## Creating a Stream
EnOS Streaming System supports creating a data processing stream and importing the configuration file of an existing stream. Take the following steps to create a processing task for the battery temperature data:

1. Log in EnOS Console and click **Stream Data Processing** > **Stream Development**.
2. Click the **+** icon above the stream list to open the **New Stream** window. Enter the name and description of the stream processing task and select one of the following templates for data processing.
   - Window Aggregation for AI
   - Multi-Point Merge
3. Click **OK** to complete creating the data aggregation stream.

EnOS Streaming System also supports importing the configuration file of an existing stream to create a stream quickly.

## Configuring the Stream
EnOS Streaming System provides templates to enable developers configure the following streams:
- Window Aggregation for AI template: Supporting AI data aggregation for a measure point and assigning the processed data to another measure point on the same device. For details, see [AI Data Aggregation Template](../learn/ai_template_overview).  
- Multi-Point Merge template: Supporting expression processing of multiple measure points of a device and assigning the processed data to another measure point on the same device. For details, see [Multi-Point Merge Template](../learn/multi_point_overview).

## Releasing the Stream
After the stream configuration is completed, you can release it online. Before that, other processing of the stream can be performed, such as saving the stream configuration, setting alarms, reverting the configuration to the online version, and exporting the configuration.
- **Save**: After the stream configuration is completed, click **Save** to save the configuration, so that the stream can be released online.
- **Release**: After the stream configuration is saved, click **Release** to release the stream online.
  .. note:: Before releasing the stream online, ensure that the stream does not have an online running version.
- **Export**: If you want to reuse the stream configuration, click **Export** to export the configuration file to a local directory. When creating more streams, you can import the saved configuration file for reference.
- **Revert to Online Version**: When you are in the progress of editing the stream configuration of an online version and get unsatisfied with the changes, you can revert the configuration to the online version with one click.
- **Alarm Setting**: For each stream, an alarm can be set to report errors through email or SMS. When errors are reported for running streams, the owner of the stream will receive notification.
