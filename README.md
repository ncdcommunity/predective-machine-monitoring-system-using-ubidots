# Predictive Maintenance and Machine Health Monitoring

Predictive Maintenance and Machine health monitoring is one of the most critical and important parts of the automation industry. In an automation or production factory these machines work on an average 20 hours per day.  In modern automation, all these machines work together and stay in sync, so its very important that every single machine is healthy.  In the old days, the usual ways to monitor machine health was manual inspection and occasional temperature readings.  With modern day technology, we can monitor these machines 24-7 and analyze the health. By doing this we keep an eye on every single change the machine is going through. The machine health monitoring is also known as predictive maintenance.

**Whats Predictive Maintenance and Machine Health Monitoring?**
Predictive maintenance and machine health monitoring go side by side.  If we know whats going on with the machine, we can predict when it needs repair or the end of it’s useful life. By knowing these two things we can work on fixing the problem on a schedule without any operational down-time. There are quite a few ways we can monitor device or machine health and a send notification to a technician when a machine needs some attention.  There are few device which are used to connect machine health data:

- Temperature and Humidity Data Monitoring
- Current and Voltage Monitoring
- Vibration Monitoring
In this article, we will read current and publish the data on Ubidots.  ubidots supports graphs, UI, notifications, and emails.  These features make it ideal for predictive maintenance analysis.We will also get the data in google sheets which will make predictive maintenance analysis more easier.

Hardware :
- [ESP-32](https://store.ncd.io/product/esp32-iot-wifi-ble-module-with-integrated-usb/)
- [IoT Long Range Wireless Vibration And Temperature Sensor](https://store.ncd.io/product/iot-long-range-wireless-vibration-and-temperature-sensor/)
- [I2C Cable](https://store.ncd.io/product/i2c-cable/)
- [PARTICLE ELECTRON OR PHOTON COMPATIBLE I2C SHIELD](https://shop.controleverything.com/products/i2c-breakout-for-particle-electron-or-particle-photon)
- [ZigBee Coordinator Long Range Wireless Mesh Modem with USB Interface](https://store.ncd.io/product/zigbee-coordinator-long-range-wireless-mesh-modem-with-usb-interface/)

Software Used:
- Arduino IDE
- [Ubidot](https://ubidots.com/)

Library Used:
- PubSubClient Library
- Wire.h

# Arduino Client for MQTT
This library provides a client for doing simple publish/subscribe messaging with a server that supports MQTT

For more information about MQTT, visit [mqtt.org](http://mqtt.org/).
## Download
The latest version of the library can be downloaded from [GitHub](https://github.com/knolleary/pubsubclient/releases/tag/v2.7)
## Documentation
The library comes with a number of example sketches. See File > Examples > PubSubClient within the Arduino application.
Full [API Documentation](https://pubsubclient.knolleary.net/api.html).
## Compatible Hardware
The library uses the Arduino Ethernet Client api for interacting with the underlying network hardware. This means it Just Works with a growing number of boards and shields, including:

- Arduino Ethernet
- Arduino Ethernet Shield
- Arduino YUN – use the included YunClient in place of EthernetClient, and be sure to do a Bridge.begin() first
- Arduino WiFi Shield - if you want to send packets greater than 90 bytes with this shield, enable the [MQTT_MAX_TRANSFER_SIZE]  (https://pubsubclient.knolleary.net/api.html#configoptions) option in   PubSubClient.h.
- Sparkfun WiFly Shield – when used with [this](https://github.com/dpslwk/WiFly) library
- Intel Galileo/Edison
- ESP8266
- ESP32
The library cannot currently be used with hardware based on the ENC28J60 chip – such as the Nanode or the Nuelectronics Ethernet Shield. For those, there is an alternative library available.

# Wire Library
  The Wire library allows you to communicate with I2C devices, often also called "2 wire" or "TWI" (Two Wire Interface),can download  from [Wire.h](https://github.com/PaulStoffregen/Wire)
## Basic Usage
- Wire.begin()
  Begin using Wire in master mode, where you will initiate and control data transfers. This is the most common use when interfacing with   most I2C peripheral chips.

- Wire.begin(address)
  Begin using Wire in slave mode, where you will respond at "address" when other I2C masters chips initiate communication.
  
 ## Transmitting
 - Wire.beginTransmission(address)
   Start a new transmission to a device at "address". Master mode is used.

- Wire.write(data)
  Send data. In master mode, beginTransmission must be called first.

- Wire.endTransmission()
  In master mode, this ends the transmission and causes all buffered data to be sent.
  
## Receiving
- Wire.requestFrom(address, count)
  Read "count" bytes from a device at "address". Master mode is used.

- Wire.available()
  Retuns the number of bytes available by calling receive.

- Wire.read()
  Receive 1 byte.

# Steps to send data to labview vibration and temperature platform using IoT Long Range Wireless Vibration And Temperature Sensor and ZigBee Coordinator Long Range Wireless Mesh Modem with USB Interface-

- Industrial Wireless Vibration temperature Sensor With 2 Mile Range Long range wireless IoT Vibration Temperature sensor can be found over here https://store.ncd.io/iot-long-range-wireless-vibration-and-temperature-sensor/

- This Labview software will work with ncd.io wireless Vibration Temperature sesnor only

- To use this Labview Utility You will need a Wireless to USB router, whihc can be found over here https://store.ncd.io/product/900hp-   s3b-long-range-wireless-mesh-modem-with-usb-interface/

- To use this UI, you will need to install following drivers Install run time engine from here 64bit http://www.ni.com/download/labview-run-time-engine-2017/6821/en/

- 32 bit http://www.ni.com/download/labview-run-time-engine-2017/6822/en/

- Install NI Visa Driver -- http://www.ni.com/download/ni-visa-run-time-engine/6647/en/

- Install Labview Run time serial driver http://www.ni.com/download/ni-serial-17.0/6613/en/ http://www.ni.com/download/labview-run-time-engine-2017-sp1/7191/en/

- Getting strated guide for this product can be found over here https://ncd.io/long-range-iot-wireless-vibration-sensor-getting-started/

- Complete product manual for this product can be found over here https://ncd.io/long-range-iot-wireless-vibration-sensor-product-manual/

##  Uploading the code  to ESP32 using Arduino IDE:
- **Download and include the PubSubClient Library and Wire.h Library.**
- **You must assign your unique Ubidots TOKEN, MQTTCLIENTNAME, SSID (WiFi Name) and Password of the available network.**
- **Compile and upload the  [Ncd__vibration_and_temperature.ino](https://github.com/mjScientech/https-github.com-mjScientech-ESP32-AND-SI7021/blob/master/Ncd__vibration_and_temperature.ino) code.**
- **To verify the connectivity of the device and the data sent, open the serial monitor.If no response is seen, try unplugging your ESP32 and then plugging it again. Make sure the baud rate of the Serial monitor is set to the same one specified in your code 115200.**

## Serial monitor output.
![alt tag](https://github.com/mjScientech/https-github.com-mjScientech-ESP32-AND-SI7021/blob/master/vibration%20serial.JPG)

## Making the Ubidot work:
- **Create the account on [Ubidot](https://ubidots.com/).**
- **Go to my profile and note down the token key which is a unique key for every account and paste it to your ESP32 code before uploading.**
- **Add a new device to your ubidot dashboard name esp32.**
  
![alt tag](https://github.com/mjScientech/Esp32-And-SHT30/blob/master/device234.JPG)

                       Click on devices and select devices in ubidot.

![alt tag](https://github.com/mjScientech/ESP32-AND-SI7021/blob/master/Device.JPG)

     Now you should see the published data in your Ubidots account, inside the device called "ESP32".

- **Inside device create new variable name sensor in which your temperature reading will be shown.**
![alt tag](https://github.com/mjScientech/ESP32-AND-SI7021/blob/master/variable.JPG)
                  
![alt tag](https://github.com/mjScientech/-predictive-machine-monitoring-system-using-Ubidots-and-Long-Range-Wireless-Vibration-And-Temp/blob/master/variable1.PNG) 

     Now you are able to view the Temperature and other sensors data which was previously viewed in serial monitor.This
     happened because the value of  different sensor readings  is passed as a string and store in
     variable and publish to variable inside  device esp32. 
- **Create dashboard in ubidots**
![alt tag](https://github.com/mjScientech/https-github.com-mjScientech-ESP32-AND-SI7021/blob/master/dashboard1.JPG)
       
          Go to data select dashboard and inside dashboard create different widgets and add new widget 
          to your dashboard screen.
# OUTPUT
- **Now as the temperature/vibration  increases and decreases new data available inside the various variable.**
![alt tag](https://github.com/mjScientech/-predictive-machine-monitoring-system-using-Ubidots-and-Long-Range-Wireless-Vibration-And-Temp/blob/master/dashboard1.PNG)
# Creating events in ubidots:
1. Select Events (from the Data dropdown).
![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event1.PNG)

2. To create a new event, click the yellow plus icon in the upper right corner of the screen.
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event2.PNG)

**Types of Events**
Ubidots support already integrated events to allow you to send Events, Alerts, and Notifications to those who need to know, when they need to know. 
Ubidots' prebuilt integrations include: 

- Email notifications
- SMS notifications
- Webhook events - [learn more](https://help.ubidots.com/user-guides/events-create-a-webhook)
- Telegram notifications
- Slack notifications - [learn more](https://help.ubidots.com/user-guides/events-slack-webhook-setup)
- Voice Call notifications - [learn more](https://help.ubidots.com/user-guides/events-voice-call-notifications)
- Back to Normal notification - [learn more](https://help.ubidots.com/user-guides/events-back-to-normal-events-and-notifications)
- Geofence notifications - [learn more](https://help.ubidots.com/user-guides/creating-a-geofence-alert)

3. Then choose a device and associating variable that indicates the devices' "values".
[![alt tag](https://github.com/mjScientech/-predictive-machine-monitoring-system-using-Ubidots-and-Long-Range-Wireless-Vibration-And-Temp/blob/master/ubi1.PNG)

4. Now selct a thresold value for your event to trigger and compare it to device values and also select time to trigger your event .

5.  Establish and configure which actions are to be executed and the message to the receiver: Send SMS, Email, Webhooks, Telegrams,     Phone Calls, SLACK, and webhooks to those who need to know.
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event6.PNG)

6.  Configure the Event notice.
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event5.PNG)

7. Determine the activity window the events may/may not be executed.
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event9.PNG)

8. Confirm your Events.

# Output of event in your mail
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/outevent.PNG)


