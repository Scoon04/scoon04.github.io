---
title: Schematic
---

## Schematic

![Individual System Design-1](https://github.com/user-attachments/assets/a326246e-0c13-4606-b9d4-72939ec2924e)

> Note: The RXD0 and TXD0 pins are the uart0 module. They were causing issues so I switched to using the uart2 module with RX on IO45 and TX on IO48. I didnt update the schematic becuase this represents how my board was designed. The uart modifications were made with external wires.

[Individual System Design.pdf](https://github.com/user-attachments/files/19599037/Individual.System.Design.pdf)

[Individual System Design (4-3-2025 11-19-09 PM).zip](https://github.com/user-attachments/files/19599112/Individual.System.Design.4-3-2025.11-19-09.PM.zip)

[Components.zip](https://github.com/user-attachments/files/19599134/Components.-.03.04.25.-.23.20.zip)

This schematic is simple electrically. The main focus of this system is to host UART communication through the other 2 systems and to communicate wirelessly with the HMI through MQTT server. This schematic doesnt show much of its functionallity becuase its functionallity is code and server based, but it does show the pins that will be used to communitate with the other PCBs and how power will be distributed to other boards. The 9V power rail comes from the barrel jack and into the pin out so it can go to other boards, and the RX and TX come in and out of the board through the in and out connectors.
