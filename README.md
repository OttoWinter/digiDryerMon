# digiDryerMon
ESP8266 based washer/dryer current monitoring via a split core current transformer over MQTT.  Pull Requests are welcome!  Please open an issue if you have any support needs.

Video Demostration and Setup - https://www.youtube.com/watch?v=1tqJkw5f0iA

UPDATE: If you don't want to use the custom Arduino sketch you can use the included files in the ESPHome folder.  You will need to modify the file to fit your network configuration.  Thanks to LuckyStyle for putting this together.  I have found the ESP8266 struggles to keep up with the API connection during each sensor poll and disconnects from the API so I used MQTT for this.

### Parts List
[Split Core Current Transformer](https://amzn.to/2XDcnoX)  
[Wemos D1 Mini](https://amzn.to/2SHvFpk)  
[10µF Capacitor](https://amzn.to/2VFhGC6)  
[10k Resistors](https://amzn.to/2ErWhWi)  
[Preformed Jumpers](https://amzn.to/2Ha3bCs)  
[Breadboard](https://amzn.to/2HbdINP)  

[Alternative NodeMCU 8266](https://amzn.to/2Eo3Ahu)  
[Alternative NodeMCU 8285](https://amzn.to/2TdNMIo)

### Sample Home Assistant Config 

```YAML
sensor:
  - platform: mqtt
    name: "Dryer Current"
    state_topic: "digiDryerMon-4A443E/SCT"
    unit_of_measurement : "A"
    icon: mdi:flash-circle
    availability_topic: "digiDryerMon-4A443E/LWT"
    payload_available: "Online"
    payload_not_available: "Offline"

  - platform: mqtt
    name: "DryerMon Signal"
    state_topic: "digiDryerMon-4A443E/RSSI"
    unit_of_measurement: "dBm"
    availability_topic: "digiDryerMon-4A443E/LWT"
    payload_available: "Online"
    payload_not_available: "Offline"   

  - platform: mqtt
    name: "DryerMon Status"
    state_topic: "digiDryerMon-4A443E/BUILD"
    availability_topic: "digiDryerMon-4A443E/LWT"
    payload_available: "Online"
    payload_not_available: "Offline"
```

### Sample Home Assistant Automation
https://www.digiblur.com/2018/11/smart-laundry-notifications-with-sonoff.html

### Wiring Diagram
![alt text](https://raw.githubusercontent.com/digiblur/digiDryerMon/master/jpgs/digiDryerMonLayout1.jpg "Wiring Diagram")
![alt text](https://raw.githubusercontent.com/digiblur/digiDryerMon/master/jpgs/digiDryerMonLayout2.jpg "Wiring Diagram2")
![alt text](https://raw.githubusercontent.com/digiblur/digiDryerMon/master/jpgs/sct-013-030-30a.jpg "SCT 30A/1V")
