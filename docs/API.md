---
title: API
---

## Message Types Breakdown

### Motor Direction (Type 1)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | motorDir_pref1 | motorDir_pref2 | motorDir_sender | motorDir_receiver | motorDir_data1 | motorDir_data2 | motorDir_suf1 | motorDir_suf2 |
| Variable Type | uint8_t | uint8_t | uint8_t | uint8_t | uint16_t | uint16_t | uint8_t | uint8_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 255 | 255 | 255 | 255 | 65535 | 65535 | 255 | 255 |
| Example Value | 100 | 101 | 205 | 220 | 2886 | 17025 | 200 | 201 |

### Rotational Velocity (Type 3)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | rotVel_pref1 | rotVel_pref2 | rotVel_sender | rotVel_receiver | rotVel_data1 | rotVel_data2 | rotVel_suf1 | rotVel_suf2 |
| Variable Type | uint8_t | uint8_t | uint8_t | uint8_t | uint16_t | uint16_t | uint8_t | uint8_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 255 | 255 | 255 | 255 | 65535 | 65535 | 255 | 255 |
| Example Value | 25 | 205 | 253 | 164 | 53244 | 27784 | 237 | 21 |
