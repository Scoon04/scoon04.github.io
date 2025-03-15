---
title: API
---

## Message Types Breakdown

### Motor Direction (Type 1)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | motorDir_pref | motorDir_pref | motorDir_sender | motorDir_receiver | motorDir_data | motorDir_data | motorDir_suf | motorDir_suf |
| Variable Type | uint16_t | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t | uint16_t | uint16_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 65535 | 65535 | 255 | 255 | 65535 | 65535 | 65535 | 65535 |
| Example Value | 100 | 10001 | 205 | 220 | 2886 | 17025 | 2040 | 2001 |

### Rotational Velocity (Type 3)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|---|---|---|---|---|---|---|---|---|
| Variable Name | rotVel_pref | rotVel_pref | rotVel_sender | rotVel_receiver | rotVel_data | rotVel_data | rotVel_suf | rotVel_suf |
| Variable Type | uint16_t | uint16_t | uint8_t | uint8_t | uint16_t | uint16_t | uint16_t | uint16_t |
| Min Value | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Max Value | 65535 | 65535 | 255 | 255 | 65535 | 65535 | 65535 | 65535 |
| Example Value | 625 | 305 | 253 | 164 | 53244 | 27784 | 7357 | 21346 |
