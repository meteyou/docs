# BigTreeTech EBB

This is an instruction to set up the BTT EBB36, EBB42 and EBB SB2209/2240 with Klipper via CANBUS.

!!! success "This guide is tested with the following boards:"

    - BTT EBB36 & 42 v1.1
    - BTT EBB36 & 42 v1.2
    - BTT EBB SB2209/2240 v1.0

    This guide was verified on a Pi running [MainsailOS](https://github.com/mainsail-crew/MainsailOS){:target="_blank"}

!!! warning "This guide will not work with the following boards:"

    - BTT EBB36 & 42 v1.0

    These boards have a different MCU.

## EBB36 & 42 v1.1 & v1.2

- [official Repository for the EBB36 v1.1 & v1.2](https://github.com/bigtreetech/EBB/tree/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB36%20CAN%20V1.1){:target="_blank"}
    - [Schematic](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB36%20CAN%20V1.1/Hardware/BIGTREETECH%20EBB36%20CAN%20V1.1-SCH.pdf){:target="_blank"}
    - [Size](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB36%20CAN%20V1.1/Hardware/BIGTREETECH%20EBB36%20CAN%20V1.1-SIZE.pdf){:target="_blank"}
    - [User Manual](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB36%20CAN%20V1.1/BIGTREETECH%20EBB36%20CAN%20V1.1%20User%20Manual.pdf){:target="_blank"}
- [official Repository for the EBB42 v1.1 & v1.2](https://github.com/bigtreetech/EBB/tree/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB42%20CAN%20V1.1){:target="_blank"}
    - [Sample config](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/sample-bigtreetech-ebb-sb-canbus-v1.0.cfg){:target="_blank"}
    - [Schematic](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB42%20CAN%20V1.1/Hardware/BIGTREETECH%20EBB42%20CAN%20V1.1-SCH.pdf){:target="_blank"}
    - [Size](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB42%20CAN%20V1.1/Hardware/BIGTREETECH%20EBB42%20CAN%20V1.1-SIZE.pdf){:target="_blank"}
    - [User Manual](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/EBB42%20CAN%20V1.1/BIGTREETECH%20EBB42%20CAN%20V1.1%20User%20Manual.pdf){:target="_blank"}
- [Sample config v1.1](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/sample-bigtreetech-ebb-canbus-v1.1.cfg){:target="_blank"}
- [Sample config v1.2](https://github.com/bigtreetech/EBB/blob/master/EBB%20CAN%20V1.1%20(STM32G0B1)/sample-bigtreetech-ebb-canbus-v1.2.cfg){:target="_blank"}

### Hardware

- **MCU:** ARM Cortex-M0+ STM32G0B1CBT6 64MHz whit FDCAN bus
- **Stepper Dirver:** Onboard TMC2209 in UART mode, UART address: 00, Rsense: 0.11R
- **Onboard Accelerometer Sensor:** ADXL345
- **Onboard Temperature IC:** Max31865 Select 2 / 4 lines PT100 / PT1000 by DIP switch (no Max31865 verson have not this feature)
- **Input Voltage:** DC12V-DC24V 6A
- **Logic Voltage:** DC 3.3V
- **Heating Interface:** Hotend (E0), maximum output current: 5A
- **Fan Interfaces:** two CNC fans (FAN0, FAN1)
- **Maximum Output Current of Fan Interface:** 1A, Peak Value 1.5A
- **Expansion Interfaces:** EndStop, I2C, Probe, RGB, PT100/PT1000, USB interface, CAN Interface
- **Temperature Sensor Interface Optional:** 1 Channel 100K NTC or PT1000(TH0), 1 Channel PT100/PT1000
- **USB Communication Interface:** USB-Type-C
- **DC 5V Maximum Output Current:** 1A

### Pinout EBB36 v1.1 & v1.2
![Pinout EBB36 v1.1 & v1.](img/pinout-ebb36-v1.1-v1.2.png)

### Pinout EBB42 v1.1 & v1.2
![Pinout EBB42 v1.1 & v1.2](img/pinout-ebb42-v1.1-v1.2.png)

## EBB SB2209/2240 v1.0

- [official Repository for the EBB SB2209/2240 v1.0](https://github.com/bigtreetech/EBB/tree/master/EBB%20SB2240_2209%20CAN){:target="_blank"}
   - [Sample config](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/sample-bigtreetech-ebb-sb-canbus-v1.0.cfg){:target="_blank"}
   - [Schematic EBB SB2209](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2209/Hardware/BIGTREETECH%20EBB%20SB2209%20CAN%20V1.0_SCH.pdf){:target="_blank"}
   - [Size EBB SB2209 Mainboard](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2209/Hardware/BIGTREETECHEBB%20SB2209%20CAN%20V1.0_SIZE.pdf){:target="_blank"}
   - [Size EBB SB2209 Subboard](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2209/Hardware/BIGTREETECH%20EBB%20SB0000%20CAN%20V1.0_size.pdf){:target="_blank"}
   - [Schematic EBB SB2240](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2240/Hardware/BIGTREETECH%20EBB%20SB2240%20CAN%20%20V1.0_SCH.pdf){:target="_blank"}
   - [Size EBB SB2240 Mainboard](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2240/Hardware/BIGTREETECH%20EBB%20SB2240%20CAN%20%20V1.0_SIZE.pdf){:target="_blank"}
   - [Size EBB SB2240 Subboard](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/SB2240/Hardware/BIGTREETECH%20EBB%20SB0000%20CAN%20V1.0_size.pdf){:target="_blank"}
   - [User Manual](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/Build%20Guide/EBB%20SB2240%202209%20CAN%20v1.0%20Build%20Guide.pdf){:target="_blank"}

### Hardware

- **MCU:** ARM Cortex-M0+ STM32G0B1CBT6 64MHz whit FDCAN bus
- **Stepper Dirver:**

    - **TMC2209 Version:** Onboard TMC2209 in UART mode, UART address: 00, Rsense: 0.11R
    - **TMC2240 Version:** Onboard TMC2240 in SPI mode
  
- **Onboard Accelerometer Sensor:** ADXL345
- **Onboard Temperature IC:** Max31865 Select 2 / 4 lines PT100 / PT1000 by DIP switch
- **Input Voltage:** DC12V-DC24V 9A
- **Logic Voltage:** DC 3.3V
- **Heating Interface:** Hotend (E0), maximum output current: 5A
- **Fan Interfaces:**

    - 2 x CNC fans (FAN1, FAN2)
    - 1 x 4-wire fan (4W_FAN)
  
- **Maximum Output Current of Fan Interface:** 1A, Peak Value 1.5A
- **Expansion Interfaces:** EndStop, Bltouch, Proximity(NPN & PNP), RGB, PT100/PT1000, USB, CAN, SPI
- **Temperature Sensor Interface Optional:** 1 Channel 100K NTC or PT1000(TH0), 1 Channel PT100/PT1000 (Max31865)
- **USB Communication Interface:** USB-Type-C
- **DC 5V Maximum Output Current:** 1A

### Pinout EBB SB2209 v1.0
![Pinout EBB SB2209 v1.0](img/pinout-ebb-sb2209-v1.0.png)

### Pinout EBB SB2240 v1.0
![Pinout EBB SB2240 v1.0](img/pinout-ebb-sb2240-v1.0.png)
