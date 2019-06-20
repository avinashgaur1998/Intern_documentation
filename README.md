# Intern_documentation
This Readme file describes interfacing RF 433MHz, NRF_24, MQ-7 sensor with Arduino module. This file also has observations that were made after interfacing the above with Arduino. 


## Firstly, To interface RF 433 MHz with Arduino, the connections were made as mentioned below-
### RF 433Hz-Arduino wiring
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


The code to be uploaded on Arduino with transmitter and Reciever respectively has been attached in this [RF_433Hz](https://github.com/avianshgaur/Intern_documentation/tree/master/RF_433Hz) folder.


**NOTES:**
* While working with RF 5V without antenna, it gave a range of about 15m in the line of sight.
* Range can be increased by adding antenna to the Transmitter and Reciever.
**Specification of RF_433MHz Transmitter**
* Frequency Range: 433.92 MHz
* Input Voltage: 5V

**Specifications RF 433MHz Transmitter**
* Frequency Range: 433.92MHz
* Input Voltage: 3-12V
##sss





The next link is to interface the NRF24 Transceiver with the Arduino.
https://randomnerdtutorials.com/nrf24l01-2-4ghz-rf-transceiver-module-with-arduino/
While working with NRF_24 without antenna, it gave a range of about 60 meters in the line of sight.




The next link provides the entire procedure to interface the MQ-7 SENSOR to Arduino. Make sure that the capacitors are ceramic(I took the capacitors of the value of 1uF). he connections of MQ-7 sensors as mentioned in the link were removed to get the satisfactory results.
MQ-7 sensor has to be calibrated by changing the "sensor_reading_clean_air" value in the code. Each sensor has to be calibrated individually. The value of "sensor_reading_clean_air" will change with different MQ-7 sensor.
The link:
https://www.instructables.com/id/Arduino-CO-Monitor-Using-MQ-7-Sensor/
The co_monitor code has been attached already.
