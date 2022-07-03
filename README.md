# Semi-autonomous Submarine Motherboard 
Hardware files for our university semi-autonomous submarine robot's motherboard design for the MATE ROV Robotics Competition (a submersible remotely operated submarine vehicle competition). This motherboard connects the surface computer to the main data-handler and general computer for our robot: a Raspberry Pi Compute Module 4. It serves as a module to control the thrusters and cameras on our robot. 

Motherboard Description
---
We chose this device as our main computer because of its high-speed operation and inclusion of many desirable features, namely the support of a PCIe x1 lane. We used this PCIe lane to provide four high-speed USB 3.0 connections, which were used for our cameras. Other than PCIe, our motherboard has Ethernet, which is used to talk with the surface computer, back-up serial connectors, and expansion slots that are used to connect to our daughterboards.

PCB Description
---
Motherboard is a 6 layer board. The full system schematic located in **"Motherboard System Schematic"** and PCB located in **"Motherboard_PCB"**. We have a Top Layer (1) and Bottom Layer (2) for essential routing connection. Next, we have (3) 3.3V layer dedicated to supply 3.3V and a (4) layer for GND GND Plane. Finally, we have a Horizontal Layer (5) and Vertical Layer (6) reserved for the low priority routing connections, such as a GPIO breakout headers. 

Power
---
We use a 12V and 5V external power supply (J9 Pg 1) to power the Motherboard. A buck converter takes the 12V power supply and switches it down to 3.3V. This 3.3V supply directly feeds the (1) external I/O board modules (slotted into Card-Edge Sockets) and (2) PCIe connector. The RPi CM4 and PiHawk external module uses the 5V from the external source.  

Cameras
---
The motherboard allows us to access the cameras underwater. The cameras are connected to an external PCIe-USB Exansion card. The motherboard uses a PCIe connector (J10 Pg 3) to convert the PCIe-USB Expansion card to command the RPI CM4 (MOD1B Pg 5) over PCIe. The RPi CM4 then uses ethernet (J13) to communicate to an external surface computer. 

![alt text](https://github.com/nnh12/ROV-Motherboard-2022/blob/main/Blocked%20Diagrams/Images/Motherboard%20Camera%20Block%20Diagram.jpg)

Thrusters
---
The motherboard controls our robot's thrusters. Our surface computer commands the RPi CM4 (MOD1B Pg 5). The RPiCM4 then communicates over USB.20 to a High-Speed-USB-Signal Switch (U8 Pg 6), converting the signal into USB Type-B Micro. This command gets sent to an external module (called PiHawk) that directly drive the thrusters. PiHawk is slotted into one of the motherboard's Card-Edge-Sockets (J8 Pg 2). In addition, to USB 2.0, it also communicates over UART to PiHawk.

![alt text](https://github.com/nnh12/ROV-Motherboard-2022/blob/main/Blocked%20Diagrams/Images/Motherboard%20Thruster%20Diagram.jpg)

External I/O Board Modules
---
The motherboard communicates over I2C to our I/O Board that our external, slotted into the Card-Edge-Sockets (J3 + J6 Pg 2). They are responsible for controling LEDs, Solenoids, and  brushed motor controllers. 

Full System Diagram
---
![alt text](https://github.com/nnh12/ROV-Motherboard-2022/blob/main/Blocked%20Diagrams/Images/Motherboard%20.jpg)
  


