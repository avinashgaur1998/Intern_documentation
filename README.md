# Intern_documentation
This Readme file describes interfacing RF 433MHz, NRF_24, MQ-7 sensor with Arduino module. This file also has observations that were made after interfacing the above with Arduino. 
## Product Developed at the end of Internship: Wearable Air Quality Monitoring System
In an attempt to make the air quality sensors suitable for personal use, we designed a compact sensor system that can be attached to the backpack. This sensor system comprises of CCS811, PMS7003, and HC-05 Bluetooth module controlled by Arduino mini pro. CCS811 measures the CO2 levels, VOC and Temperature, and PMS7003 sensor, measure the PM1, PM2.5, PM10 concenteration levelsnear the user. User can connect with the sensor via Bluetooth and check the air quality in their surroundings, as shown in the figures below. This Wearable can also be used for dust detection at a construction site, to alert the worker if the dust particles are above a certain threshold

### ![Expected_output](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/RF_24.jpg)

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

### ![Expected_output](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/RF_24.jpg)


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

### ![nRF24_Output](https://github.com/avianshgaur/Intern_documentation/blob/master/png_nRF24/nRF24_output.png)

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
* The voltages were varying from 4.3 V to 2.1 V due to the drop of 0.7V in the transistor. But Voltage drop across MQ-7 has to vary from 1.4V for 90 seconds to 5V for 60 seconds respectively according to [Datasheet](https://www.sparkfun.com/datasheets/Sensors/Biometric/MQ-7.pdf) of the MQ-7. This will result in an insignificant error which can be ignored(The lower voltage can be brought down to ~ 1.7V from 2.1V by changing all the 3.6 in [code](https://github.com/avianshgaur/Intern_documentation/blob/master/co_monitor.ino) in lines 75-78 to nearly 4.8 ).
* MQ-7 sensor has to be calibrated by changing the "sensor_reading_clean_air" value in the code. Each sensor has to be calibrated individually. The value of **"sensor_reading_clean_air"** will change with different MQ-7 sensor.
* MQ-7 can also be calibrated by changing **"sensor_reading_100ppm_CO"** value in code from "-1" to analog value of sensor at 100ppm. 
* Do not connect MQ-7 directly with Arduino module it may damage this  module. This is because the Arduino can supply current up to 40mA and MQ-7 requires current up to 150 mA.
### [Code that has to be uploaded to MCU](https://github.com/avianshgaur/Intern_documentation/blob/master/co_monitor.ino)

## To Interface PMS7003 with Arduino
PMS7003 is a kind of digital and universal particle concentration sensor, which can be used to obtain the number of suspended particles in the air, i.e. the concentration of particles, and output them in the form of digital interface.
**Requirements:**
* Host MCU (Arduino Mini Pro 3.3V in this case)
* PMS7003
* Resistor 10kohm

![](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/Pin_def.png)

### General Circuit Structure  :

![](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/circuit_diagram.png)

### [Code to be uploaded](https://github.com/avianshgaur/Intern_documentation/blob/master/PMS7003/PMS7003.ino)
 #### Circuit Diagram according to above code
| PMS7003 | Arduino |
| :---------: | :------:|
| VCC | 5V |
| GND | GND |
|Pin 7 | 3(TX)   |  
| Pin 9| 2(RX)   |


**Note:**
SoftareSerial library should be downloaded before uploading the code.

**Notes**
* DC 5V power supply is needed because the FAN should be driven by 5V. But the high level of data pin is 3.3V. Level conversion unit    should be used if the power of host MCU is 5V.
* The SET and RESET pins are pulled up inside so they should not be connected if without usage( They were not connected in this case).
* PIN7 and PIN8 should not be connected.
* Stable data should be got at least 30 seconds after the sensor wakeup from the sleep mode because of the fan’s performance.

### Expected Output

![](https://github.com/avianshgaur/Intern_documentation/blob/master/other_png/Output.png)


## Calibrating Ultimaker 2+
After the “Welcome” screen, the Ultimaker 2 will guide you through some steps for calibrating the build plate. For printing it is very important that the first layer is nicely squished into the glass plate and sticks well to it. If the distance between the nozzle and build plate is too big, your print won’t stick properly to the glass plate. On the other hand, if the nozzle is too close to the build plate it can prevent the filament from extruding from the nozzle.
 * Upload ".gcode" file in the memory card and Enter print on the Ultimaker printer
 * Clean the Buildplate surface if it is not cleaned.
  * Apply glue like Fevistick on the Buildplate. This is needed to stick 1st layer of print to surface.
  
  
 **Notes**
 * Bed Leveling: To calibrate Build plate navigate "Maintenance" > "Build plate". Then Ultimaker Printer will guide you step by step to calibrate the printer.
 * If even after levelling if the 1st layer is not sticking to surface, then check the nozzle temperature, Buildplate temperature in the setting. The temperature is diffrent for diffrent material. Increase or decrease the temperature according the material.
  For knowing about the material, find its name on the reel placed on Printer.
 
