# **Registers**



## **Registers Introduction**

The information available through the EB's HAN interface is described in the following tables of this subsection.
All registers have a specific address and an associated index that should be used as reference to the access profile.

The correspondent type of data, unit and scaler are also defined. 

The scaler is related to the resolution of the received data, i.e., to determine how many decimal digits should be considered.


Below you will find a list of every data you can extract from the EBs and the respective register's index.

For example, to extract the **Active energy import (+A)** the appropriate **index** should point to the decimal number **22** (0x0016 in hexadecimal)

For the **Clock data type** we have a special structure:


| Description | Bytes | Types | Expected Values|
|-------------|-------|-------|----------------|
| Year| 2| Clock|Long unsigned|2000 to 2099|
| Day of Month| 1| Unsigned|1 to 31|
| Weekday| 1| Unsigned| 1 - Monday to 7 - Sunday|
| Hour| 1| Unsigned|0 to 23|
| Minute| 1| Unsigned|0 to 59|
| Second| 1| Unsigned|0 to 59|
| Hundredths of second| 1| Unsigned|0 to 59|
| Deviation (from local to GMT)| 1| Long|-720 to 720 minutes|
| Clock Status| 1| Unsigned|0x00 - Winter; 0x80 - Summer|

## **Data Tables**

### **1.** **General Information**

| Index | Description | Type | Unit| Scaler |
|----------|----------|------|-----|--------|
| 1| Clock| Clock|-|-|
| 2| Device ID 1 -Device Serial Number| Octet string [10]|-|-|
| 3| Device ID 2 -Manufacturer Model Codes & Year| Octet string [6]|-|-|
| 4| Active core firmware Id.| Octet string [5]|-|-|
| 5| Active app firmware Id.| Octet string [5]|-|-|
| 6| Active com firmware Id.| Octet string [5]|-|-|
| 7| HAN interface - Modbus address| Unsigned|-|-|
| 8| HAN interface - Access profile| Bit string [256]|-|-|
| 9| Status control| Octet string|-|-|


### **2.** **Total Registers**

| Index | Description | Type | Unit| Scaler |
|----------|----------|------|-----|--------|
| 22| Active energy import (+A)| Double long unsigned|Wh|0|
| 23| Active energy export (-A)| Double long unsigned|Wh|0|
| 24| Reactive energy QI (+Ri)| Double long unsigned|VArh|0|
| 25| Reactive energy QII (+Rc)| Double long unsigned|VArh|0|
| 26| Reactive energy QIII (-Ri)| Double long unsigned|VArh|0|
| 27| Reactive energy QIV (+Rc)| Double long unsigned|VArh|0|

### **3.** **Instantaneous Values**

| Index | Description | Type | Unit| Scaler |
|----------|----------|------|-----|--------|
| 108| Instantaneous Voltage L1|  Long unsigned|V|-1|
| 109| Instantaneous Current L1|  Long unsigned|A|-1|
| 121| Instantaneous Active power + (Sum of all phases)| Double long unsigned|W|0|
| 122| Instantaneous Active power - (Sum of all phases)| Double long unsigned|W|0|
| 123| Instantaneous Power factor| Long unsigned|-|-3|
| 127| Instantaneous Frequency | Long unsigned|Hz|-1|


### **4.** **Tariff Registers**

 - Values from Active Damand Control Threshold Tariff 1-6 should be the same (10350 VA)

 - T1 is "Vazio", T2 is "Ponta" and T3 is "Cheias"

**T4 to T6 are not used**

| Index | Description | Type | Unit| Scaler |
|----------|----------|------|-----|--------|
| 10| Activity Calendar - Active Name |Octet string|-|-|
| 11| Current active tariff |Unsigned|-|-|
| 12| Active demand control threshold T1 |Double Long Unsigned|VA|0|
| 13| Active demand control threshold T2 |Double Long Unsigned|VA|0|
| 14| Active demand control threshold T3 |Double Long Unsigned|VA|0|
| 15| Active demand control threshold T4 |Double Long Unsigned|VA|0|
| 16| Active demand control threshold T5 |Double Long Unsigned|VA|0|
| 17| Active demand control threshold T6 |Double Long Unsigned|VA|0|
| 38| Rate 1 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|
| 39| Rate 2 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|
| 40| Rate 3 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|
| 41| Rate 4 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|
| 42| Rate 5 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|
| 43| Rate 6 contract 1 active energy (+A) |Double Long Unsigned|Wh|0|


### **5.** **Disconnector**

The Disconnector Control State variable can be:

- 0 when disconnected;
- 1 when connected;
- 2 when ready for reconnection 

| Index | Description | Type | Unit| Scaler |
|----------|----------|------|-----|--------|
| 132| Disconnect Control State | Disconnect Control State |-|-|



**NOTE:** All indexes are decimal representations of hexadecimal values. If you use the **recommended libraries you only need to use the decimal values given above**.


## Example of the function for getting the Active Energy +A:

Using FCT_READSINGLEREGISTER

Active Energy (+A) is a 4 bytes - Double Long Unsigned - registry. 
This means that we will get our value in our dataArray[16] in the first two positions [0] and [1].

```C++
double EDPComm::getLiveTotalRegistriesValue(uint16_t dataArray[16])
{
	// Returns a live total value of 4 bytes (ex: A+_Total)
	double regValue_1half = dataArray[1];
	double regValue_2half = (dataArray[0])*0x10000; // 2 bytes can store (0x10000 - 1) numbers.
	return regValue_1half + regValue_2half; 
}
````

### **5. Load Profile**

A load profile is a graph of the variation in the electrical load (kWh) versus time. A load profile will vary according to customer type (typical examples include residential, commercial and industrial), temperature and holiday seasons. 

Power producers, like EDP, use this information to plan how much electricity they will need to make available at any given time.

Every EDP Box has a default **load profile** in its memory that gets updated every 15 minutes.


This load profile is synchronized with the time clock, i.e:

* 0:00 AM - 1st Load profile of the Day
* 0:15 AM - 2nd Load profile of the Day
* 0:30 AM - 3rd Load profile of the Day
* 0:45 AM - 4th Load profile of the Day
* 1:00 AM - 5th Load profile of the Day

The default data coming from the load profile array is as follows:

* **Year** (2 bytes)
* **Clock** (month, day of month, weekday, hour, minute, second, Hundredths of second and deviation) (7 bytes)
* **Clock - Clock Status and AMR profile status** (1 byte)
* **Active energy (+A) inc.** (4 bytes)

Using the given Modbus library this means that the dataArray with 16 positions (each with 2 bytes) will have the values in the following manner:
    - [0] Year 
    - [1] Month/ Day of Month
	- [2] Weekday/ Hour
	- [3] Hour/ minutes
	- [4] Seconds/ Hundreths of Second
	- [5] Deviation/ Clock Status
	- [6] AMR Status/ Active Energy +A
    - [7] Active Energy +A
	- [8] Active Energy +A/ {EMPTY}

Check the [source code](../src/EDPComm-Hackathon-2017/EDPComm.cpp) of the EDPComm library to know exactly how to get these values out of the dataArray. We have built specific functions to get all the elements of the Load Profile Data.


The [EDPComm](hardware-intermediate-eb-comm.md#edp-comm) library has specific functions to get the load profile from the EBs. 
You should analyze the code example very carefully as it has some differences for the **FCT_READSINGLEREGISTER** in terms of input parameters.

## **Advise:** You should carefully analyze the source code

---
Go to the [Hardware Advanced Documentation](hardware-advanced.md)


[Go Back](hardware-beginner.md)