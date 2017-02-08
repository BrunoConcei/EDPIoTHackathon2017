# [SIGFOX and callbacks](#sigfox-and-callbacks)


### SIGFOX Cloud

SIGFOX provides ways to integrate with application systems through custom callbacks. Callbacks are a service that allows SIGFOX to push an event to your server upon an event. For example, a device might send a SIGFOX message upon an external trigger; get notified once the event had occurred. This would be the ideal case to use a Callback; the SIGFOX service can relay the messages via a POST/GET requests to a specific location (service, app or server). In addition to defining your own server and data, SIGFOX also allows you to transfer your data to the cloud services like Microsoft Azure or AWS.

[SIGFOX Cloud](https://backend.sigfox.com) is the cloud service that offers a backend for your system integration. Let's learn about this service and configure callbacks to your application servers. 


### SIGFOX Callbacks

SIGFOX offers a callback service. You can configure integration for every SIGFOX message with Microsoft Azure Platform. Namely, there are specific connectors for Event hub and IoT hub. It's also possible to create a custom Callback allowing to integrate with your own server. This is the "default" callback type. You can create a full custom request (http method, content type, headers, etc).

All devices are registered in SIGFOX network. Through the SIGFOX Cloud you can list and access the details for every registered device.

![SigFox Registered Devices](/images/sigfox.devicetype.png)

In the Device Type details page, you will find the option to configure Callbacks.   

![SigFox Device Details](/images/sigfox.devicetypeDetails.png)

Create a New Callback, and select IoT Hub connector. SIGFOX and Microsoft, have a easy way to establish this communication, bringing your devices closer to the cloud.

![SigFox Callbacks IoTHub](/images/sigfox.callbacks.IotHub.png)

Configure the callback by specifing your custom paylod format, the connection string to IoT Hub, and the syntax of the JSON body within the messages.

![SigFox Callback Creation](/images/sigfox.CallbackCreation.png)

Every time a message is received by the network, you can set up the way you want it to be forwarded to your application server.You can configure your URL, content-type, request body, etc…

The connection string for IoT Hub, you may collect it from [portal.azure.com](http://portal.azure.com).

![SigFox Azure](/images/sigfox.Azure.png)

For more information go to:

1. [https://backend.sigfox.com/apidocs/event-callback?configSource=3](https://backend.sigfox.com/apidocs/event-callback?configSource=3)
4. [http://sigfox.cloud.answerhub.com/index.html](http://sigfox.cloud.answerhub.com/index.html)  (Forum)
5. [https://backend.sigfox.com/apidocs/callback](https://backend.sigfox.com/apidocs/callback)  (Callback API doc)

#### SIGFOX Callback configuration

The configuration was quite simple, focusing on the following items:

- custom payload config: This field allows you to specify how you would like SIGFOX to decode the payload of your device. You may, for example, want to decode an input byte as an unsigned integer. The configuration in this case was:

```
temp::uint:8 humidity::uint:8 lum::uint:8 voltage::uint:16
```

- Connection string: The Azure IoT Hub access configuration (see below). In idio it is possible to evaluate the structure of * connection string * that identifies which instance of IoT HUb, also providing the respective security configurations.

```
HostName=xxx.azure-devices.net;SharedAccessKeyName=xxxx;SharedAccessKey=xxxxxxxxxxxxxxxxxxxxxxxxxx
```

- JSON Body: This is the main content of your message. You can specify any custom data you want to configure within the payload. It is also possible to use variables available for any message. For example:

```json
{
"device" : "{device}",
"data" : "{data}",
"temp" : {customData#temp},
"hum": {customData#humidity},
"voltage": {customData#voltage}
}
```

This way you'll be able to integrate the devices through SIGFOX communication with a cloud-based backend, namely Microsoft Azure. 

---

[Go Back](software-intermediate.md)

