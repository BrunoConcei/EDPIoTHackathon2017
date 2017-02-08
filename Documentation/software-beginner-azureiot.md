# [Introduction to Azure IoT](#introduction-to-azure-iot) 


### What is Internet of Things? 
The Internet of Things (IoT) starts with your things—the things that matter most to your business. IoT is about making your data come together in new ways. Tap into data with IoT dashboards. Uncover actionable intelligence. And modernize how you do business. 

You can **connect any asset** that’s important to you - with confidence – from robotics to low-power devices, across any platform or operating system. Easily scale from a few devices to a few million.

**Capture alarms and alerts** from all of your connected assets spread around the world. Spot issues before they become operational problems. Take advantage of advanced analytics and machine learning to increase reliability and uptime of your processes. Decrease costly outages and expensive repairs with prescriptive maintenance. And, take preemptive actions instead of understanding just the “what” and “why” behind a prediction.

Create **rich IoT dashboards** and reports to show anything from high-level performance KPIs to the details of an individual asset. Customize visualization so the right people have access to the metrics that matter to them, updated in real-time. Access data and reports from any device, anywhere; and publish reports to your organization.

Integrate with your business processes by automating previously manual processes by bringing IoT data to your existing business systems such as CRM, ERP, and supply chain. 


### Azure and IoT 

Microsoft Azure cloud platform has gone well beyond mere virtual machines and orchestrated workflows. It can now also power internet of things (IoT) solutions or applications. Today we have an Azure-based internet of things (IoT) platform to serve companies with connected devices.
This platform will help you create the scalable backends to support your connected devices, as well as, manage thousands of devices, removing the complexity and cost of scaling. But how does it work?

All the Azure services can be used to build your application, but there is also a set of services specifically built to support and implement an IoT scalable solution. Let's focus on this particular services:

- **Event Hubs** : Receive telemetry from millions of devices;
- **Azure IoT Hub** : Connect, Monitor and control billions of IoT assets;
- **Stream Analytics** : Real-time data stream processing from millions of IoT devices;
- **Machine Learning** : Powerfull cloud-based predictive analytics tool to enable predictive maintenance;

If you want to understand better how the Azure can help you implement IoT solutions read this [article](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-what-is-azure-iot).

Although there are other services that may become handy, let's dive in each of these services:


#### Event Hubs

Azure Event Hubs is a highly scalable data ingress service that can ingest millions of events per second so that you can process and analyze the massive amounts of data produced by your connected devices and applications. Event Hubs acts as the "front door" for an event pipeline, and once data is collected into an Event Hub, it can be transformed and stored using any real-time analytics provider or batching/storage adapters. Event Hubs decouples the production of a stream of events from the consumption of those events, so that event consumers can access the events on their own schedule. 

Event Hubs is an event processing service that provides event and telemetry processing at massive scale, with low latency and high reliability. This service is especially useful for:
- Application instrumentation
- User experience or workflow processing
- Internet of Things (IoT) scenarios

Some other key Event Hubs capabilities include behavior tracking in mobile apps, traffic information from web farms, in-game event capture in console games, or telemetry collected from industrial machines or connected vehicles.


#### Azure IoT Hub

**Azure IoT Hub** is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end. Azure IoT Hub:

- Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.
- Provides built-in declarative message routing to other Azure services.
- Provides a queryable store for device metadata and synchronized state information.
- Enables secure communications and access control using per-device security keys or X.509 certificates.
- Provides extensive monitoring for device connectivity and device identity management events.
- Includes device libraries for the most popular languages and platforms.

You may have questions around using *Event Hub* or *Azure IoT Hub*. It will depend on your project needs. To help you out, there is an interesting article to guide you: [Comparison of Azure IoT Hub and Azure Event Hubs](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-compare-event-hubs)


#### Stream Analytics

Azure Stream Analytics is a fully managed, cost effective real-time event processing engine that helps to unlock deep insights from data. Stream Analytics makes it easy to set up real-time analytic computations on data streaming from devices, sensors, web sites, social media, applications, infrastructure systems, and more.

With a few clicks in the Azure portal, you can author a Stream Analytics job specifying the input source of the streaming data, the output sink for the results of your job, and a data transformation expressed in a SQL-like language. You can monitor and adjust the scale/speed of your job in the Azure portal to scale from a few kilobytes to a gigabyte or more of events processed per second.

There are also open-source solutions that offer similar capabilities. For instance, Apache Storm on HDinsight is usually compared with Stream Analytics. If you're interested, you can get [Help choosing a streaming analytics platform: Apache Storm comparison to Azure Stream Analytics](https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-comparison-storm).


#### Machine Learning

Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.

These forecasts or predictions from machine learning can make apps and devices smarter. When you shop online, machine learning helps recommend other products you might like based on what you've purchased. When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud. When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.

For a brief overview, try the video series [Data Science for Beginners](https://docs.microsoft.com/en-us/azure/machine-learning/machine-learning-data-science-for-beginners-the-5-questions-data-science-answers). Without using jargon or math, Data Science for Beginners introduces machine learning and steps you through a simple predictive model.

Azure Machine Learning is a cloud predictive analytics service that makes it possible to quickly create and deploy predictive models as analytics solutions.
You can work from a ready-to-use library of algorithms, use them to create models on an internet-connected PC, and deploy your predictive solution quickly. Start from ready-to-use examples and solutions in the [Cortana Intelligence Gallery](https://gallery.cortanaintelligence.com/).

Finally, you can deploy your model as a web service. Quickly create, test, operationalize, and manage predictive models.

---

Having understood IoT related services in Azure, let's dive in the software details of Sigfox : [Understanding SIGFOX](software-beginner-sigfox.md)

To continue diving in the Azure services, step into the intermediate documentation : [Software Intermediate Azure IoT](software-intermediate-azureiot.md).

[Go Back](software-beginner.md)






