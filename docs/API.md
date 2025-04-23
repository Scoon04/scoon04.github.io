---
title: API
---

## Message Types Breakdown

Below is a breakdown of how the messages im hangling should be structured. It shows the overall length of the message, the name of the variable each byte is stored in, the min and max values (based on the message types), and an example of what value would be exceptable. Im able to recieve a wide variety of data for each byte, but im only looking for a couple of values.

### Motor On/Off

|  | Byte 1-2 | Byte 3 | Byte 4 | Byte 5-6 | Byte 7-8 |
|---|---|---|---|---|---|
| Variable Name | msgPref | motor_sender | motor_receiver | motor_data | msgSuf |
| Variable Type | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t |
| Min Value | AZ | M | B | 0x0040 | YB |
| Max Value | AZ | M | B | 0x0041 | YB |
| Example Value | AZ | M | B | 0x0041 | YB |

### IDs
| ID | User |
|---|---|
| M | Bruce |
| B | Baron |

For more information about the data types and communication with the team, visit the [Team Message Page](https://egr314-2025-s-309.github.io/Block-Process-Diagrams-Message-Structure/)

## API Code
```
import time
from machine import UART, Pin
import uasyncio as asyncio

uart = UART(2, 9600, tx=48, rx=45)
uart.init(9600, bits=8, parity=None, stop=1)
led = Pin(2, Pin.OUT)

maxMsgLen = 8
msgPref = b'AZ'
msgSuf = b'YB'
team = [b'B', b'M', b'X']
id = team[0]
bruce = team[1]
broadcast = team[2]

msgTypes = {
    id: [0x0040, 0x0041],
}

# Send UART Message
def sendUART(data):
    if data in msgTypes[id]:
        msg = msgPref + bruce + id + data.to_bytes(2, 'big') + msgSuf
    else:
        print('Invalid UART send')
        return
    uart.write(msg)
    print(f'Sent: {msg}')

# Parse UART Message
def handle_message(msg):
    try:
        if len(msg) != maxMsgLen or msg[:2] != msgPref or msg[-2:] != msgSuf:
            print('Bad message format')
            return
        sender, receiver = msg[2:3], msg[3:4]
        data = int.from_bytes(msg[4:6], 'big')
        if sender == id or receiver not in [id, broadcast]:
            print('Invalid sender or receiver')
            return
        if receiver in msgTypes and data in msgTypes[receiver]:
            print(f'Data: {data}')
        elif receiver == broadcast:
            print(f'Data: {data}')
    except Exception as e:
        print('UART handling error:', e)

# UART Receiver Coroutine
async def readUART():
    stream, receiving = b'', False
    while True:
        c = uart.read(1)
        if c:
            stream += c
            if stream.endswith(msgPref):
                receiving = True
                stream = msgPref
            elif receiving and stream.endswith(msgSuf):
                handle_message(stream)
                stream, receiving = b'', False
            if len(stream) > maxMsgLen:
                stream, receiving = b'', False
        await asyncio.sleep_ms(10)

async def main():
    asyncio.create_task(readUART())
    while True:
        sendUART(65)
        await asyncio.sleep(1)

try:
    asyncio.run(main())
finally:
    asyncio.new_event_loop()

```
