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

### IDs
| ID | User |
|---|---|
| M | Bruce |
| B | Baron |
| A | Aadish |
| S | Shaurya |

For more information about the data types and communication with the team, visit the [Team Message Page](https://egr314-2025-s-309.github.io/Block-Process-Diagrams-Message-Structure/)

## API Code
```
from machine import UART, Pin
import time
import uasyncio as asyncio

# UART Setup
uart = UART(2, 9600, tx=17, rx=16)
uart.init(9600, bits=8, parity=None, stop=1)
# LED Setup
led = Pin(2, Pin.OUT)

# Constants
maxMsgLen = 8
msgPref = b'AZ'
msgSuf = b'YB'
team = [b'B', b'M', b'A', b'S', b'X']  # Defines ID for each team member + broadcast(X)
# Assign individual IDs
id = team[0]        # B (This device)
bruce = team[1]     # M
aadish = team[2]    # A
shaw = team[3]      # S
broadcast = team[4] # X
receivedData = None

# Message Types
msgTypes = {
    aadish: [0x0040, 0x0041],  # Motor Direction: Only allows 0x0040 or 0x0041
    bruce: 'uint16'            # Rotational Velocity: Any value (0x0000 - 0xFFFF)
}

def sendUART(data, type):
    if type == 'motorDir':
        if data in msgTypes[aadish]:  # Only allow predefined values
            msg = msgPref + bruce + aadish + data.to_bytes(2, 'big') + msgSuf
            uart.write(msg)
            print(f'Sent: {msg}')
            return
        else:
            print(f'Send Error: Invalid motorDir data: {data}')
    elif type == 'rotVel':
        msg = msgPref + shaw + bruce + data.to_bytes(2, 'big') + msgSuf
        uart.write(msg)
        print(f'Sent: {msg}')
        return
    else:
        print('Send Error: Invalid type')

def handle_message(msg):
    global receivedData
    try:
        if len(msg) < 8 or len(msg) > maxMsgLen:
            print('Error: Invalid msg length')
            return
        # Extract parts of the message
        prefix = msg[:2]
        sender = msg[2:3]
        receiver = msg[3:4]
        data = int.from_bytes(msg[4:6], 'big')
        suffix = msg[-2:]
        # Validate format
        if prefix != msgPref or suffix != msgSuf:
            print('Error: Invalid message format')
            return
        # Validate sender
        if sender not in team:
            print('Error: Invalid sender')
            return
        if sender == id:
            print('Error: Ignoring message sent by me')
            return
        # Validate receiver
        if receiver not in team:
            print('Error: Invalid receiver')
            return
        if receiver not in [id, bruce, aadish, broadcast]:
            print('MSG not for me')
            uart.write(msg)
            return
        # Validate message type and data
        if receiver in msgTypes:
            if msgTypes[receiver] == 'uint16' or data in msgTypes[receiver]:
                receivedData = data
                return
            else:
                print(f'Error: Invalid data {data} for type {receiver}')
                return
        if receiver == broadcast:
            receivedData = data
            return
        print('Error: Unknown message type')
    except Exception as e:
        pass

async def readUART():
    stream = b''
    receiving_message = False
    while True:
        c = uart.read(1)  # Read one byte
        if c:
            stream += c  # Append byte to stream
            if stream.endswith(msgPref):  # MSG prefix detected
                receiving_message = True
                stream = msgPref  # Reset and keep prefix
            if receiving_message and stream.endswith(msgSuf):  # MSG suffix detected
                receiving_message = False
                print(f'ESP: Received {stream}')
                handle_message(stream)
                stream = b''  # Reset for next message
            if len(stream) > maxMsgLen:  # Discard oversized messages
                print('Error: Message too long')
                stream = b''
                receiving_message = False
        await asyncio.sleep_ms(10)  # Small delay for async handling

async def heartbeat():
    while True:
        #uart.write(b'\x00AZMA\x00\x40YB')
        sendUART(64, 'motorDir')
        await asyncio.sleep(5)

async def main():
    while True:
        print(f'Data = {receivedData}')
        await asyncio.sleep(1)

asyncio.create_task(readUART())
asyncio.create_task(heartbeat())

try:
    asyncio.run(main())
finally:
    asyncio.new_event_loop()
```
