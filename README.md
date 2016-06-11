ESP8266 WeMos Shield for HopeRF RFM95 RFM96 RFM98 Lora Modules
==============================================================

This shield is used to hold HopeRF [Lora module][4] Software with WeMos ESP8266 boards it has just few minimal features. 
- I2C Pullups placement
- Classic I2C 128x64 OLED connector
- Placement for RFM95/96/98 Lora module
- Placement for choosing single Wire, SMA or u-FL Antenna type for both 433MHz and 868MHz output
- 2 x WS2812B Type LED for visual indication
- Custom switch on GPIO2

You can find more information on WeMos on their [site][1], it's really well documented.
I now use WeMos boards instead of NodeMCU's one because they're just smaller, features remains the same, but I also suspect WeMos regulator far better quality than the one used on NodeMCU that are just fake of originals AMS117 3V3.

Boards arrived from OSHPark, I tested them, works fine with forked version of [single Channel LoRaWAN Gateway][5] but you can use any program that is compatible with RFM95 Lora module according it to real pinout.

Detailed Description
====================

Look at the schematics for more informations.

### Schematic  
![schematic](https://raw.githubusercontent.com/hallard/WeMos-Lora/master/WeMos-Lora-sch.png)  

### Boards  
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/WeMos-Lora-top.png" alt="Top" width="40%" height="40%">&nbsp;
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/WeMos-Lora-bot.png" alt="Bottom" width="40%" height="40%">&nbsp; 

You can order the PCB of this board at [OSHPARK][3]

### Assembled boards

<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/WeMos-Lora-top-assembled.jpg" alt="Top">    
<img src="https://raw.githubusercontent.com/hallard/WeMos-Lora/master/WeMos-Lora-bot-assembled.jpg" alt="Bottom">    

##License

You can do whatever you like with this design.

##Misc
See news and other projects on my [blog][2] 
 
[1]: http://www.wemos.cc/wiki/doku.php?id=en:d1_mini
[2]: https://hallard.me
[3]: https://oshpark.com/shared_projects/FD4f9q2s
[4]: http://www.hoperf.com/rf_transceiver/lora/
[5]: https://github.com/hallard/ESP-1ch-Gateway/
