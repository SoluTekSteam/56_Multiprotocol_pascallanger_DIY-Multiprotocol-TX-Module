#Protocols details
Here are detailed descriptions of every supported protocols (sorted by RF modules) as well as the available options for each protocol.

 If you want to see a list of models that use these protocols see the [Models](Models.md) page.

## Default Mapping of Protocols <a name="DefaultMapping"></a>
Here is the default mapping of protocols to the 16-position protocol selection switch on the module.  You can customize these when you compile your own firmware as described in [Compiling and Programming.](Compiling.md)

**Note that the protocol must be selected before the unit is turned on.**

Dial|Protocol|Sub_protocol|RX Num|Power|Auto Bind|Option|RF Module
----|--------|------------|------|-----|---------|------|---------
0|Select serial||||||
1|FLYSKY|Flysky|0|High|No|0|A7105
2|HUBSAN|-|0|High|No|0|A7105
3|FRSKYD|-|0|High|No|-41|CC2500
4|HISKY|Hisky|0|High|No|0|NRF24L01
5|V2X2|-|0|High|No|0|NRF24L01
6|DSM|DSM2|0|High|No|6|CYRF6936
7|DEVO|-|0|High|No|0|CYRF6936
8|YD717|YD717|0|High|No|0|NRF24L01
9|KN|WLTOYS|0|High|No|0|NRF24L01
10|SYMAX|SYMAX|0|High|No|0|NRF24L01
11|SLT|-|0|High|No|0|NRF24L01
12|CX10|BLUE|0|High|No|0|NRF24L01
13|CG023|CG023|0|High|No|0|NRF24L01
14|BAYANG|-|0|High|No|0|NRF24L01
15|SYMAX|SYMAX5C|0|High|No|0|NRF24L01

## Useful notes and definitions
- **Extended limits supported** - A command range of -125%..+125% will be transmitted. Otherwise the default is -100%..+100% only.
- **Autobind protocol** - The transmitter will automatically initiate a bind sequence on power up.  This is for models where the receiver expects to rebind every time it is powered up. In these protocols you do not need to press the bind button at power up to bind, it will be done automatically.
- **Channel Order** - The channel order assumed in all the documentation is AETR and it is highly recommended that you keep it this way.  You can change this in the compilation settings.  However, please indicate your channel order in all questions and posts on the forum pages. 

***
#A7105 RF Module

##FLYSKY
Extended limits supported

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
A|E|T|R|CH5|CH6|CH7|CH8

Note that the RX ouput will be AETR.

###Sub_protocol V9X9
CH5|CH6|CH7|CH8
---|---|---|---
FLIP|LIGHT|PICTURE|VIDEO

###Sub_protocol V6X6
CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12
---|---|---|---|---|---|---|---
FLIP|LIGHT|PICTURE|VIDEO|HEADLESS|RTH|XCAL|YCAL

###Sub_protocol V912
CH5|CH6
---|---
BTMBTN|TOPBTN

##HUBSAN
Models: Hubsan H102D, H107/L/C/D and Hubsan H107P/C+/D+

Autobind protocol

Telemetry enabled for battery voltage and TX RSSI

Option=vTX frequency (H107D) 5645 - 5900 MHz

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|LIGHT|PICTURE|VIDEO|HEADLESS

***
#CC2500 RF Module

##FRSKYV = FrSky 1 way
Models: FrSky receivers V8R4, V8R7 and V8FR.

Extended limits supported

Option=fine frequency tuning. This value is different for each board. To determine the option value, find the two limits where the RX loses connection then set the option value to half way between them. If you have a 4in1 V2 board the value is around 40.

CH1|CH2|CH3|CH4
---|---|---|---
CH1|CH2|CH3|CH4

##FRSKYD
Models: FrSky receivers D4R and D8R. DIY RX-F801 and RX-F802 receivers.

Extended limits supported

Telemetry enabled for A0, A1, RSSI, TSSI and Hub

Option=fine frequency tuning. This value is different for each board. To determine the option value, find the two limits where the RX loses connection then set the option value to half way between them. If you have a 4in1 V2 board the value is around 40.

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8

##FRSKYX
Models: FrSky receivers X4R, X6R and X8R.

Extended limits supported

Telemetry enabled for A1 (RxBatt), A2, RSSI, TSSI and Hub

Option=fine frequency tuning. This value is different for each board. To determine the option value, find the two limits where the RX loses connection then set the option value to half way between them. If you have a 4in1 V2 board the value is around 40.

###Sub_protocol CH_16
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12|CH13|CH14|CH15|CH16
---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12|CH13|CH14|CH15|CH16

###Sub_protocol CH_8
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8

##SFHSS
Models: Futaba RXs and XK models.

Option=fine frequency tuning. This value is different for each board. To determine the option value, find the two limits where the RX loses connection then set the option value to half way between them. If you have a 4in1 V2 board the value is around 40.

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
A|E|T|R|CH5|CH6|CH7|CH8

***
#CYRF6936 RF Module

##DEVO
Extended limits supported

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
A|E|T|R|CH5|CH6|CH7|CH8

Note that the RX ouput will be EATR.

Bind procedure using serial:
- With the TX off, put the binding plug in and power on the RX (RX LED slow blink), then power it down and remove the binding plug. Receiver should now be in autobind mode.
- Turn on the TX, set protocol = Devo with option=0, turn off the TX (TX is now in autobind mode).
- Turn on RX (RX LED fast blink).
- Turn on TX (RX LED solid, TX LED fast blink).
- Wait for bind on the TX to complete (TX LED solid).
- Make sure to set the RX_Num value for model match.
- Change option to 1 to use the global ID.
- Do not touch option/RX_Num anymore.

Bind procedure using PPM:
- With the TX off, put the binding plug in and power on the RX (RX LED slow blink), then power it down and remove the binding plug. Receiver should now be in autobind mode.
- Turn on RX (RX LED fast blink).
- Turn the dial to the model number running protocol DEVO on the module.
- Press the bind button and turn on the TX. TX is now in autobind mode.
- Release bind button after 1 second: RX LED solid, TX LED fast blink.
- Wait for bind on the TX to complete (TX LED solid).
- Press the bind button for 1 second. TX/RX is now in fixed ID mode.
- To verify that the TX is in fixed mode: power cycle the TX, the module LED should be solid ON (no blink).
- Note: Autobind/fixed ID mode is linked to the dial number. Which means that you can have multiple dial numbers set to the same protocol DEVO with different RX_Num and have different bind modes at the same time. It enables PPM users to get model match under DEVO.

##DSM
###Sub_protocol DSM2
Extended limits supported

Telemetry enabled for TSSI and plugins

option=number of channels and frame rate:
 - 0 : 4 channels @22ms
 - 1 : 5 channels @22ms
 - 2 : 6 channels @22ms
 - 3 : 7 channels @22ms

 - 4 : 4 channels @11ms
 - 5 : 5 channels @11ms
 - 6 : 6 channels @11ms
 - 7 : 7 channels @11ms

 - 8 : 8 channels @22ms
 - 9 : 9 channels @22ms
 - 10 : 10 channels @22ms
 - 11 : 11 channels @22ms
 - 12 : 12 channels @22ms

Value 6 is usually giving the best results with most of the RX.

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12
---|---|---|---|---|---|---|---|---|----|----|----
A|E|T|R|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12

Note that the RX ouput will be TAER.

###Sub_protocol DSMX
Same as above

##J6Pro

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12
---|---|---|---|---|---|---|---|---|----|----|----
A|E|T|R|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12

***
#NRF24L01 RF Module

##ASSAN
Extended limits supported

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10
---|---|---|---|---|---|---|---|---|---
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10

The transmitter must be close to the receiver while binding.

##BAYANG
Models: EAchine H8(C) mini, BayangToys X6/X7/X9, JJRC JJ850, Floureon H101 ...

Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10
---|---|---|---|---|---|---|---|---|----
A|E|T|R|FLIP|RTH|PICTURE|VIDEO|HEADLESS|INVERTED

##CG023
Models: EAchine CG023/CG031/3D X4

Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|LIGHT|PICTURE|VIDEO|HEADLESS

###Sub_protocol YD829
Models: Attop YD-822/YD-829/YD-829C ...

CH5|CH6|CH7|CH8|CH9
---|---|---|---|---
FLIP||PICTURE|VIDEO|HEADLESS

###Sub_protocol H8_3D
Models: EAchine H8 mini 3D, JJRC H20/H22

CH5|CH6|CH7|CH8|CH9
---|---|---|---|---
FLIP|LIGTH|OPT1|OPT2|CAL

JJRC H20: OPT1=Headless, OPT2=RTH

JJRC H22: OPT1=RTH, OPT2=180/360° flip mode

H8 3D: OPT1=RTH then press a direction to enter headless mode (like stock TX), OPT2=switch 180/360° flip mode

CAL: calibrate accelerometers

##CX10
Extended limits supported

Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6
---|---|---|---|---|---
A|E|T|R|FLIP|RATE

Rate: -100%=rate 1, 0%=rate 2, +100%=rate 3

###Sub_protocol GREEN
Models: Cheerson CX-10 green pcb

Same channels assignement as above.

###Sub_protocol BLUE
Models: Cheerson CX-10 blue pcb & some newer red pcb, CX-10A, CX-10C, CX11, CX12, Floureon FX10, JJRC DHD D1

CH5|CH6|CH7|CH8
---|---|---|---
FLIP|RATE|PICTURE|VIDEO

Rate: -100%=rate 1, 0%=rate 2, +100%=rate 3 or headless for CX-10A

###Sub_protocol DM007

CH5|CH6|CH7|CH8|CH9
---|---|---|---|---
FLIP|MODE|PICTURE|VIDEO|HEADLESS

###Sub_protocol Q282 and Q242

CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12
---|---|---|---|---|---|---|---
FLIP|LED|PICTURE|VIDEO|HEADLESS|RTH|XCAL|YCAL

Model: JXD 509 is using Q282 with CH12=Start/Stop motors

###Sub_protocol JC3015_1

CH5|CH6|CH7|CH8
---|---|---|---
FLIP|MODE|PICTURE|VIDEO

###Sub_protocol JC3015_2

CH5|CH6|CH7|CH8
---|---|---|---
FLIP|MODE|LED|DFLIP

###Sub_protocol MK33041

CH5|CH6|CH7|CH8|CH9|CH10
---|---|---|---|---|---
FLIP|MODE|PICTURE|VIDEO|HEADLESS|RTH

##ESKY

CH1|CH2|CH3|CH4|CH5|CH6
---|---|---|---|---|---
A|E|T|R|GYRO|PITCH

##FY326

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|RTH|HEADLESS|EXPERT|CALIBRATE

##FQ777
Model: FQ777-124

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
A|E|T|R|FLIP|RTH|HEADLESS|EXPERT

##HISKY
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
A|E|T|R|GEAR|PITCH|GYRO|CH8

GYRO: -100%=6G, +100%=3G

###HK310
Models: RX HK-3000, HK3100 and XY3000 (TX are HK-300, HK-310 and TL-3C)

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8
---|---|---|---|---|---|---|---
|||T|R|AUX|T_FSAFE|R_FSAFE|AUX_FSAFE

##KN
CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11
---|---|---|---|---|---|---|---|---|----|----
A|E|T|R|DR|THOLD|IDLEUP|GYRO|Ttrim|Atrim|Etrim

Dual Rate (DR): +100%=full range, Throttle Hold (THOLD): +100%=hold, Idle Up (IDLEUP): +100%=3D, GYRO: -100%=6G, +100%=3G

###Sub_protocol WLTOYS
###Sub_protocol FEILUN
Same channels assignement as above.

##MJXQ
Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11|CH12|CH13
---|---|---|---|---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|LED|PICTURE|VIDEO|HEADLESS|RTH|AUTOFLIP|PAN|TILT

###Sub_protocol WLH08
###Sub_protocol X600
Only 3 TX IDs available, change RX_Num value 0..2 to cycle through them
###Sub_protocol X800
Only 3 TX IDs available, change RX_Num value 0..2 to cycle through them
###Sub_protocol H26D
###Sub_protocol E010
Only 1 TX ID available

##MT99XX
Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|LED|PICTURE|VIDEO|HEADLESS

###Sub_protocol MT
Models: MT99xx
###Sub_protocol H7
Models: Eachine H7, Cheerson CX023
###Sub_protocol YZ
Model: Yi Zhan i6S
Only one model can be flown at the same time since the ID is hardcoded.
###Sub_protocol LS
Models: LS114, 124, 215

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|INVERT|PICTURE|VIDEO|HEADLESS

##Shenqi
Autobind protocol

Model: Shenqiwei 1/20 Mini Motorcycle

CH1|CH2|CH3|CH4
---|---|---|---
 | |T|R

Throttle +100%=full forward,0%=stop,-100%=full backward.

##SLT
Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6
---|---|---|---|---|---
A|E|T|R|GEAR|PITCH

##Symax
Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|RATES|PICTURE|VIDEO|HEADLESS

###Sub_protocol SYMAX
Models: Syma X5C-1/X11/X11C/X12

###Sub_protocol SYMAX5C
Model: Syma X5C (original) and X2

##V2X2
Models: WLToys V202/252/272, JXD 385/388, JJRC H6C, Yizhan Tarantula X6 ...

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9|CH10|CH11
---|---|---|---|---|---|---|---|---|----|----
A|E|T|R|FLIP|LIGHT|PICTURE|VIDEO|HEADLESS|MAG_CAL_X|MAG_CAL_Y

PICTURE: also automatic Missile Launcher and Hoist in one direction

VIDEO: also Sprayer, Bubbler, Missile Launcher(1), and Hoist in the other dir

##YD717
Autobind protocol

CH1|CH2|CH3|CH4|CH5|CH6|CH7|CH8|CH9
---|---|---|---|---|---|---|---|---
A|E|T|R|FLIP|LIGHT|PICTURE|VIDEO|HEADLESS

###Sub_protocol YD717
###Sub_protocol SKYWLKR
###Sub_protocol SYMAX4
###Sub_protocol XINXUN
###Sub_protocol NIHUI
Same channels assignement as above.
