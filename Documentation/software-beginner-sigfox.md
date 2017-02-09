# [Understanding SIGFOX](#understanding-sigfox) #


![SIGFOX Logo](../images/sigfox-logo.png "SIGFOX Logo")

## What is SIGFOX? ##

[SIGFOX](www.sigfox.com), is a French company that builds wireless networks to connect low-energy objects such as electricity meters, smartwatches, and washing machines, which need to be continuously on and emitting small amounts of data. Its technology is aimed at the Internet of Things (IoT). The company’s network complements existing high-bandwidth systems by providing economical, energy-efficient two-way transmission of small quantities of data over long distances, thus lowering barriers to wide implementation of IoT and M2M solutions, and greatly extending the battery and service life of connected devices. 

SIGFOX deploys Low-Power Wide Area Networks (LPWAN) that work in concert with hardware that manufacturers can integrate into their products. In terms of compatibility, the network takes a similar approach to traditional GSM networks. Any device with integrated SIGFOX hardware can connect to the internet – in regions where a SIGFOX network has been deployed – without any external hardware, like a Wi-Fi or Zigbee router. But, in another sense, the SIGFOX network is entirely different than traditional GSM networks, in that it can only transmit small amounts of data.

The main factor that led to the choice of SIGFOX is related to the low energy consumption and the reliability of communication. Here is a summary of the technology:

| SIGFOX Radio Technology ||
|----------------------------|-----------------|
| Purpose | Specially conceived for M2M/IoT.|
| Identity | Each device has a unique ID (NOT an IP); |
| Ultra Narrow Band | Energy-efficient; Resistant to jamming; |
| Spectrum | ISM free-to-use (ETSI 300-220); Forces 1% duty cycle; Base stations MUST comply as well;
| Frequency | 868 MHz (Europe); 902 MHz (USA); |
| Long Range & Protocols | 2-way communication with 162 dB path loss; |
| Customer Payload | 12 byte messages with a MAXIMUM of 140 message per day in Europe (ETSI 300-220).|

| SIGFOX Radio Technology |
|----------------------------|
| Global, operates a cellular network dedicated to IoT |
| Invented a radio protocol |
| NOT selling hardware |
| NOT building connected solutions |
| Each device has a unique ID (NOT an IP) |
| OUT OF THE BOX: No pairing, no signalisation and no configuration needed |
| OUT OF THE BOX: “Power ON and send message” phylosophy |
| OUT OF THE BOX: Specially conceived for M2M/IoT |

### Messages ###
- Device decides that it wants an update;
- **SMALL messages**
- **12 bytes means NO MEDIA (JPEG, JSON/XML…)**
- **12 bytes = 96 bits MAX;**
- Low bandwidth = 100 bits/s
- Examples:
  - Temperature  = 2 bytes;
  - GPS = 6 bytes;
  - State Report = 1 byte;
  - Heartbeat/Update = 0 bytes.

### Regulation ###
- 140 msgs/day is NOT a technology limit;
- Compliant with the European regulation (ETSI 300-220);
- 1 % Duty Cycle.
- Ultra Narrow Band
- 200KHz part of the spectrum;
- Each message is 100Hz wide;
- Right NOW can handle 500 msgs/s;
- Roaming is included.

### Security ###
- Each message has a unique key to the device;
- Message can be encrypted or scrambled (up to the user);
- No keys exchanged over the network;
- Servers are managed by SIGFOX (2 datacenters in France);
- HASH key for each message is calculated & sent using:
- Device ID;
- Secret Key;
- Payload; (not encrypted by default);
- Internal Increment.

For more information go to:

1. [http://www.sigfox.com/en/#!/technology](http://www.sigfox.com/en/#!/technology) (Info page)
2. [http://www.sigfox.com/static/media/Files/Documentation/SIGFOX_Whitepaper.pdf](http://www.sigfox.com/static/media/Files/Documentation/SIGFOX_Whitepaper.pdf)  (White paper)
3. [https://github.com/sigfox/makers-tour-resources](https://github.com/sigfox/makers-tour-resources)  (Workshop examples)
4. [http://www.microwave-rf.com/docs/WaveRF-2014-SIGFOX.pdf](http://www.microwave-rf.com/docs/WaveRF-2014-SIGFOX.pdf)  (more info on UNB technology)

---

Now you have good informationto start with. Let's jump over the intermediate documentation : [Software Intermediate](software-intermediate.md)

Still focused on SIGFOX? Jump directly to SIGFOX's intermediate documentation : [SIGFOX and Callbacks](software-intermediate-sigfox.md).

[Go Back](software-beginner.md)

