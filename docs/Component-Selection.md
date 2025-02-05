---
title: Component Selection
---

## Microcontroller
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| PIC18F47Q10-I/MP QFN<br>![Image](https://github.com/user-attachments/assets/4d6ef272-cb16-48e7-baa7-fd9f01511f8c)<br>$1.25<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F47Q10#product-purchase) | - More Pins<br>- 128KB Flash Size | - Slightly Larger Size<br>- Don't need all the pins<br>- Most Expensive |
| PIC18F27Q10-E/STX VQFN<br>![Image](https://github.com/user-attachments/assets/7a774841-0833-4dea-96c8-2bcb2ab06e65)<br>$1.08<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F27Q10) | - Larger Operating Temperature Range<br>- Smaller Size<br>- 128KB Flash Size<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Less Pins |
| PIC18F26Q10-E/STX VQFN<br>![Image](https://github.com/user-attachments/assets/6ce242af-c02b-4c2b-9962-acd5107c7d26)<br>$0.96<br>[Product Page](https://www.microchip.com/en-us/product/PIC18F26Q10) | - Smaller Size<br>- Larger Operating Temperature<br>- E/STX are better designed for embeded systems<br>- Less Expensive | - Only 64KB Flash Size<br>- Less Pins |

Selected Part

PIC18F27Q10-E/STX VQFN

## ESP32
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| ESP32-C3<br>![Image](https://github.com/user-attachments/assets/8d6c4125-fae5-4819-b6b3-0283b21b2964)<br>$1.00<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-C3/14115593?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) |  |  |
| ESP32-WROOM-32E<br>![Image](https://github.com/user-attachments/assets/c1877004-1b2b-4a44-b05f-48c2bbfa9678)<br>$2.88<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-WROOM-32E-N8R2/16733126?gQT=2) |  |  |
| ESP32-S3<br>![Image](https://github.com/user-attachments/assets/0f992329-f761-43f9-8f02-2ab5bf204e94)<br>$1.50<br>[Product Page](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-D0WD-V3/11657616?&utm_adgroup=&utm_term=&utm_content=&gad_source=1) |  |  |

Selected Part

ESP32-WROOM-32E was recommended by the instructor due to its built in antenna and ease of use compared to the other options. It is larger that I would like but it does the job so I can work around its size.

## Switching 3.3V Regulator
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| MAX763AESA+<br>![Image](https://github.com/user-attachments/assets/9ffbad12-9ff0-45da-8fb7-31ee5920eac3)<br>$10.00<br>[Product Page](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/MAX763AESA/1513233) | - Easy to solder | - Very Expensive<br>- Lowest input voltage at 11V<br>- Only 500mA current output |
| LTC3621EMS8E-3.3#PBF<br>![Image](https://github.com/user-attachments/assets/79b94fa0-26db-4533-ac2b-3b30e231429f)<br>$8.77<br>[Product Page](https://www.digikey.com/en/products/detail/analog-devices-inc/LTC3621EMS8E-3-3-PBF/4840601) | - Wide operating temp range<br>- Up to 17V input<br>- 1A Output Current  | - Very Expensive<br>- Datasheet was confusing<br>- Requires soldering under part |
| TPS62162DSGR<br>![Image](https://github.com/user-attachments/assets/28ce2516-d906-4d43-8702-c3ae56931a57)<br>$1.38<br>[Product Page](https://www.digikey.com/en/products/detail/texas-instruments/TPS62162DSGR/2833447) | - Better priced than the other options<br>- Useful datasheet<br>- Up to 17V input<br>- 1A Output Current | - Requires soldering under part<br>- Seems slightly more difficult to solder |

Selected Part

TPS62162DSGR is the best priced option and meets all of my requirements. I plan on using a 9V 1A battery so this part allows me to get the most performance out of that and allows the parts to get all the volts and current they need. It also shouldnt overheat due to 9V being well under its 17V max input.

## Power Supply
| **Component** | **Pros** | **Cons** |
|---------------|----------|----------|
| HW 9V 1000mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/1b58af53-ec01-4d38-9ed1-03f749cc9a79)<br>$9.99<br>[Product Page](https://www.amazon.com/HW-Rechargeable-Batteries-Micro-USB-Indicator/dp/B0B9G9RQG3?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=AI0WONWMNF2H6&gPromoCode=sns_us_en_5_2023Q4&gQT=1) |  |  |
| LCLEBM 9V 1300mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/3389944e-e1bd-4a68-a7e6-118b94958817)<br>$11.98<br>[Product Page](https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A2WEVNKRB72JGE&gQT=1) |  |  |
| Hovxjzk 9V 1200mah Rechargeable Battery<br>![Image](https://github.com/user-attachments/assets/45db0a1f-e4d1-4242-8759-1bfeeb711ef6)<br>$12.90<br>[Product Page](https://www.amazon.com/Rechargeable-Battery-Capacity-1200mAh-Batteries/dp/B0BN3B16B2?th=1) |  |  |

Selected Part

LCLEBM 9V 1300mah
