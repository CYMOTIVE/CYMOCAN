# CYMOCAN USB-CAN Interface #

CYMOCAN is a low cost USB to CAN-FD (Controller Area Network - Flexible Data rate) interface.

Using the [CandleLight firmware](https://github.com/candle-usb/candleLight_fw) CYMOCAN can work with Windows(WCID USB) and Linux(SocketCAN over gs_usb).

## What is in this repository?

* Hardware files for the CYMOCAN board and [Debug edge](https://debug-edge.io/) breakout board

## Hardware
## CYMOCAN_G0
CYMOCAN_G0 has:
* 2 CAN-FD interfaces 
* USB
* SWD + UART (Over [Debug edge](https://debug-edge.io/))

![CYMOCAN_G0 Schematic](/images/CYMOCAN_G0_schematic.png)

CYMOCAN_G0 BOM
|Reference|Description|Quantity|
|:---|:---:|:---:|
| C1, C2 | 0603 1uF Capacitor | 2
| C3| 0603 0.1uF Capacitor | 1
| C4 | 0603 100nf Capacitor | 1
| C5 | 0603 4.7uF Capacitor | 1
| D1, D2, D3, D4, D5, D6 | 0603 LED | 6
| J1 | Molex 105450-0101 USB-C socket | 1
| J2, J3, J4, J7 | 01x02 Pin Header | 4
| J5, J8 | 3 Pin TerminalBlock Bornier 5.08mm | 2
| R1, R2 | 0603 5.1K Resistor | 2
| R3, R4 | 0603 10K Resistor | 2
| R5 | 0603 40K Resistor | 1
| R6, R7, R8, R9, R13 | 0603 220 Resistor | 5
| R10, R11 | 0603 120 Resistor | 2
| R12 | 0603 330 Resistor | 1
| SW1 | Push switch 6mm THT | 1
| U1 | AP2112K-3.3 LDO regulator| 1
| U2 | STM32G0B1CBT6 Microcontroller | 1
| U3, U5 | TJA1051T-3 CAN transceiver | 2
| U4 | USBLC6-2P6 USB ESD protection diodes| 1


![CYMOCAN_G0 ](/images/CYMOCAN_G0_layout.png)

![CYMOCAN_G0 ](/images/CYMOCAN_G0_preview.png)

## Debug edge breakout
You Do not need this in order to flash and use the CYMOCAN board.
This breakout is only necessary if you wish to debug the board during development. 

## Getting started with CYMOCAN ##
### Flashing the Board ###
After assembling the device follow the flashing instructions in the [CandleLight firmware](https://github.com/candle-usb/candleLight_fw) Repo.

For now use the PR https://github.com/candle-usb/candleLight_fw/pull/139 and the nucleo_g0b1re target.

### Linux ###
You will need to compile a kernel version 5.18 or above for GS_USB CAN-FD support.
The flags you must enable are:
* CAN
* CAN_GS_USB

After compiling and installing the Kernel the CYMOCAN will appear as a standard SocketCAN device.

To setup the device for classic CAN use the following commands
```
sudo ip link set can0 qlen 1000
sudo ip link set can0 up type can bitrate 500000
```
Subsitute can0 for the channel you are using.
Now you can use the device with any SocketCAN compatible software.

### Windows ###
TODO

