---
title: Component Selection
---

## PIC Microcontroller

| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| PIC18F47Q10-I/PT TQFP<br>![Image](https://github.com/user-attachments/assets/6d7fc249-07ad-4904-bfbb-ba29c82f6786)<br>$1.22<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F47Q10#product-purchase) | - More Pins<br>- 128KB Flash Size | - Slightly Larger Size<br>- Don't need all the pins<br>- Most Expensive |
| PIC18F27Q10-I/SS SSOP<br>![Image](https://github.com/user-attachments/assets/5fc13709-1fcc-4bf5-b8de-9e213ad720b4)<br>$1.02<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F27Q10) | - Larger Operating Temperature Range<br>- Smaller Size<br>- 128KB Flash Size<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Less Pins |
| PIC18F26Q10-I/SS SSOP<br>![Image](https://github.com/user-attachments/assets/ae1ad637-cbbb-40eb-9a5e-984ea9c86cd8)<br>$0.91<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F26Q10) | - Smaller Size<br>- Larger Operating Temperature<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Only 64KB Flash Size<br>- Less Pins |

Selected Part

PIC18F27Q10-I/SS SSOP was selected due to its optimal size for my use case, high flash size, and pins count. Its smaller in for factor so I can fit it neatly on the pcb. Also, the pins contain everything we need without all the extra pins on the larger models. See the [PIC Project Demo](#PIC-Project-Demo) for more information about this chip and what pins I used.

## PIC Project Demo

![Image](https://github.com/user-attachments/assets/347ae521-e0a8-4c0f-9ddc-49590972ea65)

![Image](https://github.com/user-attachments/assets/fa33effc-904e-42d7-9f16-b8a310933e59)

These show the MCC configuration and and pin selections in mplab x. I have UART for the esp32 chip communication, ADC for the gyroscope, and I2C_Host for controlling the gyroscope and actuator. I may need to use I2C_Client instead of host but I believe host is the proper selection so I can read and write to and from the devices.

The pins selected were the default pins form MCC, however I did check several other pins to make sure I had multiple options and there are several other options for each component. The pin selection will be finalized later based on the pcb size and other components on it.

There are no errors in the MCC notifications. They only suggested I enable global and peripheral interrupts because some components are interrupt driven, so I enabled in in the code with the following lines.
```
INTERRUPT_GlobalInterruptEnable(); //Enable Global Interrupts
INTERRUPT_PeripheralInterruptEnable(); //Enable Peripheral Interrupts
```

## Power Budget

### Version 1

| **All Major Components** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|---|---|---|---|---|---|
|  | Microcontroller | PIC18F27Q10 | 1.8 - 5.5 | 1 | 250 |
|  | ESP32 Controller | ESP32-S3-WROOM-1-N4 | 3.3 - 3.6 | 1 | 355 |
| **9V Power Rail** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|  | N/A | N/A | N/A | N/A | N/A |
| **3.3V Power Rail** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|  | Microcontroller | PIC18F27Q10 | 1.8 - 5.5 | 1 | 250 |
|  | ESP32 Controller | ESP32-S3-WROOM-1-N4 | 3.3 - 3.6 | 1 | 355 |
| **External Power Source** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Current Supplied (mAh)** |
|  | Battery | B0B248DSFG | 9V | 1 | 1300 |
| **Battery Life** | **Parts Required Current** | **Battery Current (mAh)** | **Lowest Runtime (hh:mm)** |  |  |
|  | 605 | 1300 | 02:09 |  |  |
