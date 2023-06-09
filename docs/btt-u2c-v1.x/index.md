# BigTreeTech U2C v1.x

This is an instruction to set up the BTT U2C with Klipper. There are two possible variants. Use the board as a pure
CANBUS adapter (candlelight FW) or a Klipper USB-to-CAN adapter.

!!! success "This guide is tested with the following boards:"

    - BigTreeTech U2C v1.1

    This guide was verified on a Pi running [MainsailOS](https://github.com/mainsail-crew/MainsailOS){:target="_blank"}

There are multiple solutions to run the U2C with Klipper:

- [CandleLight_FW (recommended)](candlelight.md)
- [Klipper USB-to-CAN adapter](klipper-usb-to-can.md)

The straightforward variant to use the U2C is the candlelight firmware. With this, very little has to be configured, and
you don't have to update it with Klipper MCU updates. With the U2C, there are few advantages through the Klipper
firmware since no freely assignable pins are available on the board.

### Links

- [official Repository for the U2C v1.x](https://github.com/bigtreetech/u2c){:target="_blank"}
    - [Schematic v1.0](https://github.com/bigtreetech/U2C/blob/master/BIGTREETECH%20U2C%20V1.0.pdf){:target="_blank"}
    - [Schematic v1.1](https://github.com/bigtreetech/U2C/blob/master/BIGTREETECH%20U2C%20V1.1.pdf){:target="_blank"}
    - [User Manual](https://github.com/bigtreetech/U2C/blob/master/BIGTREETECH%20U2C%20V1.0%26V1.1%20User%20Manual.pdf){:target="_blank"}

### Pinout
![Pinout from the U2C v1.x](img/pinout-u2c-v1.x.png)