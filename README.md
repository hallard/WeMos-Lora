ESP8266 WeMos Shield for HopeRF RFM95 RFM96 RFM98 Lora Modules
==============================================================

This shield is used to hold HopeRF [Lora module][4] Software with WeMos ESP8266 boards it has just few minimal features. 
- I2C Pullups placement
- Classic I2C 128x64 OLED connector
- Placement for RFM95/96/98 Lora module
- Placement for choosing single Wire, SMA or u-FL Antenna type 
- 2 x WS2812B Type LED for visual indication
- Custom switch on GPIO2
- Added footprint for Microchip 24AA02E64 64 bits serial number (v1.1+) 
- Added Solder PAD jumper to be able to connect GPIO16 to Reset to enable deep sleep (V1.2+)


You can find more information on WeMos on their [site][1], it's really well documented.
I now use WeMos boards instead of NodeMCU's one because they're just smaller, features remains the same, but I also suspect WeMos regulator far better quality than the one used on NodeMCU that are just fake of originals AMS117 3V3.

Boards arrived, I tested them, works fine with forked version of [single Channel LoRaWAN Gateway][5] but you can use any program that is compatible with RFM95 Lora module according it to real pinout.

Detailed Description
====================

Look at the schematics for more informations.

SPI connexion is classic (MOSI/MISO/CLK), 

Since V1.2, chip Select is still connected with GPIO16 by default but solder pad on bottom of the board allow you to connect GPIO16 to RESET for Deep Sleep. In this case, please add and solder R3 Pulldown (100K) to make RFM95 SPI device always selected.

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

### Schematic  
![schematic](https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-sch.png)  

### Firmware  
![firmware](https://raw.githubusercontent.com/hallard/WeMos-Lora/firmware/)  

### Boards  
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-top.png" alt="Top">&nbsp;
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-bot.png" alt="Bottom">

You can order the PCB of this board at [PCBs.io][3] if you do so, PCBs.io give me discount that allow me to buy some new created boards.

### Assembled boards

<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-top-assembled.jpg" alt="Top">    
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/pictures/WeMos-Lora-bot-assembled.jpg" alt="Bottom">    
##License

You can do whatever you like with this design.

##Misc
See news and other projects on my [blog][2] 
 
[1]: http://www.wemos.cc/wiki/doku.php?id=en:d1_mini
[2]: https://hallard.me
[3]: https://PCBs.io/share/4Q1Z4 
[4]: http://www.hoperf.com/rf_transceiver/lora/
[5]: https://github.com/hallard/ESP-1ch-Gateway/
[6]: https://github.com/matthijskooijman/arduino-lmic/pull/34