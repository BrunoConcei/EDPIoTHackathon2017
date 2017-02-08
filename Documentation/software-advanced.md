# Software Advanced

This is the **advanced** section of documentation we created for the [EDP IoT Hackathon](http://edpiothackathon.edp.pt).

Our goal here is to dive into more details in key Azure IoT scenarios and some additional Azure services that may become handy. 

- [Software Advanced](software-advanced.md)
  * [Azure IoT Scenarios](software-advanced.md#azure-iot-scenarios)
    * [Remote Monitoring](software-advanced.md#remote-monitoring)
    * [Predictive Maintenance](software-advanced.md#predictive-maintenance)
  * [Data Visualization](software-advanced.md#data-visualization)
  * [Other Azure Services](software-advanced.md#other-azure-services)
    * [Logic Apps](software-advanced.md#logic-apps)
    * [Azure Functions](software-advanced.md#azure-functions)
    * [Notification Hub](software-advanced.md#notification-hub)

### [Azure IoT Scenarios](#azure-iot-scenarios)

In the EDP IoT Hackathon, you'll need to implement an Azure-based IoT solution. In the IoT community several projects have already been made available in the Internet. This projects, aligned with the current needs of enterprises, have identified some scenarios that have become common. Let's understand them:

#### [Remote Monitoring](#remote-monitoring)

The remote monitoring scenario illustrates a solution where you can perform end-to-end monitoring. It brings together key Azure IoT services to enable the following features: **data ingestion**, **device identity**, **command and control**, **rules** and **actions**.

To exemplify this features, Microsoft created the **[Azure IoT Suite](https://www.azureiotsuite.com)** packaging multiple Azure services with custom extensions as preconfigured solutions : on of this preconfigured solutions is Remote Monitoring. It's a base implementations of common IoT solution patterns a examples or templates. The end goal is:

- as a starting point for your own IoT solution.
- to learn about the most common patterns in IoT solution design and development.
- Each preconfigured solution implements a common IoT scenario and is a complete, end-to-end implementation. You can deploy the Azure IoT Suite remote monitoring preconfigured solution from [https://www.azureiotsuite.com](https://www.azureiotsuite.com). In addition, you can download the complete source code from this repository to customize and extend the solution to meet your specific requirements.

Particularly to the Remote Monitoring scenario, take a look at this articles:
- [Azure IoT Remote Monitoring preconfigured solution (GitHub repo)](https://github.com/Azure/azure-iot-remote-monitoring)
- [Azure IoT Remote monitoring preconfigured solution walkthrough](https://docs.microsoft.com/en-us/azure/iot-suite/iot-suite-remote-monitoring-sample-walkthrough)

#### [Predictive Maintenance](#predictive-maintenance)

The predictive maintenance is usually related to anomaly detection scenarios. With the recent developments in Artificial Intelligence, the IoT scenarios have been complemented towards predictive maintenance integrating real-time device telemetry with predictive models, for instance created using Azure Machine Learning.

Again, within the **[Azure IoT Suite](https://www.azureiotsuite.com)**, you can easily connect to and monitor devices, and analyze data in real time. The predictive maintenance preconfigured solution takes the data and uses rich dashboards and visualizations. The end goal is to demonstrate how enterprises can bring new intelligence driving efficiencies and enhance revenue streams. 

Particularly to the Remote Monitoring scenario, take a look at this articles:
- [Azure IoT Predictive maintenance preconfigured solution (GitHub repo)](https://github.com/Azure/azure-iot-predictive-maintenance)
- [Azure IoT Predictive maintenance preconfigured solution overview](https://docs.microsoft.com/en-us/azure/iot-suite/iot-suite-predictive-overview)

### [Data Visualization](#data-visualization)

Most technical solutions will include a visualization layer. IoT solutions are usually not an exception, and most of the times are close coupled to data visualization techniques and technologies.

IoT solutions user experience (UX) typically includes a website, but can also include web services and APIs with a graphical user interface in the form of a mobile or desktop app. It usually implements access to and visualization of device data and analysis results, discovery of devices through the registry, command and control capabilities, and the workflows of the provisioning. In many cases, end users will be notified of alerts, alarm conditions, or necessary actions that need to be taken through push notifications. 

The solution UX can also provide or integrate with live and interactive dashboards, which are a suitable form of visualizations for IoT scenarios with large population of devices. 
IoT solutions often include geo-location and geo-aware services and the UI will need to provide appropriate controls and capabilities. 

There are several technology options to implement Data Visualization. For instance, **Azure App Service** is a managed platform with powerful capabilities for building web and mobile apps for many platforms and mobile devices. Web Apps and Mobile Apps allow developers to build web and mobile apps using languages like .NET, Java, NodeJS, PHP, or Python. 
In addition, **Azure API Apps** allows easy exposure and management of APIs, which can be accessed by mobile or web clients. 

**Azure Notification Hubs** enables sending of push notifications to personal mobile devices (that is, smartphones and tablets). It supports iOS, Android, Windows, and Kindle platforms, while abstracting the details of the different platform notification systems (PNS). With a single API call, a notification can target an individual user or an audience segment with a large number of users. 

In IoT, dashboards become important as it provides a natural way for aggregated views and help visualize a vast number of devices. **Power BI** can be a great accelerator, as it includes rich, interactive and real time features.

Another suitable technology for IoT visualizations is **Bing Maps**. It includes map controls and services that you can use to incorporate Bing Maps in applications and websites. In addition to interactive and static maps, the APIs provide access to geospatial features such as geocoding, route and traffic data, and spatial data sources that you can use to store and query data that has a spatial component, such as device locations. 

Of course, there is a range of other technologies that can be used within Azure. There are a lot of open-source technologies that can easily be implemented on Azure, even if it only supports non-Microsoft operating system (Ex: Linux). 

### [Other Azure Services](#other-azure-services)

There are a lot of services in Azure, that will help you implement several scenarios. Depending on the requisites and goals of your solution, this services can guarantee a specific workflow or integrate with other services.
For the challenge presented in EDP IoT Hackathon, we specially recommend reading about the following services:

#### [Logic Apps](#logic-apps) 

Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud. It's a service that my help you integrate your IoT solution with other components.

**Logic apps** provides a visual designer to model and automate your process as a series of steps known as a workflow. There are many connectors across the cloud and on-premises to quickly integrate across services and protocols. 

The advantages of using Logic Apps include the following:

- Saving time by designing complex processes using easy to understand design tools
- Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code
- Getting started quickly from templates
- Customizing your logic app with your own custom APIs, code, and actions
- Connect and synchronize disparate systems across on-premises and the cloud

Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management. Logic Apps will scale up automatically to meet demand.

Here we leave you with some scenarios where Logic Apps can be used:
- [Logic Apps Examples and Common Scenarios](https://docs.microsoft.com/en-us/azure/app-service-logic/app-service-logic-examples-and-scenarios)
- [Create a new logic app connecting SaaS services](https://docs.microsoft.com/en-us/azure/app-service-logic/app-service-logic-create-a-logic-app)

#### [Azure Functions](#azure-functions)  

Azure Functions is a solution for easily running small pieces of code, or "functions," in the cloud. You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it. Functions can make development very productive, and you can use your development language of choice, such as C#, F#, Node.js, Python or PHP - it even supports NuGet and NPM, so you can use your favorite libraries.

**Azure Functions** becomes very handy to process data, integrate systems, work with the internet-of-things (IoT), or build simple APIs/microservices. Consider Functions for tasks like image or order processing, file maintenance, long-running tasks that you want to run in a background thread, or for any tasks that you want to run on a schedule.

Functions provides templates to get you started with key scenarios::

|||
|----|-----|
| **BlobTrigger** | Process Azure Storage blobs when they are added to containers. You might use this function for image resizing.|
| **EventHubTrigger** | Respond to events delivered to an Azure Event Hub. Particularly useful in application instrumentation, user experience or workflow processing, and Internet of Things (IoT) scenarios.|
| **Generic webhook** | Process webhook HTTP requests from any service that supports webhooks. |
| **GitHub webhook** | Respond to events that occur in your GitHub repositories.|
| **HTTPTrigger** | Trigger the execution of your code by using an HTTP request.|
| **QueueTrigger** | Respond to messages as they arrive in an Azure Storage queue.|
| **ServiceBusQueueTrigger** | Connect your code to other Azure services or on-premise services by listening to message queues.|
| **ServiceBusTopicTrigger** | Connect your code to other Azure services or on-premise services by subscribing to topics.|
| **TimerTrigger** | Execute cleanup or other batch tasks on a predefined schedule.|

As you can see, Azure Functions **integrates** with various Azure and other services. These services can trigger your function and start execution, or they can serve as input and output for your code. You can easily create triggers from 
**Azure DocumentDB**, **Azure Event Hubs**, **Azure Mobile Apps (tables)**, **Azure Notification Hubs**, **Azure Service Bus (queues and topics)**, **Azure Storage (blob, queues, and tables)**, **GitHub (webhooks)** or **On-premises (using Service Bus)**.

If you are looking for more technical information about Functions, see the [Azure Functions Developer Reference](https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference).


#### [Notification Hubs](#notification-hub)  

**Notification Hubs** is a scalable, push notification engine for quickly sending millions of messages. It provide an easy-to-use, multiplatform, scaled-out push infrastructure that enables you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.

With Notification Hubs, you can easily send cross-platform, personalized push notifications, abstracting the details of the different platform notification systems (PNS). With a single API call, you can target individual users or entire audience segments containing millions of users, across all their devices.

You can use Notification Hubs for both enterprise and consumer scenarios. For example:

- Send breaking news notifications to millions with low latency.
- Send location-based coupons to user segments.
- Send event notifications to users or groups for sports/finance/games applications.
- Notify users of enterprise events like new messages/emails, and sales leads.
- Send one-time-passwords required for multi-factor authentication.

Nowadays, in most IoT solutions, besides the typical data visualization needs, usually it may be important to create user awareness on-demand. Using notifications to reach users on the mobile phone, became an important channel. In IoT solutions you can detect specific scenarios and warn your users. The scenarios detection will depend on data (as discussed above), but notifying users will rely in services like Notification Hubs.

For developers, creating push notifications became simple independently of your users' mobile platform. Here we'll leave some tutorials on how to use Notifications Hubs to send notifications to most common platforms:

- [Getting started with Notification Hubs for Windows Universal Platform Apps](https://docs.microsoft.com/en-us/azure/notification-hubs/notification-hubs-windows-store-dotnet-get-started-wns-push-notification);
- [Get started with Notification Hubs with Xamarin for Android](https://docs.microsoft.com/en-us/azure/notification-hubs/xamarin-notification-hubs-push-notifications-android-gcm);
- [iOS Push Notifications with Notification Hubs for Xamarin apps](https://docs.microsoft.com/en-us/azure/notification-hubs/xamarin-notification-hubs-ios-push-notification-apns-get-started);
- [Sending push notifications to Android with Azure Notification Hubs](https://docs.microsoft.com/en-us/azure/notification-hubs/notification-hubs-android-push-notification-google-fcm-get-started);
- [Sending push notifications to iOS with Azure Notification Hubs](https://docs.microsoft.com/en-us/azure/notification-hubs/notification-hubs-ios-apple-push-notification-apns-get-started);

---

[Go Back](/Documentation/readme.md)
