# ESP8266 WeMos Shield for HopeRF RFM95 RFM96 RFM98 Lora Modules


This shield is used to hold HopeRF [Lora module][4] Software with WeMos ESP8266 boards it has just few minimal features. 
- I2C Pullups placement
- Classic I2C 128x64 OLED connector
- Placement for RFM95/96/98 Lora module
- Placement for choosing single Wire, SMA or u-FL Antenna type 
- 2 x WS2812B Type LED for visual indication
- Custom switch on GPIO2
- Added footprint for Microchip 24AA02E64 64 bits serial number (v1.1+) 
- Added Solder PAD jumper to be able to connect GPIO16 to Reset to enable deep sleep (V1.2+)


You can find more information on WeMos D1 mini boards ([mini][1], [mini pro][7], [mini lite][8]), it's really well documented.
I now use WeMos boards instead of NodeMCU's one because they're just smaller, features remains the same, but I also suspect WeMos regulator far better quality than the one used on NodeMCU that are just fake of originals AMS117 3V3.

Boards arrived, I tested them, works fine with forked version of [single Channel LoRaWAN Gateway][5] but you can use any program that is compatible with RFM95 Lora module according it to real pinout.

## Detailed Description

Look at the schematics for more informations.

SPI connexion is classic (MOSI/MISO/CLK), 

**New v1.3** Solder pad on bottom layer to be able to switch 3V3 and GND Pin. It's configured as old version mapping by default (silkscreen is correct). 

Since V1.2, chip Select is still connected with GPIO16 by default but solder pad on bottom of the board allow you to connect GPIO16 to RESET for Deep Sleep. In this case: 

- add and solder R3 Pulldown (100K) to make RFM95 SPI device always selected
- on bottom solder pad cut trace between GPIO19 and SEL 
- on bottom solder join GPIO16 and RST with solder


Other pins that may need be adapted into code (for example if you use TTN network gateway code) according to the following pinout

Please not that to avoid 3 GPIOs for DIO0,DIO1,DIO2 Interrupt, these 3 are OR'ed with 3 diodes, respectively named D2,D3 and D4. This permit to use only one IRQ pin (here GPIO15). This is only possible because on IRQ routine the RFM9x IRQ register is read and then software knows which one has been triggered.
You can see more details ont this dedicated LMIC [Pull Request][6]

```
   WeMos D1          RFM9x Module
  GPIO12 (D6) <----> MISO
  GPIO13 (D7) <----> MOSI
  GPIO14 (D5) <----> CLK
  GPIO15 (D8) <----> DIO0/D2 OR DIO1/D3 OR DIO2/D4
  GPIO16 (D0) <----> SEL Chip Select (depending on bottom solder PAD position)

   WeMos D1         Shield Feature
  GPIO5  (D1) <----> I2C SCL
  GPIO4  (D2) <----> I2C SDA
  GPIO0  (D3) <----> WS2812 LEDS
  GPIO2  (D4) <----> Push Button
  GPIO16 (D0) <----> RESET (depending on bottom solder PAD position)
```

## Schematic  

![schematic](https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-sch.png)  

## Bill Of Material

Nothing fancy, all components are 0805 and/or PTH and can be ordered almost anywhere (digikey, mouser, radiospare, ...). 
use only what you need dependings on what you want to do. You can find lot of components on ebay or aliexpress, but since vendors are often ephemere, I put for reference the BOM on well known providers.

Here is the [octopart BOM](https://octopart.com/bom-tool/SJPhS5Am)

## Firmware  

[firmware](https://github.com/hallard/WeMos-Lora/tree/master/firmware)  

## Boards  

<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-top.png" alt="Top">&nbsp;
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-bot.png" alt="Bottom">

~~You can order the PCB of this board at [PCBs.io][3] if you do so, PCBs.io give me discount that allow me to buy some new created boards.~~
   
Looks like PCBs.io is gone, I do not have any rewards from PCBs.io since August 2020 and my free order placed after are still not received, so my guess they are not on business anymore.

So you can order the board on [oshpark](https://oshpark.com/shared_projects/E9P1U0Ae). It's a pitty after several discuss with OSHPark that I can't have any rewards for each people ordering my boards, this would allow me to order free PCB for shared projects and create new ones. For information my shared boards generated a total of **$285 162.00** orders at PCBs.io in 4 years, not bad at all :-)

Hoping one day OSHparks will thanks me giving them this market. 


## Assembled boards (V1.0)

<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-top-assembled.jpg" alt="Top">    
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-bot-assembled.jpg" alt="Bottom">    

## License

<img alt="Creative Commons Attribution-NonCommercial 4.0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png">   

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/)    
If you want to do commercial stuff with this project, please contact [CH2i company](https://www.ch2i.eu/en#support) so we can organize an simple agreement.

# Misc

See news and other projects on my [blog][2] 
 
[1]: https://wiki.wemos.cc/products:d1:d1_mini
[2]: https://hallard.me
[3]: https://PCBs.io/share/4Q1Z4 
[4]: http://www.hoperf.com/rf_transceiver/lora/
[5]: https://github.com/hallard/ESP-1ch-Gateway/
[6]: https://github.com/matthijskooijman/arduino-lmic/pull/34
[7]: https://wiki.wemos.cc/products:d1:d1_mini_pro
[8]: https://wiki.wemos.cc/products:d1:d1_mini_lite