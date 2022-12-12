
- [LabView FPGA MyRio STEVAL-MKI172V1](#labview-fpga-myrio-steval-mki172v1)
- [Hardware Specifications](#hardware-specifications)
- [Wiring](#wiring)
- [How it works ?](#how-it-works-)
- [Contributors](#contributors)


# LabView FPGA MyRio STEVAL-MKI172V1

The goal of this project is to use LSM303AGR chip embedded on STEVAL-MKI172V1 board on MyRio dev evaluation board.
All project is coded in graphic FPGA on labview.

# Hardware Specifications

The chip is capable of communicating via several protocols, such as I2C or SPI, we chose to use SPI because it seemed easier.
We have used the logical analyzer of VirtualBench to catch all signals and try to understand what was going on.

# Wiring

CS <-> ConnectorC/DIO4\
SCL <-> ConnectorC/DIO5\
SDA <-> ConnectorC/DIO6\
VDD <-> 3.3V\
GND <-> GND

# How it works ?

Our whole project runs in the vi main. It tells us what to do at each moment.

First, the chip must be initialized by giving it the command to switch to 3 wires mode. This is done with the SPI_SET_3W_Mode.vi. This vi will set the cs pin to low, then wait 100 µseconds, after which a loop is launched. In this loop, the clock signal is generated, with a modulo. After each clock stroke, we wait 200 µseconds, then we launch the VI SPI_Write_Protocol.vi. This VI has in parameter The address to send, the message to send, a boolean value to know if we change of state of clock. The vi will thus send the good boolean value according to the index of the loop.

In a second step, we send to the address who i am, and wait for its answer. The operation of the SPI_READ VI is similar to the previous one, the difference is that we don't write a message but wait for one, so the VI has a returned value. The operation is thus very similar.

The last step is the reading in loop of the desired value (acceleration of X).
To do this, we read the value every 100 ms with the SPI_READ vi.

We decided to use a loop in this project, instead of the countless flat sequence structures, because it seemed more elegant and it would be a challenge. 

Unfortunately, we didn't get a chance to test the final version of the project, but it should work just fine (the frames captured by the virtualbench are exactly like the technical data, so it should work just fine).

Thanks to this project and our amazing and wonderful teacher mr @nenel83, we learned a lot about using labview FPGA.

# Contributors

Swan boissay and Mathias Donzel\
![My Image](img/bg.png)


