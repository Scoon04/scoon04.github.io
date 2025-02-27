---
title: Schematic
---

## Schematic

![Image](https://github.com/user-attachments/assets/a09aff7a-e1a4-4753-94e4-5c6dad9dcbe7)

[Individual System Design.pdf](https://github.com/user-attachments/files/18999858/Individual.System.Design.pdf)

[Individual System Design (2-26-2025 5-53-55 PM).zip](https://github.com/user-attachments/files/18999859/Individual.System.Design.2-26-2025.5-53-55.PM.zip)

This schematic is simple electrically. The main focus of this system is to host UART communication through the other 2 systems and to communicate wirelessly with the HMI through MQTT server. This schematic doesnt show much of its functionallity becuase its functionallity is code and server based, but it does show the pins that will be used to communitate with the other PCBs and how power will be distributed to other boards. The 9V power rail comes from the barrel jack and into the pin out so it can go to other boards, and the RX and TX come in and out of the board through the in and out connectors.

## BOM

| Part Name | Unit Quantity | Cost per Unit (Prototype) | Total Prototype Cost | Cost per Unit (Production) | Total Production Cost | Manufacturer | Manufacturer Part # | Vendor Link | Datasheet Link | Supplier | Supplier Part # | # Ordered | Date Ordered | # Recieved | Surplus | Designator |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0.1uF Ceramic | 2 | $0.11 | $0.22 | $0.11 | $0.22 | YAGEO | CC1206KRX7R8BB104 | https://www.digikey.com/en/products/detail/yageo/CC1206KRX7R8BB104/5884627 | https://www.yageo.com/upload/media/product/productsearch/datasheet/mlcc/UPY-GPHC_X7R_6.3V-to-250V_24.pdf | DigiKey | 311-3564-2-ND | 4 | 2/28 |  | -4 | C1, C4 |
| 2.2uF Ceramic | 1 | $0.18 | $0.18 | $0.18 | $0.18 | Samsung Electro-Mechanics | CL31B225KBHNNNE | https://www.digikey.com/en/products/detail/samsung-electro-mechanics/CL31B225KBHNNNE/3886949 | https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/503/CL31B225KBHNNNE_Character.pdf | DigiKey | 1276-1291-2-ND | 3 | 2/28 |  | -3 | C2 |
| 10uF Ceramic | 1 | $0.15 | $0.15 | $0.15 | $0.15 | Samsung Electro-Mechanics | CL31B106KAHNNNE | https://www.digikey.com/en/products/detail/samsung-electro-mechanics/CL31B106KAHNNNE/3887462 | https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/658/CL31B106KAHNNNE_Spec.pdf | DigiKey | 1276-1804-2-ND | 3 | 2/28 |  | -3 | C3 |
| 100ohm | 1 | $0.17 | $0.17 | $0.17 | $0.17 | Panasonic Electronic Components | ERJ-8ENF1000V | https://www.digikey.com/en/products/detail/panasonic-electronic-components/ERJ-8ENF1000V/88671 | https://industrial.panasonic.com/cdbs/www-data/pdf/RDA0000/AOA0000C304.pdf | DigiKey | P100FTR-ND | 3 | 2/28 |  | -3 | R5 |
| 10k Resistor | 3 | $0.10 | $0.30 | $0.10 | $0.30 | YAGEO | RC1206FR-0710KL | https://www.digikey.com/en/products/detail/yageo/RC1206FR-0710KL/728483 | https://www.yageo.com/upload/media/product/products/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf | DigiKey | 311-10.0KFRCT-ND | 5 | 2/28 |  | -5 | R3, R4, R6 |
| 22.1k Resistor | 1 | $0.10 | $0.10 | $0.10 | $0.10 | Stackpole Electronics Inc | RNCP1206FTD22K1 | https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RNCP1206FTD22K1/2240381 | https://www.seielect.com/catalog/sei-rncp.pdf | DigiKey | RNCP1206FTD22K1CT-ND | 3 | 2/28 |  | -3 | R2 |
| 51k Resistor | 1 | $0.10 | $0.10 | $0.10 | $0.10 | Stackpole Electronics Inc | RMCF1206JT51K0 | https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RMCF1206JT51K0/1753857 | https://www.seielect.com/catalog/sei-rmcf_rmcp.pdf | DigiKey | RMCF1206JT51K0CT-ND | 3 | 2/28 |  | -3 | R1 |
| 3.3uH Inductor | 1 | $0.24 | $0.24 | $0.24 | $0.24 | Murata Electronics | LQM31PN3R3M00L | https://www.digikey.com/en/products/detail/murata-electronics/LQM31PN3R3M00L/2594619 | https://search.murata.co.jp/Ceramy/image/img/P02/JELF243B-0013.pdf | DigiKey | 490-6705-2-ND | 3 | 2/28 |  | -3 | L1 |
| LED | 1 | $0.32 | $0.32 | $0.32 | $0.32 | Dialight | 5988260107F | https://www.digikey.com/en/products/detail/dialight/5988260107F/1291286 | https://s3-us-west-2.amazonaws.com/catsy.557/Dialight_CBI_data_598-1206_Apr2018.pdf | DigiKey | 350-2052-2-ND | 3 | 2/28 |  | -3 | D1 |
| 1.5A Fuse | 1 | $0.75 | $0.75 | $0.75 | $0.75 | Littelfuse Inc. | 022501.5MXP | https://www.digikey.com/en/products/detail/littelfuse-inc/022501.5MXP/777788?&utm_adgroup=&utm_term=&utm_content=&gad_source=1 | https://www.littelfuse.com/assetdocs/littelfuse-fuse-224-225-datasheet?assetguid=26e6ad94-5fb7-4bad-acf6-da1c91c16d87 | DigiKey | F4663-ND | 3 | 2/28 |  | -3 | F1 |
| Fuse Holder | 1 | $0.81 | $0.81 | $0.81 | $0.81 | Keystone Electronics | 4628 | https://www.digikey.com/en/products/detail/keystone-electronics/4628/2137316?&utm_adgroup=&utm_term=&utm_content=&gad_source=1 | https://www.keyelco.com/userAssets/file/M65p44.pdf | DigiKey | 36-4628-ND | 2 | 2/28 |  | -2 |  |
| Barrel Jack | 1 | $0.60 | $0.60 | $0.60 | $0.60 | Same Sky (Formerly CUI Devices) | PJ-037A | https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-037A/1644545 | https://www.cuidevices.com/product/resource/pj-037a.pdf | DigiKey | CP-037A-ND | 2 | 2/28 |  | -2 | J2 |
| Ribbon Connectors | 2 | $0.97 | $1.94 | $0.97 | $1.94 | Würth Elektronik | 61200821621 | https://www.digikey.com/en/products/detail/w-rth-elektronik/61200821621/4846916?&utm_adgroup=&utm_term=&utm_content=&gad_source=1 | https://www.we-online.com/components/products/datasheet/61200821621.pdf | DigiKey | 732-5395-ND | 3 | 2/28 |  | -3 | P2 |
| Pushbutton | 3 | $1.00 | $3.00 | $1.00 | $3.00 | Omron Electronics Inc-EMC Div | B3U-1000P | https://www.digikey.com/en/products/detail/omron-electronics-inc-emc-div/B3U-1000P/1534338 | https://omronfs.omron.com/en_US/ecb/products/pdf/en-b3u.pdf | DigiKey | SW1020TR-ND | 5 | 2/28 |  | -5 | S1, S2, S3 |
| 3.3V Regulator | 1 | $1.47 | $1.47 | $1.47 | $1.47 | Texas Instruments | LMR50410Y3FQDBVRQ1 | https://www.digikey.com/en/products/detail/texas-instruments/LMR50410Y3FQDBVRQ1/13562985 | https://www.ti.com/lit/ds/symlink/lmr50410-q1.pdf | DigiKey | 296-LMR50410Y3FQDBVRQ1TR-ND | 3 | 2/28 |  | -3 | U1 |
| Micro USB Port | 1 | $0.77 | $0.77 | $0.77 | $0.77 | GCT | USB3131-30-0230-A | https://www.digikey.com/en/products/detail/gct/USB3131-30-0230-A/9859642 | https://gct.co/files/specs/usb3131-spec.pdf | DigiKey | 2073-USB3131-30-0230-ATR-ND | 0 | 2/28 |  | 0 | J1 |
| ESP32-S3-WROOM-1-N4 | 1 | $5.06 | $5.06 | $5.06 | $5.06 | Espressif Systems | ESP32-S3-WROOM-1-N4 | https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639 | https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf | DigiKey | 1965-ESP32-S3-WROOM-1-N4TR-ND | 0 | 2/28 |  | 0 | U2 |
| Ribbon Cable | 1 | $3.85 | $3.85 | $3.85 | $3.85 | Marvic International, Inc. | 530182808045 | https://www.amazon.com/gp/product/B07DFBPZLJ?smid=A64W1E1ZZHST0 | N/A | Amazon | B07DFBPZLJ | 1 | 2/28 |  | -1 |  |
| Battery | 1 | $11.98 | $11.98 | $11.98 | $11.98 | ShenZhen Maxpower Technology | LCLEBM | https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A2WEVNKRB72JGE&gQT=1 | N/A | Amazon | B0B248DSFG | 1 | 2/28 |  | -1 |  |
