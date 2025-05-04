---
title: Component Selection
---

## My Team Role

My role on my team is to send and recieve data to and from the HMI through an MQTT server. I will recieve data from the gyroscope and send it to the HMI wirelessly with esp32. I will also recieve wireless data from the HMI and send it to the motor driver. Additionally, I will be making sure the power is implemented properly accross the other boards.

## Component Selection

### ESP32

| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| ESP32-C3<br>![Image](https://github.com/user-attachments/assets/8d6c4125-fae5-4819-b6b3-0283b21b2964)<br>$1.00<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-C3/14115593?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) | - More Affordable<br>- Small Size | - Needs external antenna to opperate normally<br>- Extra components take up more space<br>- Harder to solder |
| ESP32-S3-WROOM-1-N4<br>![Image](https://github.com/user-attachments/assets/466d1162-997f-4f1b-a346-3a31fbbc5549)<br>$2.95<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) | - Recomended by Instructor<br>- Build in Antenna<br>- Easier to solder | - Larger in Size<br>- More expensive |
| ESP32-S3<br>![Image](https://github.com/user-attachments/assets/0f992329-f761-43f9-8f02-2ab5bf204e94)<br>$1.50<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-D0WD-V3/11657616?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) | - More Affordable<br>- Small Size | - Needs external antenna to opperate normally<br>- More of a hassle to work with<br>- Harder to solder |

Selected Part

>ESP32-S3-WROOM-1-N4

This part was recommended by the instructor due to its built in antenna and ease of use compared to the other options. They also have it in stock as well so this will cut down on my overall budget. It is larger than I would like but it does the job without any major hassle so I can work around its size.

### Switching 3.3V Regulator

| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| LM2575D2T-3.3R4G<br>![image](https://github.com/user-attachments/assets/fea271f6-0a50-459a-a540-97bd2227866c)<br>$3.32<br>[Product Page](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688) | - Easy to solder<br>- Up to 40V input<br>- 1A Current Output | - Slightly more expensive |
| LTC3621EMS8E-3.3#PBF<br>![Image](https://github.com/user-attachments/assets/79b94fa0-26db-4533-ac2b-3b30e231429f)<br>$8.77<br>[Product Page](https://www.digikey.com/en/products/detail/analog-devices-inc/LTC3621EMS8E-3-3-PBF/4840601) | - Wide operating temp range<br>- Up to 17V input<br>- 1A Output Current  | - Very Expensive<br>- Datasheet was confusing<br>- Requires soldering under part |
| LMR50410Y3FQDBVRQ1<br>![Image](https://github.com/user-attachments/assets/27154629-ffba-48d2-8ea3-39eddf6070cc)<br>$1.47<br>[Product Page](https://www.digikey.com/en/products/detail/texas-instruments/LMR50410Y3FQDBVRQ1/13562985) | - Better priced than the other options<br>- Useful datasheet<br>- Up to 36V input<br>- 1A Output Current<br>- Higher Operating Temp Range | - Min input voltage is close to 5V input from the micro usb port so it may step down slightly below 3.3V |

Selected Part

>LM2575D2T-3.3R4G

This is my choice for the 2nd itteration of my board. My original choice was the LMR50410Y3FQDBVRQ1, but I was having issues with it overheating. This could have been becuase of its size and improper heat dissipation or just a bad batch of products. Whatever the cause was, I needed something reliable. This new choice is the surface mount version of the one we had in class, so I know it works. Dispite its slightly higher price, and larger size, this is the next best option.

### Power Supply

| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| HW 9V 1000mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/1b58af53-ec01-4d38-9ed1-03f749cc9a79)<br>$9.99<br>[Product Page](https://www.amazon.com/HW-Rechargeable-Batteries-Micro-USB-Indicator/dp/B0B9G9RQG3?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=AI0WONWMNF2H6&gPromoCode=sns_us_en_5_2023Q4&gQT=1) | - Cheapest Option<br>- Rechargable | - Lowest mah size<br> |
| LCLEBM 9V 1300mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/3389944e-e1bd-4a68-a7e6-118b94958817)<br>$11.98<br>[Product Page](https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A2WEVNKRB72JGE&gQT=1) | - Rechargable<br>- Larger mah size<br>- 2 Pack | - Slightly more expensive |
| Hovxjzk 9V 1200mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/45db0a1f-e4d1-4242-8759-1bfeeb711ef6)<br>$12.90<br>[Product Page](https://www.amazon.com/Rechargeable-Battery-Capacity-1200mAh-Batteries/dp/B0BN3B16B2?th=1) | - 2 Pack<br>- Larger mah size<br>- Rechargable | - Most expensive<br>- Long delivery time |

Selected Part

>LCLEBM 9V 1300mah

This part has a larger mah size so it will last a bit longer than the other options without having to recharging. It's also a great price for a 2 pack, and has a quick delivery time unlike one of the other options. It overall is slightly better than the other options because of its price, mah size, and delivery time.

### Minor Components

Any minor components I select must be no smaller than 1206 size, this is for an easier time soldering components. Some other minor components I need are pushbuttons for programming the ESP32, Fuses, and some debug items. These items aren't major so I havent done a component selection for them, but I do have a list of minor components on the Minor Components Page (located under the Resources Page) that I am constantly updating. You can also find a larger more detailed list of items on the [BOM Page](Bill-of-Materials.md).

## Final Major Component List

| **Component** | **Image** | **Link** |
|---------------|----------|----------|
| ESP32-S3-WROOM-1-N4 | ![Image](https://github.com/user-attachments/assets/466d1162-997f-4f1b-a346-3a31fbbc5549) | [Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) |
| LM2575D2T-3.3R4G | ![image](https://github.com/user-attachments/assets/fea271f6-0a50-459a-a540-97bd2227866c) | [Product Page](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688) |
| LCLEBM 9V 1300mah | ![Image](https://github.com/user-attachments/assets/3389944e-e1bd-4a68-a7e6-118b94958817) | [Product Page](https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A2WEVNKRB72JGE&gQT=1) |
| 9100 RPM Motor | ![image](https://github.com/user-attachments/assets/150b535b-7145-48b7-9938-523e9ada5008) | [Product Page](https://www.digikey.com/en/products/detail/adafruit-industries-llc/711/5353610?gQT=1) |

### Final Component Decision Making Process

The microcontroller and battery are the same parts ive had for the entire project. They provide the functionallity and battery life I need. The voltage regulator was switched do to issues with my previous one overheating. The motor was an addon made last minute for a more presentable project for the showcase. More descriptions about the project on the [Team Website](https://egr314-2025-s-309b.github.io/)

## ESP32 Pinout Diagram

>***Check [Schematic Page](Schematic.md) for most updated information in case this diagram hasent been updated***

![image](https://github.com/user-attachments/assets/ccfeed44-4e6a-496f-b7b8-8672e5cccd58)

My ESP32 pins will only use the RX and TX pins for the uart data stream and the D+ and D- for programming with a micro usb port. This will communicate wirelessly through a MQTT server to the HMI to share and collect more data, similar purpose to the uart stream but wireless. It will also communicate with a online user to do similar things that the in person user can do. See the [Process Diagram](https://egr314-2025-s-309b.github.io/Block-Process-Diagrams-Message-Structure/) on the team website for more info on this.

## Power Budget

The power budget on my board only needs to power the microcontroller. However, all 3 boards on the spinning top are going to use the same power do this isnt an accurate representation of the true battery life of the full project.

| **All Major Components** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|---|---|---|---|---|---|
|  | ESP32 Controller | ESP32-S3-WROOM-1-N4 | 3.3 - 3.6 | 1 | 355 |
| **9V Power Rail** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|  | Motor | 711 | 9 | 1 | 100 |
| **3.3V Power Rail** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Max Current (mA)** |
|  | ESP32 Controller | ESP32-S3-WROOM-1-N4 | 3.3 - 3.6 | 1 | 355 |
| **External Power Source** | **Component Name** | **Part Number** | **Supply Voltage Range** | **#** | **Current Supplied (mAh)** |
|  | Battery | B0B248DSFG | 9V | 1 | 1300 |
| **Battery Life** | **Parts Required Current** | **Battery Current (mAh)** | **Lowest Runtime (hh:mm)** |  |  |
|  | 355 | 1300 | 03:39 |  |  |
| **25% Safety Margin** | 756.25 | 1300 | 01:43 |  |  |

### Power Budget Explenation

This power budget allowed us to decide what battery to use. Considering our project is wireless, the battery life matters. This power budget showed us that a 1300 mAh battery (while not having the best battery life) would be enough for my system. And considering my teamates system will have its own power supply, this will be sufficient. The motor has a max stall current of 250mA, but this isnt practical as the motor wont be stalling all the time and it wont be running all the time so the battery life will be much better than shown.
