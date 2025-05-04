---
title: Schematic
---

## Schematic

![Individual System Design-1](https://github.com/user-attachments/assets/2303e1e2-b90d-433c-a193-fd5af2fd80b1)

[Individual System Design.pdf](https://github.com/user-attachments/files/19640118/Individual.System.Design.pdf)

[Individual System Design (4-7-2025 3-59-36 PM).zip](https://github.com/user-attachments/files/19640113/Individual.System.Design.4-7-2025.3-59-36.PM.zip)

[Components.zip](https://github.com/user-attachments/files/19599134/Components.-.03.04.25.-.23.20.zip)

[Verification Code.zip](https://github.com/user-attachments/files/19640190/Checkoff.Code.zip)

## Desision Making Process

My part of the project is managing the MQTT, so all I need hardware wise is to be able to handle other teamates UART messages to be able to program the microcontroller. This board handles those tasks very well.

## 2.0 Discussion

For a Version 2.0 of our design, our main goals would be improving battery life and overall hardware efficiency. In the current design, the system relies on a relatively large battery, which adds bulk and limits runtime. Plus this battery doesnt provide the best battery life. Switching to a higher-capacity LiPo battery would extend battery life while reducing weight. Additionally, choosing a more compact microcontroller with less power consumption would further reduce the drain on the battery while still keeping performance consistent. Plus not using uart would save battery life. We’d also reduce the total number of components by reducing part sizes and removing unnecessary features. This not only simplifies the schematic and improves power efficiency, but also makes the board smaller and easier to fit into the device. Using smaller surface-mount parts would help shrink the overall footprint even more. Finally, we’d adjust the layout to lower the center of gravity. In the current design, heavier components sit higher on the structure, making it less stable during movement or testing. Placing the battery and other dense parts closer to the base would improve balance and stability of the top. Together, these changes would make Version 2.0 lighter, longer-lasting, and more stable, without sacrificing core functionality.
