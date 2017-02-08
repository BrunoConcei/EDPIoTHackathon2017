# [Continuing with Azure IoT](#continueing-with-azure-iot)


Knowing the basic services on Azure to support your IoT solution, is a good starting point. However, let's structure our ideas a understand how services may be combined to achieve our goals.

Microsoft has created the **[Microsoft Azure IoT reference architecture](http://download.microsoft.com/download/A/4/D/A4DAD253-BC21-41D3-B9D9-87D2AE6F0719/Microsoft_Azure_IoT_Reference_Architecture.pdf)** providing guidance for building secure and scalable, device-centric solutions for connecting devices, conducting analysis, and integrating with backend systems. The concepts of this architecture are also generally applicable to private cloud implementations, at lower scale and with increased deployment and management efforts. 

The goal of this architecture is to enable the flow of information between intermittent or continuously connected devices and line-of-business assets (that is, not general-purpose devices such as personal PCs, smartphones, or tablets) and cloudbased backend systems for the purpose of analysis, control, and business process integration. The solution architecture is specifically designed for large-scale IoT environments with devices from industrial serial production with tens of thousands of units, and/or industrial machinery emitting significant amounts of data. The model is suitable for so-called “maker” and hobbyist scenarios where small numbers of special-built devices are operated, but may be costlier than a solution equivalent to running a single website. 

The architecture aims to be neutral with regard to particular industries and use-case scenarios and also neutral toward particular approaches for modeling state, metadata, and behavior of devices. However, while the architecture is abstract, the assumption is that realizations of the architecture in particular solutions will be very concrete and aligned with particular industry standards or domain specific designs.  

The reference architecture provides flexibility for composability and extensibility to allow for a variety of technology choices driven by the specific solution requirements. The document first introduces foundational principles for the architecture, then presents the conceptual model and components of the architecture, which can be implemented using Azure or third-party services. The remaining sections provide more details about the individual components, design considerations, and technology trade-offs. 

The following pictureshows the high-level conceptual architecture. The architecture is composed of core platform services and application-level components to facilitate the processing needs across three major areas of a typical IoT solution: 
- Device connectivity
- Data processing, analytics, and management
- Presentation and business connectivity

![Microsot IoT Reference Architecture](/images/iot-reference-architecture.png)

This is a conceptual architecture that helps you to start idealizing your architecture.

Has you've probably understood, ingesting data from devices to cloud is a key part in any IoT solution. This being said, let's continue to dive into Azure IoT Hub.

## Azure IoT Hub
 
In addition to a rich set of device-to-cloud and cloud-to-device communication options, including messaging, file transfers, and request-reply methods, Azure IoT Hub addresses the device-connectivity challenges in the following ways:

| Feature | Description |
|---------|-------------|
| **Device twins** | Using Device twins, you can store, synchronize, and query device metadata and state information. Device twins are JSON documents that store device state information (metadata, configurations, and conditions). IoT Hub persists a device twin for each device that you connect to IoT Hub. |
| **Per-device authentication and secure connectivity** | You can provision each device with its own security key to enable it to connect to IoT Hub. The IoT Hub identity registry stores device identities and keys in a solution. A solution back end can add individual devices to allow or deny lists to enable complete control over device access. |
| **Route device-to-cloud messages to Azure services based on declarative rules** | IoT Hub enables you to define message routes based on message rules to control where your hub sends device-to-cloud messages. Message rules do not require you to write any code, and can take the place of custom post-ingestion message dispatchers. |
|**Monitoring of device connectivity operations** | You can receive detailed operation logs about device identity management operations and device connectivity events. This monitoring capability enables your IoT solution to identify connectivity issues, such as devices that try to connect with wrong credentials, send messages too frequently, or reject all cloud-to-device messages.|
|**An extensive set of device libraries**| Azure IoT device SDKs are available and supported for various languages and platforms--C for many Linux distributions, Windows, and real-time operating systems. Azure IoT device SDKs also support managed languages, such as C#, Java, and JavaScript. |
|**IoT protocols and extensibility**| If your solution cannot use the device libraries, IoT Hub exposes a public protocol that enables devices to natively use the MQTT v3.1.1, HTTP 1.1, or AMQP 1.0 protocols. You can also extend IoT Hub to provide support for custom protocols: Creating a field gateway with the Azure IoT Gateway SDK that converts your custom protocol to one of the three protocols understood by IoT Hub; Customizing the Azure IoT protocol gateway, an open source component that runs in the cloud.
| **Scale** | Azure IoT Hub scales to millions of simultaneously connected devices and millions of events per second.|

For more information check the respective documentation:
- [Azure IoT Developer Center](https://azure.microsoft.com/en-us/develop/iot/);
- [Process IoT Hub device-to-cloud messages using routes (.NET)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-csharp-process-d2c);
- [Get started with device twins (​.NET/Node)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-node-twin-getstarted);
- [How to use twin properties (​.NET/Node)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-node-twin-how-to-configure);
- [Schedule and broadcast jobs for ​.NET/Node](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-node-schedule-jobs)

###Azure IoT Hub Config

Now that you know what Azure IOT Hub can do, let's do a quick overiew on how to setup an Azure IoT Hub. 

####Create an IoT hub
Create an IoT hub for your simulated device app to connect to. The following steps show you how to complete this task by using the Azure portal.

1. Sign in to the Azure portal.
2. In the Jumpbar, click New > Internet of Things > IoT Hub.

 ![Create Azure IoT Hub](/images/azureiot-create-new.png)
3. In the IoT hub blade, choose the configuration for your IoT hub.

    ![Configure Azure IoT Hub](/images/azureiot-create-config.png)

   * In the Name box, enter a name for your IoT hub. If the Name is valid and available, a green check mark appears in the Name box.
   * Select a [pricing and scale tier](https://azure.microsoft.com/pricing/details/iot-hub/). Uou can use the free F1 tier.
   * In Resource group, either create a resource group, or select an existing one. For more information, see [Using resource groups to manage your Azure resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-portal).
   * In Location, select the location to host your IoT hub. For this tutorial, choose your nearest location.
4. When you have chosen your IoT hub configuration options, click **Create**.  It can take a few minutes for Azure to create your IoT hub. To check the status, you can monitor the progress on the Startboard or in the Notifications panel.

 ![Azure IoT Hub creation](/images/azureiot-create-confirm.png)  
5. When the IoT hub has been created successfully, click the new tile for your IoT hub in the Azure portal to open the blade for the new IoT hub. Make a note of the Hostname, and then click Shared access policies.

 ![Shared Access Policies in Azure IoT Hub](/images/azureiot-create-policies.png)
6. In the Shared access policies blade, click the iothubowner policy, and then copy and make note of the IoT Hub connection string in the iothubowner blade. For more information, see [Access control](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-security) in the "IoT Hub developer guide."

 ![Get Azure IoT Hub's connections string](/images/azureiot-create-connection.png)

You have now created your IoT hub! To send data from devices to your IoT Hub service, you'll first have to create a device identity:

####Device identity

Azure IoT Hub only allows connections from known devices that present proper credentials. You can do it programmatically using the SDK, use the DeviceExplorer utility (Windows only) or the iothub-explorer command line interface to provision a device for use in Azure IoT Hub. 

You have a pre-built version of the **Device Explorer** application for Windows can be downloaded by clicking on this link: [Downloads](https://github.com/Azure/azure-iot-sdks/releases) (Scroll down for SetupDeviceExplorer.msi). The default installation directory for this application is "C:\Program Files (x86)\Microsoft\DeviceExplorer". You might want to pin the DeviceExplorer.exe application to the taskbar for easier access.
When you run the utility you need to input the iothubowner connection string in the IoT Hub Connection String field found in the Configuration tab.

If you are on a non-Windows machine, or prefer to use a command line interface instead of the DeviceExplorer utility, you can install the **iothub-explorer command line interface**. The iothub-explorer tool enables you to provision devices in your IoT hub. It runs on any computer where Node.js is available.

On Windows, open the Node.js command prompt and type the following:

```
npm install -g iothub-explorer
npm update -g iothub-explorer
```

On Mac OS X open Terminal and type the following:

```
npm install -g iothub-explorer
npm update -g iothub-explorer
```

####Create a New Azure IoT Device
If you are using the DeviceExplorer simply open the Management tab and click the Create button. In the dialog that opens, enter the name of your device - something like *MyEDPIoTDevice* works well. Then Click the Create button, and click Done on the confirmation dialog that opens.

![Create a device with Device Explorer](/images/azureiot-deviceexp-create.png)

You will see your device in the Devices list. Once a device is created, you can get the device-specific connection string by selecting it in the Devices list, right-clicking and selecting Copy connection string for selected device:

![Device list in Device Explorer](/images/azureiot-deviceexp-devicelist.png)

If you are on a non-Windows machine, or prefer to use a command line interface instead of the DeviceExplorer utility, you can provision a new Azure IoT Hub device using the **iothub-explorer command line interface**.

Using the Node.js command prompt or Terminal, execute the following commands (you may need to wrap the connections string in quotes, depending on the terminal application you are using). You may replace *MyEDPIoTDevice* with any name you’d like:

```
iothub-explorer login [YOUR IOT HUB CONNECTION STRING] 
iothub-explorer create MyEDPIoTDevice --connection-string
```

Once a device is created, the device information, including the device-specific connection string will be displayed.

![Create a device with iothub-explorer command line interface](/images/azureiot-iothubexp-create.png)

The device-specific connection string identifies the device by name and includes a key that is only for that device.

Congratulations! You have created an Azure IoT Hub and a representation of a physical device. As most of Microsoft Azure service, you can pick your any kind of language to implement your solution. Check this documentation:

- [Get started with Azure IoT Hub (.NET)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-csharp-getstarted);
- [Get started with Azure IoT Hub (Node)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-node-node-getstarted);
- [Get started with Azure IoT Hub (Java)](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-java-java-getstarted);

---

[Go Back](software-intermediate.md)

