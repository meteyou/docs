# BigTreeTech PI v1.2 + U2C Module v1.0

This is an instruction to set up a BigTreeTech Pi v1.2 with a U2C Module v1.0 with Klipper. The BigTreeTech Pi v1.2 is a
Raspberry Pi alternative with a H616 SoC. The U2C Module v1.0 is a USB-to-CAN adapter, which can be plugged on the top
of the BigTreeTech Pi v1.2 as a HAT.

!!! success "This guide is tested with the following boards:"

    - BigTreeTech PI v1.2 + U2C Module v1.0

    This guide was verified on a BigTreeTech PI running [BTT-CB1 v2.3.2](https://github.com/bigtreetech/CB1){:target="_blank"}

There are multiple solutions to run the U2C with Klipper:

- [CandleLight_FW (BTT fork) (recommended)](candlelight.md)
- [Klipper USB-to-CAN](klipper-usb-to-can.md)

The straightforward variant to use the U2C is the candlelight firmware. With this, very little has to be configured, and
you don't have to update it with Klipper MCU updates. With the U2C, there are few advantages through the Klipper
firmware since no freely assignable pins are available on the board.

### Links

- [official Repository for the U2C](https://github.com/bigtreetech/u2c){:target="_blank"}
    - [Schematic v1.1](https://github.com/bigtreetech/U2C/blob/master/BIGTREETECH%20U2C%20V1.1.pdf){:target="_blank"}
      (this is the schematic for v1.1, but it is also valid for v2.x)
    - [User Manual](https://github.com/bigtreetech/U2C/blob/master/BIGTREETECH%20U2C%20V1.0%26V1.1%20User%20Manual.pdf){:target="_blank"}
      (this is the guide for v1.x, but it is also valid for v2.x)

### Pinout
![Pinout from the U2C v2.x](img/pinout-u2c-v2.x.png)