---
title: API
---

## Message Types Breakdown

Below is a breakdown of how the messages im hangling should be structured. It shows the overall length of the message, the name of the variable each byte is stored in, the min and max values (based on the message types), and an example of what value would be exceptable. Im able to recieve a wide variety of data for each byte, but im only looking for a couple of values.

### Motor Direction (Type 1)

|  | Byte 1-2 | Byte 3 | Byte 4 | Byte 5-6 | Byte 7-8 |
|---|---|---|---|---|---|
| Variable Name | msgPref | motorDir_sender | motorDir_receiver | motorDir_data | msgSuf |
| Variable Type | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t |
| Min Value | AZ | M | A | 0x0040 | YB |
| Max Value | AZ | M | A | 0x0041 | YB |
| Example Value | AZ | M | A | 0x0041 | YB |

### Rotational Velocity (Type 3)

|  | Byte 1-2 | Byte 3 | Byte 4 | Byte 5-6 | Byte 7-8 |
|---|---|---|---|---|---|
| Variable Name | msgPref | rotVel_sender | rotVel_receiver | rotVel_data | msgSuf |
| Variable Type | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t |
| Min Value | AZ | S | M | 0 | YB |
| Max Value | AZ | S | M | 65535 | YB |
| Example Value | AZ | S | M | 27784 | YB |

For more information about the data types and communication with the team, visit the [Team Message Page](https://egr314-2025-s-309.github.io/Block-Process-Diagrams-Message-Structure/)

## API Code
```
from machine import UART, Pin
import time
import uasyncio as asyncio

# UART Setup
#uart = UART(0, 9600, tx = 43, rx = 44) #  My board
uart = UART(2, 9600, tx = 17, rx = 16) # Dev board
uart.init(9600, bits = 8, parity = None, stop = 1)
#led = Pin(16, Pin.OUT)

# Max Message length (bytes)
maxMsgLen = 64

# Set ID's
Bruce = b'\xFF'
Baron = b'\xFE'
Aadish = b'\xFD'
Shaurya = b'\xFC'
Broadcast = b'X'

# Prefix and Suffix
msgPref = b'AZ'
msgSuf = b'YB'

# Define bytes in data
# Motor Direction
motorDir_sender = Bruce
motorDir_receiver = Aadish
# Rotational Velocity
rotVel_sender = Shaurya
rotVel_receiver = Bruce

msg = b''

def readUART():
    msg = b''
    found_prefix = False
    while True:
        if uart.any():  # Check if there is data available
            byte = uart.read(1)  # Read one byte at a time
            if not found_prefix:
                if byte == msgPref[:1]:  # First byte matches first part of prefix
                    msg = byte  # Reset and start storing
                    next_byte = uart.read(1)  # Read the next byte
                    if next_byte == msgPref[1:]:  # Second byte matches
                        msg += next_byte
                        found_prefix = True
                continue  # Ignore any other byte before prefix
            else:
                msg += byte
                if msg.endswith(msgSuf):
                    break  # Suffix found, stop reading
    # Ensure valid message format and store sender and receiver
    if len(msg) <= maxMsgLen and msg[:2] == msgPref and msg[-2:] == msgSuf:
        sender = msg[2:3]
        receiver = msg[3:4]
        if receiver in [Baron, Bruce, Broadcast]:  # Check if message is for me
            return msg  # Return the entire message
        else:
            uart.write(msg)  # Forward message if not intended for me
    return None

# Send uart function
def sendUART(data, type):
    if type == 'motorDir':
        message = msgPref + motorDir_sender + motorDir_receiver + data + msgSuf
        uart.write(message)
    elif type == 'rotVel':
        message = msgPref + rotVel_sender + rotVel_receiver + data + msgSuf
        uart.write(message)

while 1:
    '''#UART Write Testing
    sendUART(bytes([0x16,0x12]),'rotVel')
    time.sleep(0.1)
    print(uart.read())
    #UART Read Testing'''
    sendUART(b'\x01\x02', 'rotVel')
    #led.value(not led.value())
    #data = b'\x01' + msgPref + rotVel_sender + rotVel_receiver + b'\x00\x19\x03\x04' + msgSuf + msgPref + rotVel_sender + rotVel_receiver + b'\x01\x18' + msgSuf
    #uart.write(data)
    time.sleep(.5)
    #testmsg = readUART()
    #print('MSG = ', uart.read())
    #led.value(not led.value())
    # Data Byte Breakdown
    '''print('String = ', recieveData)
    print('Length = ', len(recieveData))
    print('Prefix = ', recieveData[:2])
    print('Sender = ', recieveData[2])
    print('Reciever = ', recieveData[3])
    print('Data = ', recieveData[4:6])
    print('Suffix = ', recieveData[-2:])'''
```
