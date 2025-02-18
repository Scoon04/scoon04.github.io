---
title: Component Selection
---

## My Team Role

My role on my team is to send and recieve data to and from the HMI. I will recieve data from the gyroscope and send it to the HMI wirelessly with esp32. I will also recieve wireless data from the HMI and send it to the motor driver. I will also be responsible for recieving and translating gyroscope data to send to the motor driver if we decide to do that later on. Additionally, I will be making sure the regulated power is implimented properly, however im not sure if that will be on my board or another team members board for the final design.

## Microcontroller
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| PIC18F47Q10-I/PT TQFP<br>![Image](https://github.com/user-attachments/assets/6d7fc249-07ad-4904-bfbb-ba29c82f6786)<br>$1.22<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F47Q10#product-purchase) | - More Pins<br>- 128KB Flash Size | - Slightly Larger Size<br>- Don't need all the pins<br>- Most Expensive |
| PIC18F27Q10-I/SS SSOP<br>![Image](https://github.com/user-attachments/assets/5fc13709-1fcc-4bf5-b8de-9e213ad720b4)<br>$1.02<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F27Q10) | - Larger Operating Temperature Range<br>- Smaller Size<br>- 128KB Flash Size<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Less Pins |
| PIC18F26Q10-I/SS SSOP<br>![Image](https://github.com/user-attachments/assets/ae1ad637-cbbb-40eb-9a5e-984ea9c86cd8)<br>$0.91<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F26Q10) | - Smaller Size<br>- Larger Operating Temperature<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Only 64KB Flash Size<br>- Less Pins |

Selected Part

PIC18F27Q10-I/SS SSOP was selected due to its optimal size for my use case, high flash size, and pins count. Its smaller in for factor so I can fit it neatly on the pcb. Also, the pins contain everything we need without all the extra pins on the larger models. See the [PIC Project Demo](#PIC-Project-Demo) for more information about this chip and what pins I used.

## ESP32
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| ESP32-C3<br>![Image](https://github.com/user-attachments/assets/8d6c4125-fae5-4819-b6b3-0283b21b2964)<br>$1.00<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-C3/14115593?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) | - More Affordable<br>- Small Size | - Needs external antenna to opperate normally<br>- Extra components take up more space |
| ESP32-S3-WROOM-1-N4<br>![Image](https://github.com/user-attachments/assets/466d1162-997f-4f1b-a346-3a31fbbc5549)<br>$2.95<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) | - Recomended by Instructor<br>- Build in Antenna | - Larger in Size<br>- More expensive |
| ESP32-S3<br>![Image](https://github.com/user-attachments/assets/0f992329-f761-43f9-8f02-2ab5bf204e94)<br>$1.50<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-D0WD-V3/11657616?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) | - More Affordable<br>- Small Size | - Needs external antenna to opperate normally<br>- More of a hassle to work with |

Selected Part

ESP32-S3-WROOM-1-N4 was recommended by the instructor due to its built in antenna and ease of use compared to the other options. It is larger that I would like but it does the job without any major hassle so I can work around its size.

## Switching 3.3V Regulator
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| MAX763AESA+<br>![Image](https://github.com/user-attachments/assets/9ffbad12-9ff0-45da-8fb7-31ee5920eac3)<br>$10.00<br>[Product Page](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/MAX763AESA/1513233) | - Easy to solder | - Very Expensive<br>- Lowest input voltage at 11V<br>- Only 500mA current output |
| LTC3621EMS8E-3.3#PBF<br>![Image](https://github.com/user-attachments/assets/79b94fa0-26db-4533-ac2b-3b30e231429f)<br>$8.77<br>[Product Page](https://www.digikey.com/en/products/detail/analog-devices-inc/LTC3621EMS8E-3-3-PBF/4840601) | - Wide operating temp range<br>- Up to 17V input<br>- 1A Output Current  | - Very Expensive<br>- Datasheet was confusing<br>- Requires soldering under part |
| LMR50410Y3FQDBVRQ1<br>![Image](https://github.com/user-attachments/assets/27154629-ffba-48d2-8ea3-39eddf6070cc)<br>$1.47<br>[Product Page](https://www.digikey.com/en/products/detail/texas-instruments/LMR50410Y3FQDBVRQ1/13562985) | - Better priced than the other options<br>- Useful datasheet<br>- Up to 36V input<br>- 1A Output Current<br>- Higher Operating Temp Range | - Nothing stands out a being a con. This just seems like a better product overall for my use case |

Selected Part

LMR50410Y3FQDBVRQ1 is the best priced option and meets all of my requirements. I plan on using a 9V 1A battery so this part allows me to get the most performance out of that and allows the parts to get all the volts and current they need. It also shouldnt overheat due to 9V being well under its 36V max input, as well as it having a higher operating temp range than the other choices.

## Power Supply
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| HW 9V 1000mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/1b58af53-ec01-4d38-9ed1-03f749cc9a79)<br>$9.99<br>[Product Page](https://www.amazon.com/HW-Rechargeable-Batteries-Micro-USB-Indicator/dp/B0B9G9RQG3?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=AI0WONWMNF2H6&gPromoCode=sns_us_en_5_2023Q4&gQT=1) | - Cheapest Option<br>- Rechargable | - Lowest mah size<br> |
| LCLEBM 9V 1300mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/3389944e-e1bd-4a68-a7e6-118b94958817)<br>$11.98<br>[Product Page](https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A2WEVNKRB72JGE&gQT=1) | - Rechargable<br>- Larger mah size<br>- 2 Pack | - Slightly more expensive |
| Hovxjzk 9V 1200mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/45db0a1f-e4d1-4242-8759-1bfeeb711ef6)<br>$12.90<br>[Product Page](https://www.amazon.com/Rechargeable-Battery-Capacity-1200mAh-Batteries/dp/B0BN3B16B2?th=1) | - 2 Pack<br>- Larger mah size<br>- Rechargable | - Most expensive<br>- Long delivery time |

Selected Part

LCLEBM 9V 1300mah has a larger mah size so it will last a bit longer than the other options without having to recharging. It's also a great price for a 2 pack, and has a quick delivery time unlike one of the other options. It overall is slightly better than the other options because of its price, mah size, and delivery time.

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

## ESP32 Pinout Diagram

![Image](https://github.com/user-attachments/assets/c9f38d54-e26a-4491-99a1-08f9e845aa43)

My ESP32 module will only need the UART pins to give and recieve data from the PIC microcontroller. The reason its not doing more is becuase the class requirements need us to use at least one PIC and ESP32 controller. The HMI will have an EPS32 module controlling it, so if I only used the ESP32 module then the project wouldn't meet class requirements. The plan is to use MQTT to send data between ESP32 modules and then my module will use UART to give and recieve data from the local PIC controller.

## Power Budget

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
