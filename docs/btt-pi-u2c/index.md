# BigTreeTech PI v1.2 + U2C Module v1.0

!!! success "This guide is tested with the following boards:"

    - BigTreeTech Pi v1.2
    - U2C Module v1.0

    This guide was verified on a BigTreeTech Pi v1.2 running [CB1 Debian11 Klipper](https://github.com/bigtreetech/CB1/releases/latest){:target="_blank"}

This is an instruction to set up a BigTreeTech Pi v1.2 with a U2C Module v1.0 with Klipper. The BigTreeTech Pi v1.2 is a
Raspberry Pi alternative with a H616 SoC. The U2C Module v1.0 is a USB-to-CAN adapter, which can be plugged on the top
of the BigTreeTech Pi v1.2 as a HAT.

![U2C Module v1.0](img/btt-pi-u2c-module.jpg)

This module is already preconfigured & flashed by BigTreeTech. Turn off the Pi, remove the power supply, and plug the
module on the Pi. After the Pi is fully booted again, CAN should be ready.

## Using U2C Module v1.0 on the minimal CB1 image

!!! warning "this is only needed if..."

    you use the minimal image from BigTreeTech. The minimal Image have nothing preinstalled from the the Klipper
    enviroment.

    - BigTreeTech Pi v1.2
    - U2C Module v1.0

    This guide was verified on a BigTreeTech Pi v1.2 running [CB1 Debian11 minimal](https://github.com/bigtreetech/CB1/releases/latest){:target="_blank"}

On the minimal image the CAN interface must be configured first. This can be done with the
`/etc/network/interfaces.d/can0` file. Follow the steps below to set them up.

```bash
# open file with nano
sudo nano /etc/network/interfaces.d/can0
```

``` title="/etc/network/interfaces.d/can0"
allow-hotplug can0
iface can0 can static
    bitrate 500000
    up ifconfig $IFACE txqueuelen 128
```

To save and close the nano editor:  
`ctrl+s` => save file  
`ctrl+x` => close editor

After a reboot, the can interface should be ready.