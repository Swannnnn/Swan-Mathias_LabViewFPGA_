
- [LabView FPGA MyRio STEVAL-MKI172V1](#labview-fpga-myrio-steval-mki172v1)
- [Hardware Specifications](#hardware-specifications)
- [Wiring](#wiring)
- [How it works ?](#how-it-works-)


# LabView FPGA MyRio STEVAL-MKI172V1

The goal of this project is to use LSM303AGR chip embedded on STEVAL-MKI172V1 board on MyRio dev evaluation board.

All project is coded in graphic FPGA on labview.

# Hardware Specifications

The chip is capable of communicating via several protocols, such as I2C or SPI, we chose to use SPI because it seemed easier.

We have used the logical analyzer of VirtualBench to catch all signals and try to understand what was going on.

# Wiring

CS <-> ConnectorC/DIO4
SCL <-> ConnectorC/DIO5
SDA <-> ConnectorC/DIO6
VDD <-> 3.3V
GND <-> GND

# How it works ?




![My Image](img/bg.png)


