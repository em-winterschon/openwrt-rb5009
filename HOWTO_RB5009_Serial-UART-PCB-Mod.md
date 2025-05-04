# A Quick Summary for Enabling UART Serial on the RB5009UG

This device does not come with a RJ45 or DB9 serial console connection by default, much to the dismay of many users and owners. However, there is a UART header on the PCB which can be connected to if one is adventurous and really wants that serial console (who doesn't?)

## Opening the case
- https://openwrt.org/toh/mikrotik/rb5009ug_s_in#opening_the_case

Just remove 8 screws from bottom side. Hinge up the top plastic. PCB is held to the aluminum backplane with thermal paste and a thin heatsink distance plate for the SoC and switch. There are also two thermal pads (3mm thick) under the SFP case and under some psu chip above the SFP, the pads will hold back with some force some when lifting the PCB from the backplane.

### Serial UART
→ [port.serial](https://openwrt.org/docs/techref/hardware/port.serial) general information about the serial port, serial port cable, etc.

There is a MikroTik SPI/UART combination 10-pin header (pin spacing=2.0mm) and the pinout is as seen from top side:

```
   GND Vcc  Rx  ?  GND
   #--------------------#
   |.-. .-. .-. .-. .-. |
   |'-' '-' '-' '-' '-' |
   |.-. .-. .-. .-. .-. |
   |'-' '-' '-' '-' '-' |
   #--------------------#
   CLK  DO /CS  Tx  DI
```

### Serial Connection Parameters
- MikroTik RB5009UG+S+IN: 115200,8N1

### Connections the UART Headers
This uses the typical "reverse Tx/Rx" style when connecting a bare-lead or Dupont header style serial device to the UART connectors.

- Ground to GND pin
- Tx Lead to Tx header
- Rx Lead to Rx header

If you are going to wire up a RJ45 console jack for the side of the case (standard method on MikroTik L009UiGS), then follow these instructions:
- https://help.mikrotik.com/docs/spaces/ROS/pages/328139/Serial+Console#SerialConsole-RJ45TypeSerialPort


Note: the other pins are used for SPI connections, and therefore not needed for our purposs.

### Doc Sources
- https://openwrt.org/toh/mikrotik/rb5009ug_s_in
- https://help.mikrotik.com/docs/spaces/ROS/pages/328139/Serial+Console
- https://openwrt.org/toh/mikrotik/common
- https://forum.openwrt.org/t/add-support-for-mikrotik-rb5009ug/104391/
