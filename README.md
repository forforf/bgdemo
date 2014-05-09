# BGDemo -- Hello World

Note: Project is Windows based

## Project notes:

### project.xml
* This line must be included if the BLED112 dongle is to be used. (I think it's licensing info)
	`<usb_main in="cdc.xml" />`

* My initial thought is to identify the device type in the out file
    `<image out="bled112.hex" />`
	
### hardware.xml
* Do NOT enable sleeposc in BLED112, it's not present. It is ok to enable in the BLE112 and BLE113
    `<sleeposc enable="false" ppm="30" />`
	
    <usb enable="false" />
* power is 0-15, Unclear whether BLED112 supports power (BLE112 and BLE113 0=-24dBm, 15=+3dBm)
  Do NOT change bias	
    <txpower power="15" bias="5" />
    
* Allows for the system to slow the system clock down to preserve power. User Guide Warning:
  UART and PWM interfaces use system clock for timings. If the system clock is slowed down the peripheral interface timings are invalid. This feature must only be enabled when peripherals requiring stable clock are not used.
  SPI Master sends clock signal with transmission which allows enabling the slow clock feature.  
	`<slow_clock enable="true" />`
