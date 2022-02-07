<h1 align="center">
  BuildingMonitoringSystem
</h1>
<p>Security monitoring and control system in a public building using Can bus.</p>
<p>The system consists of two modules: master and slave.</p> 

<p>The slave module receives data from sensors, next sends them by CAN transmission with a time interval of 1sec. The sensors provide information about the detection of fire, water, movement and dangerous gases.</p>

<p>The master module receives the information and, depending on the operating mode, takes the appropriate action. Each state displays a graphic on OLED screen. The operating mode can be selected using the keypad:</p>
- A: Disable State ( Disable action on incoming sensor messages )<br/>
- B: Lock State ( Simulate close building. If slave detect move, gas, fire or water, than alarm was triggered. RFID Card unlock building. )<br/>
- C: Unlock State ( If slave detect gas, fire or water, than alarm was triggered. RFID Card lock building )<br/>
- D: Alarm State ( Can be triggered auto or manual )<br/><br/>

<p>Change from Lock State to Unlock State and vice versa can be triggered by RFID card or badge</p>

![architecture](https://user-images.githubusercontent.com/38471368/148918213-27d3c155-dfc0-4c97-afc3-69e99ef02944.png)

# Master

![master](https://user-images.githubusercontent.com/38471368/148575802-17fef368-e944-4c77-8095-dd460ee70d9f.png)


# Slave

![slave](https://user-images.githubusercontent.com/38471368/148462722-69f697cd-3ba4-4d00-b532-36160dce1bb4.png)

# CAN

### Microchip MCP2515 wiring

| Microchip MCP2515 | Arduino |
| :---------------: | :-----: |
| VCC | 5V |
| GND | GND |
| SCK | SCK |
| SO | MISO |
| SI | MOSI |
| CS | 10 |
| INT | 2 |


`CS` and `INT` pins can be changed by using `CAN.setPins(cs, irq)`. `INT` pin is optional, it is only needed for receive callback mode. If `INT` pin is used, it **must** be interrupt capable via [`attachInterrupt(...)`](https://www.arduino.cc/en/Reference/AttachInterrupt).

**NOTE**: Logic level converters must be used for boards which operate at 3.3V.

### Espressif ESP32 wiring

Requires an external 3.3V CAN transceiver, such as: SN65HVD230 - Waveshare 3945 <br/>

CAN_H ----------- CAN_H <br/>
CAN_L ----------- CAN_L <br/>


| CAN transceiver | ESP32 |
| :-------------: | :---: |
| 3V3 | 3V3 |
| GND | GND |
| CTX | GPIO_5 |
| CRX | GPIO_4 |

`CTX` and `CRX` pins can be changed by using `CAN.setPins(rx, tx)`.



## 🚀 Quick start
### Visual Studio with Visual Micro or Arduino IDE
1. ESP 32
2. Build & deploy code

## 🧪 Technology Stack

- C++

## 🛠️ Project References:

- https://github.com/sandeepmistry/arduino-CAN
- https://github.com/miguelbalboa/rfid
