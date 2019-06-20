# Intern_documentation
This Readme file describes interfacing RF 433MHz, NRF_24, MQ-7 sensor with Arduino module. This file also has observations that were made after interfacing the above with Arduino. 


## Firstly, To interface RF 433 MHz with Arduino, the connections were made as mentioned below-
### RF 433MHz-Arduino wiring
#### For Transmitter
| Transmitter | Arduino |
| :---------: | :------:|
| VCC | 5V |
| GND | GND |
|Data | 12 |
#### For Reciever
|Reciever| Arduino|
| :----: | :-----:|
|VCC|5V|
|GND|GND|
|DATA|11|


The code to be uploaded on Arduino with transmitter and Reciever respectively has been attached in this [RF_433MHz](https://github.com/avianshgaur/Intern_documentation/tree/master/RF_433Hz) folder.


**NOTES:**
* While working with RF 5V without antenna, it gave a range of about 15m in the line of sight.
* Range can be increased by adding antenna to the Transmitter and Reciever.
* [RadioHead](http://www.airspayce.com/mikem/arduino/RadioHead/RadioHead-1.46.zip) library has to be installed before uploading the code.

**Specification of RF_433MHz Transmitter**
* Frequency Range: 433.92 MHz
* Input Voltage: 5V

**Specifications RF 433MHz Transmitter**
* Frequency Range: 433.92MHz
* Input Voltage: 3-12V

## To Interface nRF24L01 – 2.4GHz RF Transceiver Module With Arduin
**Specifications nRF24L01 – 2.4GHz RF Transceiver**
* Input Voltage: 3.3V
* Range with Antenna: 250Kb rate (Open area) >1000 meter.

[RadioHead](http://www.airspayce.com/mikem/arduino/RadioHead/RadioHead-1.46.zip) library has to be download before uploading the code.


[nRF24L01](https://github.com/avianshgaur/Intern_documentation/tree/master/nRF24L01) has the code that has to be uploaded in Arduino.

**Following is the circuit diagram for the client and server respectively**
* [Client](https://github.com/avianshgaur/Intern_documentation/blob/master/png_nRF24/Client.png)
* [Server](https://github.com/avianshgaur/Intern_documentation/blob/master/png_nRF24/Server.png)

**Notes**
* Important: Input voltage is of 1.9V~3.6V, do not exceed this voltage, otherwise it will fry your module. 
* When testing without antenna,the tranceiver module was transmitting upto range of 50-60 metres in the line of sight.
* Range can be increased with adding an antenna to both the modules.

## To interface the MQ-7 SENSOR to Arduino##
 **Notes:**
* Make sure that the capacitors are ceramic(I took the capacitors of the value of 1uF).
* The connections of MQ-7 sensors were removed as shown in this [image]() to get the satisfactory results.
* The voltages were varying from 4.3 V to 2.1 V due to the drop of 0.7V in the transistor. But Voltage has to vary from 1.4V to 5V according to [Datasheet]() of the MQ-7. This will result in insignificant error which can be ignored(The lower voltage can be brought down to ~ 1.7V from 2.1V by changing 3.6 V in [code]() to nearly 4.7).
* MQ-7 sensor has to be calibrated by changing the "sensor_reading_clean_air" value in the code. Each sensor has to be calibrated individually. The value of "sensor_reading_clean_air" will change with different MQ-7 sensor.
* Do not connect MQ-7 directly with Arduino module it may damage the Arduino module. This is because the arduino can supply current upto 40mA and MQ-7 requires current upto 150 mA.
 

The link:
https://www.instructables.com/id/Arduino-CO-Monitor-Using-MQ-7-Sensor/
The co_monitor code has been attached already.
