# Smart-Medicine-Bottle
RuuviTag Medication Reminder - For liquid Keppra Epilepsy Medication. <br>
The project may be easily modified for any medication, but the 3d prints were made for this particular bottle size.

### Disclaimer: This project depends on opensource software and hardware that is at best hobbiest grade and should not be considered medical grade.


## Features:
- A Node-Red flow for Home Assistant
  - sends a notification via NTFY if medication has not been given by a certain time.
  - Uses a RuuviTag BLE sensor to sense if bottle has been tipped over to load syringe.
  - 3D printed eclosure to attach BLE tag to bottom of Keppra bottle. 

## 3D printing
3D model was generated using the free version of [SketchUp](https://www.sketchup.com/plans-and-pricing/sketchup-free)
The current [STL model](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Bottle%20sensor%20(1).stl) file is a fraction too small and needs to be printed at 102% to fit Keppra Bottle snugly.
![Bottle Sensor](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Bottle%20Sensor.png?raw=true)
![Bottle](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Bottle.png?raw=true)
![RuuviTag](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/RuuviTag.png?raw=true)

## Node-Red
The [Node-Red flow](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Node-Red-HA-flow.json) has 2 parts:
- The first listens for changes in the z axis accelerometer from a RuuviTag.
  - values around +1 mean the bottle is the right way up.
  - values around -1 mean the bottle has been tipped over for loading a syringe.
  - If the bottle has been tipped over the **Home Assistant 'Keppra Given'** Sensor changes to True.
  - The sensor automatically resets at noon and midnight.
- The second part checks the **Home Assistant 'Keppra Given' Sensor** at set times in the morning and evening
  - If the sensor is false then a notification is sent to Phones subscribed to the NTFY topic.

![Node-Red](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/node-red.png?raw=true)

## Ruvitag
This project uses the Z axis accelerometor of a RuuviTag to determine orintation. Accelerometers are not available with the RuuviTag Home Assistant integration so another gateway device is needed. I am using [Ruuvi-Go-Gateway](https://github.com/Scrin/ruuvi-go-gateway) on Raspberry Pi which emulates the offical [Ruuvi Gateway](https://ruuvi.com/gateway/). 

## NTFY
This project depends on self hosted  [NTFY](https://docs.ntfy.sh/install/) instance for notifications.
But can easily be replaced with any other notification service.
