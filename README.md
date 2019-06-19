# Intern_documentation
https://randomnerdtutorials.com/rf-433mhz-transmitter-receiver-module-with-arduino/
The above link contains the instructions to interface RF 5V TX/RX with arduino.
While working with RF 5V without antenna, it gave a range of about 15m in the line of sight.



The next link is to interface the NRF24 Tranceiver with the arduino.
https://randomnerdtutorials.com/nrf24l01-2-4ghz-rf-transceiver-module-with-arduino/
While working with NRF_24 without antenna, it gave a range of about 60 metres in the line of sight.




The next link provides the entire procedure to interface MQ-7 SENSOR to Arduino. Make sure that the capacitors are ceramic(I took the capacitors of value of 1uF). he connections of MQ-7 sensors as mentioned in the link were removed to get the satisfactory results.
MQ-7 sensor has to be callibrated by changing the "sensor_reading_clean_air" value in the code. Each sensor has to be calibrated individually. The value of "sensor_reading_clean_air" will change with diffrent MQ-7 sensor.
The link:
https://www.instructables.com/id/Arduino-CO-Monitor-Using-MQ-7-Sensor/
The co_monitor code has been attached already.


