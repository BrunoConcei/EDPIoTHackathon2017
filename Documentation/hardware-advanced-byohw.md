# **Build Your Own Hardware**



## **Getting Started**

If you wish, you can build your own hardware to send data from the EB to the [Azure Cloud](sofware-beginner-azureiot.md). It's up to you to decide which case suits your team best.

Be aware that, in order to connect your own piece of hardware to the EB you should always comply with all the rules of the challenge as well as the main generic goals of the EDP IoT Hackathon.

Be creative, you can have your own shield in the Akeru board or instead a Sigfox's enabled board with the provided circuit.

**Note**: If you wish to use your own Sigfox's enabled device please contact us as soon as possible via [EDP STARTER's email](edpstarter@edp.pt)

All libraries in this [documentation](hardware-intermediate-eb-comm.md) serve as a reference but you can always use others if you think they're more suitable or have a better performance.

**Remember:**

**1 - You only have 2 weeks to hack the EB and present your final idea.**

**2 - All extra effort, creative thinking and new working solutions to this documentation we'll be rewarded in the end.**


**NOTE:** We will only accept boards that can send all data coming from the EBs through the [Sigfox IoT techonology](software-beginner-sigfox.md). 

## **Warning**: Any other type of communication will not be considered for the EDP IoT Hackathon 2017.

## **Generic Goals**
###  **Hardware**

In the hardware part of the challenge, teams will be asked to:
* Connect to the EBs via HAN (Home Area Network) interface 
* Feed the circuit and the board through the HAN Interface (+5 VDC & GND pins). You should also be capable to do it via USB for debbugging proposes
* Communicate and comply with the [Sigfox backend](https://backend.sigfox.com/welcome/news)

### **Software**

In the software part of the challenge, teams will be asked to send data to [Microsoft Azure](software-begginer-azureiot.md) 
via [Sigfox IoT Communication Protocol](software-beginner-sigfox.md) such as:
* Load profile data (15min period)
* Live values (Active Power, Reactive Power, Current, Tension, ... ) 

Don't forget [Sigfox IoT techonology's](software-beginner-sigfox.md) limitations when sending Load Profile Data:

* 12 bytes payload hard limit 
* 140 msgs/day protocol soft limit

## **Additional Information**

**1.** Your final design must be able to work solely via EB connection (+5 Vdc). We recommend to first test your solution ONLY via PC power feeding and then include the EB (+5 Vdc) part

**2.** If you plan to use another device to hack the EB take a look at [Sigfox's website](https://partners.sigfox.com/products/kit). We recommend the [Akene shield](http://snootlab.com/lang-en/snootlab-shields/889-akene-v1-en.html).

**3.** Feel free to contact any mentor during the EDP IoT Hackathon 2017 if you still have any question. We will try to answer you back as fast as possible.

**4.** During the EDP IoT Hackathon 2017, EDP Starter HQ is open during weekdays to every team. You'll have 10 EDP Boxes available to test and work on your design.

---

[Go Back](hardware-advanced.md)