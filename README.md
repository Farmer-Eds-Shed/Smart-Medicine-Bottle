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

Current STL model files are a fraction too small and need to be printed at 102% to fit Keppra Bottle snugly.
![Bottle Sensor](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Bottle%20Sensor.png?raw=true)
![Bottle](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/Bottle.png?raw=true)
![RuuviTag](https://github.com/Farmer-Eds-Shed/Smart-Medicine-Bottle/blob/main/RuuviTag.png?raw=true)

## Node-Red

## Ruvitag
This project uses the Z axis accelerometor of a RuuviTag to determine orintation. Accelerometers are not available with the RuuviTag Home Assistant integration so another gateway device is needed. I am using [Ruuvi-Go-Gateway](https://github.com/Scrin/ruuvi-go-gateway) on Raspberry Pi which emulates the offical Ruuvi Gateway. 

## NTFY
This project depends on self hosted  [NTFY](https://docs.ntfy.sh/install/) instance for notifications.
But can easily be replaced with any other notification service.
