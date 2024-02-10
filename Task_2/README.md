# Task 2 - Extract the Firmware - (Hardware analysis, Datasheets)

Thanks to your efforts the USCG discovered the unknown object by trilaterating the geo and timestamp entries of their record with the correlating entries you provided from the NSA databases. Upon discovery, the device appears to be a device with some kind of collection array used for transmitting and receiving. Further visual inspection shows the brains of this device to be reminiscent of a popular hobbyist computer. Common data and visual ports non-responsive; the only exception is a boot prompt output when connecting over HDMI. Most interestingly there is a 40pin GPIO header with an additional 20pin header. Many of these physical pins show low-voltage activity which indicate data may be enabled. There may be a way to still interact with the device firmware...

Find the correct processor datasheet, and then use it and the resources provided to enter which physical pins enable data to and from this device

Hints:
Note: For the pinout.svg, turn off your application's dark mode if you're unable to see the physical pin labels (eg: 'P1', 'P60')
The pinout.svg has two voltage types. The gold/tan is 3.3v, the red is 5v.
The only additional resource you will need is the datasheet, or at least the relevant information from it

Downloads:
Rendering of debug ports on embedded computer ([pinout.svg](https://nsa-codebreaker.org/files/task2/pinout.svg?1707529470))  
image of device CPU ([cpu.jpg](https://nsa-codebreaker.org/files/task2/cpu.jpg?1707529470))  
copy of display output when attempting to read from HDMI ([boot_prompt.log](https://nsa-codebreaker.org/files/task2/boot_prompt.log?1707529470))  

Prompts:
Provide the correct physical pin number to power the GPIO header
Provide a correct physical pin number to ground the board:
Provide the correct physical pin number for a UART transmit function:
Provide the correct physical pin number for a UART receive function:

The image cpu.jpg has the part number of the cpu, which yields the datasheet in an online search:
[BCM2837 Datasheet](https://cs140e.sergio.bz/docs/BCM2837-ARM-Peripherals.pdf)
searching the datasheets yields the specific pins of the cpu and their functions, with that information
the pins are mapped to the corresponding provided pinout provided in pinout.svg of which is for 
[Rasberry Pi 3B+](https://www.raspberrypi.com/products/raspberry-pi-3-model-b-plus/), in addition to the gpio pinout for the peripheral device show next to the 40 pin gpio
![Rasberry Pi GPIO](https://community-storage.element14.com/communityserver-components-secureimagefileviewer/telligent/evolution/components/attachments/13/153/00/00/00/01/74/28/pi3_gpio.png-560x743.png?sv=2016-05-31&sr=b&sig=vOQbyWa%2F%2Bt5OIWeSMw%2Ftawqf3TzVdYnZLgu3MRVc%2FGI%3D&se=2024-02-15T23%3A59%3A59Z&sp=r)
![Rasberry Pi GPIO](https://www.raspberrypi.com/documentation/computers/images/GPIO-Pinout-Diagram-2.png)
![Rasberry Pi GPIO](https://www.raspberrypi.com/documentation/computers/images/GPIO.png)
once the specific pins have been determined submit in specified format
