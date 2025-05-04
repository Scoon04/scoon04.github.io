---
title: Block Diagram
---

![image](https://github.com/user-attachments/assets/3fb776ed-d963-4da6-bceb-58b18d3f9e56)

## General Info
My block diagram shows the components and their communication with the microcontroller. Because my section is the MQTT server, there arent many electrical components to show. There are some general buttons for programing and debuging, as well as a block for the micro usb port for programing. The uart pins are shown for showing how I will be sending and recieving data from my teamates boards. I added a 9V motor controlled by a transistor for the final showcase of the project. This was to give us something more presentable and exciting for our audience.

## Decision making Process
Given my responsibility for our teams project was managing the MQTT server, and our only microcontroller options were PIC18F and esp32-s3, then the choice has to be esp32-s3 as it had the wifi capabilities out of the box where thei PIC doesnt. The buttons and led were for debug and programming purposes. The transistor controlled motor was a last minute addon that was made after my team split into 2. We no longer had the motor driver system so the simplest solution was a transistor to controll a motor. This also fit the basic functionality of the spinning top.
