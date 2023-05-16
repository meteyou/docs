# CandleLight_FW (U2C v1.x)

But the U2C v2.x has the STM32G0B1 that currently is not supported by the official CandleLight project. Therefore,
BigTreeTech created a fork of that project and added STM32G0B1 support.

Github: [github.com/bigtreetech/candleLight_fw/tree/stm32g0_support](https://github.com/bigtreetech/candleLight_fw/tree/stm32g0_support)

## Compile CandleLight_FW (budgetcan_fw)
```bash
# install requirements
sudo apt-get install cmake gcc-arm-none-eabi

cd ~
# clone git repo
git clone --depth=1 -b stm32g0_support https://github.com/bigtreetech/candleLight_fw
cd ~/candleLight_fw

# create cmake toolchain
mkdir build
cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=../cmake/gcc-arm-none-eabi-8-2019-q3-update.cmake

# compile firmware
make budgetcan_fw
```

## Flash CandleLight_FW (budgetcan_fw)
First, the adapter must boot in DFU mode. Please press the boot button and then connect the USB cable. With
`dfu-util -l`, you can check whether the adapter is booted in DFU mode. This should look like this:

If dfu-util can discover a board in DFU mode it should then look like this:
![dfu-util -l output](img/dfu-util_-l.svg)

If the BTT U2C has booted in DFU mode, you can flash it with this command:

```bash
make flash-budgetcan_fw
```

It should then look like this:
![flash candlelight](img/flash_candlelight.svg)

## Add can0 interface

Now you only have to create the interface in the OS. to do this, create the file `/etc/network/interfaces.d/can0` and
fill it with the following content.

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