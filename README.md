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
* While working with RF 5V without an antenna, it gave a range of about 15m in the line of sight.
* Range can be increased by adding an antenna to the Transmitter and Reciever.
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

### Client
![Client](https://github.com/avianshgaur/Intern_documentation/blob/master/png_nRF24/Client.png)

### Server
 ![Server](https://github.com/avianshgaur/Intern_documentation/blob/master/png_nRF24/Server.png)

**Notes**
* Important: Input voltage is of 1.9V~3.6V, do not exceed this voltage. Otherwise, it will fry your module. 
* When testing without antenna, the transceiver module was transmitting up to the range of 50-60 meters in the line of sight.
* Range can be increased with adding an antenna to both the modules.

## To interface the MQ-7 SENSOR to Arduino
 ### Requirements
  * MQ-7 CO sensor
  *  NPN bipolar transistor. Virtually any NPN transistor that can handle 300 mA or more will work here(I used BD 139).
  * Resistors: 2 x 1k (from 0.5k to 1.2k will work fine), and 1 x 10k (that one is best kept precise - although if you absolutely must use a different value, adjust reference_resistor_kOhm variable in the sketch accordingly).
  * Capacitors: 2 x 10uF or more(1uF ceramic capacitors will work too.). Tantalum or ceramic ones are required (Electrolytic capacitors were not working).
  * Green and red LED(optional)
  * Piezo Buzzer to indicate high CO level(optional)
  
  ### Circuit diagram
  
  ![](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/MQ-7_circuit.jpg)


 **Notes:**
* Make sure that the capacitors are ceramic(I took the capacitors of the value of 1uF).
* The connections of MQ-7 sensors were removed as shown in the image below to get the satisfactory results.
  
  ![Modified MQ7](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/modified_MQ-7.jpg)
* The voltages were varying from 4.3 V to 2.1 V due to the drop of 0.7V in the transistor. But Voltage drop across MQ-7 has to vary from 1.4V for 90 seconds to 5V for 60 seconds respectively according to [Datasheet](https://www.sparkfun.com/datasheets/Sensors/Biometric/MQ-7.pdf) of the MQ-7. This will result in an insignificant error which can be ignored(The lower voltage can be brought down to ~ 1.7V from 2.1V by changing 3.6 V in [code]() to nearly 4.7).
* MQ-7 sensor has to be calibrated by changing the "sensor_reading_clean_air" value in the code. Each sensor has to be calibrated individually. The value of **"sensor_reading_clean_air"** will change with different MQ-7 sensor.
* MQ-7 can also be calibrated by changing **"sensor_reading_100ppm_CO"** value in code from "-1" to analog value of sensor at 100ppm. 
* Do not connect MQ-7 directly with Arduino module it may damage this  module. This is because the Arduino can supply current up to 40mA and MQ-7 requires current up to 150 mA.
### [Code that has to be uploaded to MCU](https://github.com/avianshgaur/Intern_documentation/blob/master/co_monitor.ino)


