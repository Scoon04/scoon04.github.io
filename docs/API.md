---
title: API
---

## Message Types Breakdown

Below is a breakdown of how the messages im hangling should be structured. It shows the overall length of the message, the name of the variable each byte is stored in, the min and max values (based on the message types), an example of what value would be exceptable, and what values im expecting. Im able to recieve a wide variety of data for each byte, but im only looking for a couple of values. This is why the expected values row is very important.
> Example: I can recieve up to 255 for message sender, but I only need to know 4 values (one for each teamate), so while 205 fits within the acceptable range, I may not be looking for that value specifically.

### Motor Direction (Type 1)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | motorDir_pref | motorDir_pref | motorDir_sender | motorDir_receiver | motorDir_data | motorDir_data | motorDir_suf | motorDir_suf |
| Variable Type | uint16_t | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t | uint16_t | uint16_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 65535 | 65535 | 255 | 255 | 65535 | 65535 | 65535 | 65535 |
| Example Value | 100 | 10001 | 205 | 220 | 2886 | 17025 | 2040 | 2001 |
| Expected Values | 0 (0x00) | 1 (0x01) | 255 (0xFF) | 253 (0xFD) | 0 (0x00)<br>0 (0x00) | 64 (0x40)<br>65 (0x41) | 0 (0x00) | 32 (0x20) |

> Some variables are stored in the same variable but across multiple bytes. Any 2 bytes that share a variable name will store the expected values togeather. Example: motorDir_pref has 2 bytes. Byte 1 = 0x00, Byte 2 = 0x01. The actual stored value will look like this: 0x0001. This takes two 8 bit segments and strings them togeather.

### Rotational Velocity (Type 3)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | rotVel_pref | rotVel_pref | rotVel_sender | rotVel_receiver | rotVel_data | rotVel_data | rotVel_suf | rotVel_suf |
| Variable Type | uint16_t | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t | uint16_t | uint16_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 65535 | 65535 | 255 | 255 | 65535 | 65535 | 65535 | 65535 |
| Example Value | 625 | 305 | 253 | 164 | 53244 | 27784 | 7357 | 21346 |
| Expected Values | 0 (0x00) | 3 (0x03) | 252 (0xFC) | 255 (0xFF) | Varies | Varies | 0 (0x00) | 34 (0x22) |

> The expected value of rotational velocity is set to varies. This is because the value will be read in decimal form and converted to hexidecimal to send. This means I need to be ready to recieve a wide variety of data. The other data is treated as a digital state change (if x then do y). This data is being continuously updated.

For more information about the data types and communication with the team, visit the [Team Message Page](https://egr314-2025-s-309.github.io/Block-Process-Diagrams-Message-Structure/)

## API Code
```
from machine import UART
from machine import Pin
import time
import uasyncio as asyncio

# initialize a new  UART class
uart = UART(2, 9600, tx = 17, rx = 16)
# run the init method with more details including baudrate and parity
uart.init(9600, bits = 8, parity = None, stop = 1) 

# Message length (bytes)
msgLen = 8

# Set ID's
Bruce = bytes([0xFF])
Baron = bytes([0xFE])
Aadish = bytes([0xFD])
Shaurya = bytes([0xFC])

# Define bytes in data
# Motor Direction
motorDir_pref = bytes([0x00,0x01])
motorDir_sender = Bruce
motorDir_receiver = Aadish
motorDir_suf = bytes([0x00,0x20])
# Rotational Velocity
rotVel_pref = bytes([0x00,0x03])
rotVel_sender = Shaurya
rotVel_receiver = Bruce
rotVel_suf = bytes([0x00,0x22])

# Send uart function
def sendUART(data, type):
    if len(data) == 2: # Is data 2 bytes long
        if type == 'motorDir':
            message = motorDir_pref + motorDir_sender + motorDir_receiver + data + motorDir_suf
            uart.write(message)
        elif type == 'rotVel':
            message = rotVel_pref + rotVel_sender + rotVel_receiver + data + rotVel_suf
            uart.write(message)
    else:
        raise ValueError('Invalid data length')

# Read uart function
def readUART(): 
    if uart.any(): # Is there any incoming data for uart to read?
        readString = uart.read() # Read and store data
        if readString and len(readString) == msgLen: # Checks if readString actally has data and if it's the proper length
            if bytes([readString[3]]) == Baron or bytes([readString[3]]) == Bruce: # Checks if data is meant for me
                if readString[:2] == motorDir_pref and readString[-2:] == motorDir_suf: # Is data meant for Motor Direction?
                    motorDir_data = readString[4:6] # Stores 2 data bytes for Motor Direction, [inclusive, exclusive]
                    return motorDir_data
                elif readString[:2] == rotVel_pref and readString[-2:] == rotVel_suf: # Is data meant for Rotational Velocity?
                    rotVel_data = readString[4:6] # Stores 2 data bytes for Rotational Velocity, [inclusive, exclusive]
                    return rotVel_data
                else:
                    raise ValueError('Invalid Message Format')
            else: # Data isnt meant for me
                uart.write(readString) # Place code that will send data to next user
        else:
            raise ValueError('Invalid Message Length')
    return None

while True:
    '''#UART Write Testing
    sendUART(bytes([0x16,0x12]),'rotVel')
    time.sleep(0.1)
    print(uart.read())
    #UART Read Testing'''
    data = motorDir_pref + motorDir_sender + Baron + bytes([0x00,0x19]) + motorDir_suf
    uart.write(data)
    time.sleep(0.1)
    motorDir_data = readUART()
    print('Data = ',motorDir_data)
    #Data Byte Breakdown
    '''print('String = ', recieveData)
    print('Length = ', len(recieveData))
    print('Prefix = ', recieveData[:2])
    print('Sender = ', recieveData[2])
    print('Reciever = ', recieveData[3])
    print('Data = ', recieveData[4:6])
    print('Suffix = ', recieveData[-2:])'''
    #time.sleep(1)
```
