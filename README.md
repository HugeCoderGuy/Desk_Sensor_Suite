# Desk Sensor Suite
It's everything you need and everything you don't to monitor the state of your house (in this case the main cabin of the boat I live on) with the ability to check everything from anywhere!
<p align="center">
<img src="https://media.giphy.com/media/WLyFLFnENAt1ckAOiM/giphy-downsized-large.gif">
</p>

All of the data that is collected is displayed in real time graphs such as these below:
<p align="center">
<img width="900" alt="Screen Shot 2022-08-07 at 9 02 43 AM" src="https://user-images.githubusercontent.com/81666253/188034548-7ffb7218-52f5-4cdf-87f2-beedc9f959ba.png">
</p>

## Features

- Displays current PM2.5, PM1.0, ambient temperature, and humidity
- Arduino filters PM data for noise and displays rolling average of PMs for consistent data capture
- Uploads collected data to Thingspeak.com using via the ESP8266 wifi module every minute
- Security feature with the PIR sensor that is toggled by a button
  - Every time it senses the presence of someone, it documents it in the Thinspeak API call. My boat doesn't have a lock, so this feature is to help identify when a crime may have happened. 
- Hue changing mood light for the Jellyfish on top of the sensor suite
- Button debounce rejection with arduino external interrupt sequence
- 3D printed enclosure to hold all electronics in minimal package size


**To Do:**
- Debug IQ air API call to query current outdoor AQI at closest monitor station
  - Issue caused by ESP8266 misinterpretting ASCII symbols transmitted over serial by the arduino.

<p align="center">
<img src="https://user-images.githubusercontent.com/81666253/188033265-c2f5e337-6cc7-4013-a468-3004ea761d7d.jpg" width="400" align="center">
</p>
