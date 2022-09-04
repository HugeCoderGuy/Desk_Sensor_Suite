# Desk Sensor Suite
It's everything you need and everything you don't to monitor the state of your house (in this case the main cabin of the boat I live on) with the ability to check everything from anywhere!
<p align="center">
<img src="https://media.giphy.com/media/WLyFLFnENAt1ckAOiM/giphy-downsized-large.gif">
</p>

  The ultimate goal of this was to implement an AQI sensor on the boat so that we could see how much smoke was getting in durring California wildfire season. Then I decided to add the temp/humidity sensor. Then I added IOT functionaility. This process of "What other functionality can I add?" continued to spiral until it evolved into the compact unit you see before you. All of the data you don't see in the above gif is stored in a Thingspeak database that visualizes the data in a format as seen below:
<p align="center">
<img width="600" alt="Screen Shot 2022-08-07 at 9 02 43 AM" src="https://user-images.githubusercontent.com/81666253/188034548-7ffb7218-52f5-4cdf-87f2-beedc9f959ba.png">
</p>

  Overall I learned a ton from the project. Examples include juggling two serial communications intermittently, managing a circuit with 8 modules with varying operating voltages, and coordinating the code to handle everything fluidly. Spending whole days attempting to troubleshoot communication with the ESP8266 Wifi module certainly got fustrating, but the overal design experience was very enjoyable!

## Features
<p align="center">
<img src="https://media.giphy.com/media/VxLLXeweBaHsRnHc60/giphy-downsized-large.gif">
</p>

- Displays current PM2.5, PM1.0, ambient temperature, and humidity
- Arduino filters PM data for noise and displays rolling average of PMs for consistent data capture
- Uploads collected data to Thingspeak.com using via the ESP8266 wifi module every minute
- Security feature with the PIR sensor that is toggled by a button
  - Every time it senses the presence of someone, it documents it in the Thinspeak API call. My boat doesn't have a lock, so this feature is to help identify when a crime may have happened. 
- Hue changing mood light for the Jellyfish on top of the sensor suite
- Button debounce rejection with arduino external interrupt sequence
- LCD display is toggled on/off at night to prevent energy waste
- 3D printed enclosure to hold all electronics in minimal package size


**To Do:**
- Debug IQ air API call to query current outdoor AQI at closest monitor station
  - Issue caused by ESP8266 misinterpretting ASCII symbols transmitted over serial by the arduino.

## Setup
<p align="center">
<img src="https://user-images.githubusercontent.com/81666253/188033265-c2f5e337-6cc7-4013-a468-3004ea761d7d.jpg" width="300" align="center">
</p>

**Hardware Required:**

I've begun making the circuit diagram for this setup in fritzing, but it was honestly so involved that I decided that the documentation for a personal project such as this would be better saved for my goverment job. So if you're a bold individual trying to replicate this, here is your shopping list:
- Arduino Mega
- ESP8266 Wifi Module
- Photoresistor
- 16x2 LCD
- DHT11 temp/humidity sensor
- Mini breadboard
- Adafruit Neopixel
- x2 buttons
- A few resistors to limit current to LCD and photoresistor
- Various wires
- x6 M3 screws for LCD and arduino
- Some glue
- PIR sensor 

I designed the 3D printed housing to house all of the components in Solidworks. I then printed it on my Monoprice Select Mini with 50% infill at a normal resolution. Supports are not required for the jellyfish base, but is necesesary for the slot that allows the backplate to slide in.

**Software:**

The dependencies for this is a whole lot more straight forward than the hardware. The SoftwareSerial library is used to communicate with the PM sensor and computer durring the debugging process. The good'ol liquidcrystal library manages the LCD. Adafruit's neopixel and PM2.5 libraries handle their sensors. Finally the DHT library handles the DHT11 module.  


***[The Code Can be Found Here!]()***
