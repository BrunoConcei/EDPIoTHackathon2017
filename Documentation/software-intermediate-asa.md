# [Diving into Stream Analytics](#diving-into-stream-analytics)


You can use Stream Analytics to process and route IoT Data. It allows you to do real-time data processing in the cloud. Let learn how to create a new Stream Analytics job and define the input data stream as the data coming from your IoT Hub. Next you will define an output data stream that sends data to Power BI. Finally, you will write a SQL-like query that collects data coming in on the input stream and routes it to the output stream.

If you prefer to understand how Stream Analytics can be used to process data from IoT Devices, check [this](https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-get-started-with-azure-stream-analytics-to-process-data-from-iot-devices)
 article.

###Create the Stream Analytics Job
Open a new browser tab and navigate to the [https://portal.azure.com](https://portal.azure.com). 

1. In the Azure portal, click the green plus sign in the top-left corner of the page to create a new Stream Analytics job. Select Intelligence + Analytics and then click Stream Analytics job.

 ![Create an Azure Stream Analytics](/images/asa-create.png)
2. Provide a job name, validate the subscription is correct and then create a new Resource group in the same region as the Event hub storage (default is South Central US for the script).
3. Click CREATE at the bottom of the page.

 ![Configure the Azure Stream Analytics](/images/asa-configure.png)
4. The job will create and open the job page. Or you can click the created analytics job on the portal dashboard.

###Define input sources

1. Click the INPUTS tab to define the source data.

 ![Input jobs in Azure Stream Analytics](/images/asa-jobinput.png)
2. Click ADD AN INPUT.

 ![Add an input job in ASA](/images/asa-create-jobinput.png)
3. Enter a name for your input as INPUT ALIAS.
4. Source Type is Data Stream
5. Source is IoT Hub.
6. Endpoint should be *Messaging*.
7. The shared access policy name can be *iothubowner*. You can also create a spefici policy to use in this integration between IoT Hub and Stream Analytics.
8. Select JSON for EVENT SERIALIZATION FORMAT and UTF8 for ENCODING.

 Your settings will look like:

 ![input job configuration in ASA](/images/asa-jobinput-config.png)
9. Click CREATE at the bottom of the page to finish the wizard.

Now that you've created the input stream, you will follow the same steps to create the output stream.

###Define output

Here we're creating an example, of building an output stream to PowerBI, so you can visualize your data.
However there are several possibilities around the output targets in Stream Analytics. Here it will depend on your needs.
For example, you can directly connect Stream Analytics to a SQL database, a blob or table storage, Event Hub, a Service Bus Queue or Topic, a DocumentDB, a Data Lake Store or PowerBI.

Let's start, then: 

1. On the Stream Analytics job overview pane, select OUTPUTS.
2. Click Add.
3. Enter a name for your output as OUTPUT ALIAS.
4. Define the Sink as Power BI.
5. You'll have to authorize the connection between Power BI and Microsoft Azure. Remember that this output will need access to your Power BI dashboard.

 In this step, supply a work or school account for the Stream Analytics job output. If you already have Power BI account, select Authorize Now. If not, choose Sign up now. [Here is a good blog walking through details of Power BI sign up](http://blogs.technet.com/b/powerbisupport/archive/2015/02/06/power-bi-sign-up-walkthrough.aspx).

7. After authenticating and authorizing, you will be asked to configure the Power BI output:
**Group Workspace** – Select a workspace in your Power BI tenant under which the dataset will be created.
**Dataset Name** - Provide a dataset name that you want your Power BI output to have. 
**Table Name** - Provide a table name under the dataset of your Power BI output. Currently, Power BI output from Stream Analytics jobs may only have one table in a dataset.

8. Click CREATE at the bottom of the page to finish the wizard.

###Write the Query

1. Go to the Query tab of your job. Write your query, the output of which you want in your Power BI. 

 In the query, you want to select data from the input stream and put it into the output stream. With data like energy and power you can do interesting things like apply operations on the data as you query it. For this example, you will write a query that selects from the input stream and send the output stream the minimum, maximum and average values from the data coming in, and enables you to group the data by either location or device ID. Using a TumblingWindow you will send data to the output stream in rolling increments of 5-seconds. 

2. Write your query. Here is an example query:

 ```SQL
 SELECT
    MAX(enrg) AS enrg,
    MAX(pwr) AS pwr,
    System.TimeStamp AS time,
    dspl
 INTO
    OutputPBI
 FROM
    InputEDPIoTHub TIMESTAMP BY time
 GROUP BY
    TUMBLINGWINDOW(ss,1),
    dspl 
 ```
3. Click SAVE in the lower middle of the screen. Once the query is saved, click **START** to start the Stream Analytics job. It will take a few minutes for the Stream Analytics job to get started and to start sending data to Power BI, but you should see the the dataset and tabe names showing up in Power BI within a few minutes.

**Congratulations**, you've now gone through the steps of conigurating an Azure Stream Analytics(ASA). Now thing of your project needs and take advantage of Stream Analytics. Most important is the ASA query language. We recomend you to check the following additional documentation:

- [Data connection: Learn about data stream inputs from events to Stream Analytics](https://docs.microsoft.com/en-us/azure/Stream-Analytics/stream-analytics-define-inputs);
- [Stream Analytics outputs: Options for storage, analysis](https://docs.microsoft.com/en-us/azure/Stream-Analytics/stream-analytics-define-outputs);
- [Query examples for common Stream Analytics usage patterns](https://docs.microsoft.com/en-us/azure/Stream-Analytics/stream-analytics-stream-analytics-query-patterns);
- [Introduction to Stream Analytics Window functions](https://docs.microsoft.com/en-us/azure/Stream-Analytics/stream-analytics-window-functions);
- [Machine Learning integration in Stream Analytics](https://docs.microsoft.com/en-us/azure/Stream-Analytics/stream-analytics-how-to-configure-azure-machine-learning-endpoints-in-stream-analytics);



---

[Go Back](software-intermediate.md)

