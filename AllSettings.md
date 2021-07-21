#Pads
#####Name:

<Ch04:Snare1  H>
Name:Snare      
Input name. Every input can have a custom Name set from a predefined list of names. On Head/Bow inputs the custom name has cymbal 'H' appended at the end, on Rim/Edge inputs the custom name has cymbal 'R' appended at the end.

#####Disabled:

Disabled:    No
If you don't use the input set Set Disabled to Yes. Default is No (input is enabled).

#####MNote:

MNote: D2    38
Master note. You can use MNote to easily set all input's notes  in one place. It shows the current Note of the input and if changed it sets Note, ANote, PNote (and DBNote if it is a rim/edge input) to the same value.

#####Note:

Note:  D2    38
Input's note. D2 is note name and 38 is MIDI note number.

#####ANote:

ANote: D2    38
Input's alternating note. If it is different from Note then the note values will be alternating between Note and ANote for every hit. By default it is equal to Note.

#####PNote:

PNote: D2    38
Input's note for "pressrolls". If a "pressroll" is detected then the note values will be taken from PNote rather than from Note/ANote. See also PressRoll Time in Miscellaneous settings.

#####Channel:

Channel:     10
Input's MIDI channel. Default is 10 on all channels.

#####Function:

Function:Normal
Function of the input. It can be set to Normal, PrgChg or CutOff. Default is Normal.

When set to PrgChg it has no effect on Head/Bow inputs. On switch type Rim/Edge inputs this option activates Program Change support. To activate the Program Change support:
1. Configure the input either as a dual piezo/switch pad or as a Yamaha style 3 zone cymbal.
2. On a Rim/Edge input set Function to PrgChg.
3. Set ANote to a number which will limit the Program Change lowest number.
4. Set PNote to a number which will limit the Program Change highest number.
   Pressing the edge switch will send MIDI Program Change messages on each press in the upwards direction between ANote and PNote values. Pressing the bell switch (if the edge and bell switches are wired as in a Yamaha style 3 zone cymbal and configured accordingly) will send MIDI Program Change messages on each press in the downwards direction between ANote and PNote values. Of course, it doesn't have to be a real Yamaha type 3 zone pad/cymbal, it just needs switches connected to the rim/edge input as in a Yamaha type 3 zone cymbal, i.e. one switch connected directly and the second switch connected over a 10k resistor. It will work with only one switch as well but it will only cycle in upwards direction going to a ANote value again after reaching PNote value. Sent kit (PC number + 1) is shown on the LCD when Program Change message is sent.

When set to CutOff the 'ANote' setting changes it meaning to 'cut off' level - hits with velocities below level set in 'ANote' will not trigger Note On/Off messages.

#####Curve:

Curve:  Log1    
Hit level curve. Sets input signal strength to MIDI level adaptation function for the input. Can be set to Linear, Log1, Log2, Log3, Exp1, Exp2, S1, S2, Strong1, Strong2, Max.

#####ComprLvl:

ComprLvl:     0
Compression level on the input. Can be set between 0 and 7. Here is an illustration of the effect this setting has on a MIDI note velocity depending on the applied compression level (0 - top line, 7 - bottom line) and input hit strength with a Linear curve setting:

#####LvlShift:

LvlShift:     0
Level shift on the input. Can be set to 0, 8, 16, 24, 32, 40, 48 or 56. Here is an illustration of the effect this setting has on a MIDI note velocity depending on the applied level shift (0 - bottom line, 56 - top line) and input hit strength with a Linear curve setting and compression level 7:

#####Xtalk:

Xtalk:        2
Crosstalk suppression level. Can be set between 0 (no crosstalk suppression) and 7 (strongest crosstalk suppression). If the drum kit has parasitic vibrations transmitted from one pad to another it can trigger signals on pads which were not hit thus producing false MIDI signals. Adjusting this setting you can try to mitigate this problem. Be warned that with a poorly built kit the crosstalk suppression will not help to avoid the problem.

#####XtalkGrp:

XtalkGrp:     0
Crosstalk suppression group of the input. Can be set between 0 and 7. By default all inputs are placed into the same group meaning that the Xtalk setting will be evaluated  against signals from all pads. If some of your pads are physically/mechanically isolated you can place pads into 8 different Xtalk groups so that the Xtalk setting only evaluated against within the same group thus avoiding unnecessary suppression.

#####Threshold:

Threshold:   30
For piezo inputs: Input threshold level. Sets at what minimum (relative electrical) level a signal will be detected as a hit. This is one of the main settings effecting overall performance of the drum kit and the best actual value depends on types of pads used. It may take a while to find the best value.

For switch Rim/Edge inputs: Input switch threshold. Sets below which level the switch is detected as hit/pressed.  Note that on the switch Rim/Edge inputs actual velocity is determined by signal from a piezo on a Head/Bow input. The best way to set a correct threshold on a switch input is to use MIDI-OX to monitor 'aftertouch' MIDI messages. With a proper threshold value you should see 2 or 3 (dual zone or 3way/3 zone pad) 'aftertouch' on' MIDI messages when you press the switch and 2 or 3 'aftertouch off' MIDI messages when you release the switch.

#####Gain:

Gain:         4
Gain level for the input. Can be set between 0 and 8. Lower value makes the input less sensitive, higher value makes the input more sensitive. Set it lower for 'hot' pads (pads which produce stronger electrical signals), set it higher for 'cold' pads (pads which produce weaker electrical signals).

#####HiLvlAuto:

HiLvlAuto:  Yes
When set to Yes, MegaDrum tries to auto adjust HighLevel for the input. Can be used for an initial setup to get a sense how 'hot' or 'cold' the pad is.  After this, set it to No and adjust HighLevel manually using the auto detected level as a guidance.

#####HighLevel:

HighLevel:  855
High (top) level of the input. Signals with relative electrical levels between Threshold and HighLevel will produce MIDI notes with velocities between 1 and 127 (provided both ComprLvl and LvlShift are set to 0). Any signals with relative electrical levels above HighLevel will produce MIDI notes with velocity 127. The further Threshold and HighLevel are apart the better, provided you can reliably get MIDI notes with velocity 127 with strongest hits. Having said that, you will lose almost no dynamics until when HighLevel-Threshold<200~300. If you set HighLevel to maximum, 1023, and still easily get MIDI notes with velocity 127 you probably have a very 'hot' pad and you may lose hit dynamics. Try lowering Gain. If it doesn't help will probably need to use a voltage divider on the input. Don't be scared, a voltage divider is just a trim potentiometer which lowers input signal.

#####Retrigger:

Retrigger:    8
Retrigger period in milliseconds for the input. Determines how many milliseconds must pass after a previously detected signal for a new signal to be detected to prevent a 'machine gun' effect or false triggering due to vibration after a hit. As a Threshold setting this is one is one of the most important parameters and it may take some time to find the best value. Ideally it should be set as low as possible and let 'Dynamic Threshold' to combat the 'machine gun' and false triggering. But if even with highest Dynamic Threshold Levels and Dynamic  Threshold Decay times you still get these unwanted effects you may need to raise Retrigger level. On DIY pads and cymbals I have Retrigger set between 4 and 12 milliseconds. Setting it too high will prevent you from doing fast drum rolls.

#####DynLevel and DynTime:

DynLevel:     5

DynTime:     32

Dynamic Threshold level and Dynamic Threshold decay time for the input.  Also two very important parameters. Raising both DynLevel and DynTime will tell MegaDrum to suppress false triggering (crosstalks between inputs, double triggering) harder. Raising them too high may cause MegaDrum to miss some hits on fast/press rolls. DynLevel sets how hard MegaDrum will try to suppress false triggering. DynTime sets for how long MegaDrum will try to suppress false triggering. For most rubber type pads/cymbals DynLevel between 8 and 15 and DynTime between 8 and 20 should produce the best results. For mesh type pads it may be needed to raise DynTime above 20 and up to 60.

#####ExtrFals:

ExtrFals:    No
Extra false triggering suppression. Disabled by default. Can be enabled for some pads/cymbals with very long inconsistent after hit vibration but it will negatively affect pressrolls and very fast rolls. Ignored on Atmega.

#####RollSmth:

RollSmth:      0
Rolls smoothing level. Disabled by default (0) and can be set to 1 (lightest smoothing), 2 or 3 (strongest smoothing). When set to 1, 2 or 3 the MIDI Note On levels will be smoothed if hits from the same input come within Note Off Delay. Ignored on Atmega.

#####MinScan:

MinScan:     20
Minimum scan time for the input. Measured/shown in 1/10th of millisecond. Can be set between 1 and 100 (0.1 - 10ms). When MegaDrum detects a signal above Threshold/Dynamic threshold, it will keep sampling it for MinScan period of time before marking the signal as registered and making it ready to be sent over MIDI next MegaDrum scans (scan time is set by 'Latency') all channels for registered signals.
Lowering it will improve Latency (MegaDrum latency is between Latency and and Latency+MinScan) and may worsen level accuracy. Raising it will worsen Latency and may improve level accuracy. Generally for rubber type pads/cymbals setting MinScan to 20 (2ms) is enough for proper signal level detection. For mesh type pads you may need to raise MinScan to 30~50 - the bigger mesh type pads the higher MinScan is required for proper signal level detection..

#####DualHead for Head/Bow input or PadName->Type for Rim/Edge inputs:

DualHead:   Yes
For Head/Bow inputs: Can be set to No, Yes or 3Way.
If set to No, Head/Bow and Rim/Edge inputs are treated as separate pads.
If set to Yes, Head/Bow and Rim/Edge inputs are treated as parts of the same dual zone pad or as parts of the same 3 zone pad, e.g. Yamaha style 3 zone cymbals. See more about 3 zone pads below in BNote and BThreshold settings.
If set to 3Way, Head/Bow and Rim/Edge inputs are treated as Bow and Bell inputs of 3way pads, e.g. 3way Roland style cymbals, and the next Rim/Edge input is treated as an edge input of the same pad.

Type:     Piezo
For Rim/Edge inputs: Can be set as either Piezo or Switch. Sets the type of a trigger connected to the input. You can set it as Switch only if the Head/Bow input DualHead parameter is set to Yes or 3Way.

#####3rd Dsbld (only available on Rim/Edge inputs):

3rd Dsbld:   No
If you don't use 3rd zone set Set 3rd Dsbld to Yes. Default is No (3rd zone is enabled).

#####MBNote (only available on Rim/Edge inputs):

MBNote:C#3   49
Master note for the 3rd zone/rim shot. You can use MBNote to easily set all BNote, ABNote and PBNote  values in one place. It shows the current BNote and if changed it sets BNote, ABNote and PBNote (but not DBNote) to the same value.

#####BNote (only available on Rim/Edge inputs):

BNote: C#3   49
For piezo/switch/switch 3 zones pdas/cymbals: Note number for the 3rd zone of a 3 zone Yamaha style pad/cymbal.
For piezo/piezo dual zone pads: Note number for a rim shot. Set equal to a note number of the rim to disable rim shot functionality. Note that this feature is still experimental. Right settings for HighLevel on both the head and the rim inputs is very important. Raising MinScan on both the head and the rim can also improve rim shot reliability.

#####ABNote (only available on Rim/Edge inputs):

ABNote:C#3   49
3rd zone alternating note. If it is different from BNote then the note values will be alternating between BNote and ABNote for every hit. By default it is equal to BNote.

#####DBNote (only available on Rim/Edge inputs):

DBNote:C#3   49
For piezo/switch 2 or 3 zones pads/cymbals only. Dampened note value. If a pad/cymbal is hit when the rim/edge switch is pressed then the note value is taken from DBNote rather than from Note of the head/bow input. By default it is equal to Note of the head/bow input.

#####PBNote (only available on Rim/Edge inputs):

PBNote:C#3   49
3rd zone's note for "pressrolls". If a "pressroll" is detected then the note values will be taken from PBNote rather than from BNote/ABNote. See also PressRoll Time in Miscellaneous settings.

#####DualMidPoint (only available on Rim/Edge inputs):

DualMidPoint 15
For dual piezo/piezo pads: Midpoint is used to fine tune separation between head and rim hits. It can be set between 0 and 15. The higher the value the easier to get rim hits and more difficult to get head hits and vice versa.
For dual piezo/switch pads this option is disabled.

#####DualMidWidth (only available on Rim/Edge inputs):

DualMidWidth 15
For dual piezo/piezo pads: The width of signals for rim shots. It can be set between 0 and 15. The higher the value the easier to get rim shots and more likely to get false rim shots on head or rim hits and vice versa.
For dual piezo/switch pads this option is disabled.

#####BThreshold (only available on Rim/Edge inputs):

BThreshold:  15
For piezo/switch/switch 3 zones pdas/cymbals:Input switch threshold for the 3rd zone of a 3 zone Yamaha style pad/cymbal. Sets below which level the Bell switch is detected as hit/pressed. This level must be lower than Threshold level of the Rim/Edge input of a switch type trigger. If the connected pad is dual zone piezo/switch type or a 3way Roland cymbal, BThrshold must be set to 0 to prevent false triggering of Bell notes or alternatively set all Bell Notes (BNote, ABNote, PBNote) equal to the Edge/Rim Notes.
For dual piezo/piezo pads this option is disabled.

#Pads Extra Settings

#HiHat Pedal
#####Type:

Type:   F.Contr 

Type:       Pot 
Set the type of the HiHat pedal. The only difference, at the moment , is that when it set to F.Contr (Foot Controller) MegaDrum send Control Change (CC) messages with the changes of the pedal position. And when it is set to Pot (Potentiometer) it doesn't send CC messages.

#####New Algrthm:

New Algrthm: No 
New pedal handling algorithm for CC4 messages and Chick/Splash triggering. Default is No. When set to Yes it uses 4 settings:
MinVlcty
MaxVlcty
ChckDead
ChkCrv
If you press/release your pedal longer then ChkDead time period then no chick/splash will be triggered. To find right setting for it, navigate to Pedal->ChkDead and see detected values for various press speeds.
If you press/release your pedal slower then MinVlcty but shorter than ChkDead then chick/splash will have velocity 1.
If you press/release your pedal faster then MaxVlcty then chick/splash will have velocity 127 if started from full open or below 127 if started from lower position.
If you press/release your pedal with a velocity between MinVlcty and MaxVlcty then chick/splash will have velocity between 127 and 1 depending on where the press started and the press velocity.
ChkCrv is used to apply desired velocity Curve to chick/splash notes.
To configure:
a. navigate to Pedal->MaxVlcty and press the pedal as fast as possible. Note the "raw" velocity value you see and set MaxVlcty just below this value. In my case it was around 900.
b. navigate to Pedal->MinVlcty and press the pedal as slow as you want it to be still registered as chick. Note the "raw" velocity value you see and set MinVlcty just above this value. In my case it was around 400.
c. navigate to Pedal->ChckDead and press the pedal as slow as you want it to be still registered as chick. Note the "raw" timer value you see and set ChckDead just above this value. In my case it was around 600.
d. navigate to ChkCrv and set it to Exp2C. You may of course use another Curve or create a custom Curve for chicks and I recommend to use Exp2C as a starting point for the custom chick Curve.

#####Curve:

Curve:  Linear  
Set a curve you want to apply to the HiHat pedal CC messages. Options are LinearC, Log1C, Log2C, Log3C, Exp1C, Exp2C, S1C, S2C, Strong1C, Strong2C. Default is LinearC. Can be used to metigate non-linearity of the pedal output.

#####ChckDelay:

ChckDelay:    0 
Sets a number of milliseconds MegaDrum will wait before sending a Chick note, when you do a Chick. It can be set to any value above 0. If you set it to 0 you can only get Chicks. The higher ChckDelay the easier it is to get Splashes but the longer delays are when doing Chicks. If set too high, 15-30 milliseconds, you might begin noticing Chick latency.Default is 0.

#####AltIn:

AltIn:       No 

Here you can choose to use either a standard HiHat pedal input if set to No, or an alternative high impedance HiHat pedal input if set to Yes. High impedance might need to be used with high impedance output pedals. Default is No.

#####CC Value:

CC Value:     4 
Cotrol Change message number to be used with F.Contr type. Default is 4. 

#####CC RdcLvl:

CC RdcLvl:    0 
CC MIDI messages reduction level . If set above 0 it reduces amount of CC MIDI messages for pedal position changes. Can be set between 0 (default - no reduction) and 3 (maximum reduction).

#####LvlsRevers:

LvlsRevers:  No 

For some types of pedals it necessary to set it to Yes to reverse input levels read from a pedal.

#####EnSoftChick:

EnSoftChick: No 

Enables or disables "soft chicks". "Soft chick" are HiHat "chicks" which are triggered when the pedal is pressed only half way and then quickly released.

#####LevelsAuto:

LevelsAuto: Yes 

If set to Yes MegaDrum will try automatically adjust HiHat Pedal->LowLevel nad HiHat Pedal->HiLevel after you pressed the pedal a few times. You may use it initially as a guidance for proper Low and High levels of the pedal. Once you saw what levels were auto set you'd better set it to No and adjust LowLevel and HiLevel values manually. Default is Yes.

#####LowLevel:

LowLevel:    90 

Set the low level of the pedal, when pedal is fully pressed. If set too low you may not be able to get fully closed HiHat pedal.

#####HiLevel:

HiLevel:    900 

Set the high level of the pedal, when pedal is fully open (released). If set too high you may not be able to get fully open HiHat pedal.

You should adjust both low and high level so that the values were as far apart as possible and yet the pedal reaches extreme positions. Use VU Meter (not very accurate), Big VU Meter (more accurate) or CC messages (with MDM Raw MIDI Log). When using CC messages and MDM Raw MIDI Log as a guidance you need to achieve such a configuration that CC messages are not sent by MegaDrum in extreme pedal positions.

#####OpenLvl:
#####SOpenLvl:
#####SOpenLvl2:
#####HOpenLvl:
#####HOpenLvl2:

OpenLvl:      8

Measured against CC MIDI message value: 0 - for fully open, 127 - for fully closed. Set the level below which HiHat hits registered as open/semi open/semi open2/half open/half open2 hits.

#####ClosedLvl:

ClosedLvl:  110 

Measured against CC MIDI message value: 0 - for fully open, 127 - for fully closed. Set the level below which HiHat hits registered as semi closed and above which as closed hits.

Next screens are HiHat Pedal->MinVlcty: MaxVlcty: ChckDead: and ChkCrv:

MinVlcty:   400 

MaxVlcty:   900 

ChckDead:   600 

ChkCrv:   Exp2C 

These 4 settings are used only when "HiHat Pedal->New Algrthm:" is set to Yes. See recommendation for configuring these settings in HiHat Pedal->New Algrthm above.

#####ChickThrsh:

ChickThrsh  120 

Measured against CC MIDI message value: 0 - for fully open, 127 - for fully closed. Set the level below which a following pedal 'step on' will generate a chick.

#####ShrtChckTh:

ShrtChckTh  115 

Measured against CC MIDI message value: 0 - for fully open, 127 - for fully closed. Set the level below which a following pedal 'step on' will generate a chick with velocity between 1 and 64 depending on the speed with which the pedal is pressed.

#####LngChckTh:

LngChckTh:   16 
Measured against CC MIDI message value: 0 - for fully open, 127 - for fully closed. Set the level below which a following pedal 'step on' will generate a chick with velocity between 1 and 127 depending on the speed with which the pedal is pressed.

#####HHInput:

HHInput:      2 
Set the input number which will be paired with the HiHat pedal as a HiHat cymbal. It is set to input 2 by default which is a default HiHat cymbal input. It can be set to any even input number corresponding to a Bow input of a dual (3 zone) cymbal.

#####BowSO/EdgeSO/BellSO:
and
#####BowSO2/EdgeSO2/BellSO2:

BowSO: G1    44 

Set the note number which MegaDrum will send when you hit HiHat on the Bow/Edge/Bell and the HiHat pedal is between fully open and half pressed (half open).

#####BowHO/EdgeHO/BellHO:
and

#####BowHO2/EdgeHO2/BellHO2:

BowHO: G1    44 

Set the note number which MegaDrum will send when you hit HiHat on the Bow/Edge/Bell and the HiHat pedal is half pressed (half open).

#####BowSCL/EdgeSCL/BellSCL:

BowSCL:G1    44 

Set the note number which MegaDrum will send when you hit HiHat on the Bow/Edge/Bell and the HiHat pedal is between half pressed (half open) and fully pressed.

#####BowCL/EdgeCL/BellCL:

BowCL: G1    44 

Set the note number which MegaDrum will send when you hit HiHat on the Bow/Edge/Bell and the HiHat pedal is fully pressed.

#####Chick:

Chick: F#2   42 

Set the note number which MegaDrum will send when you do HiHat chicks.

#####Splsh:

Splsh: A#2   46 

Set the note number which MegaDrum will send when you do HiHat splashes.

#Misc
Next screen after 'Firmware ver' is MIDI Speed:

<MIDI Speed    >
<     USB+MIDI >
(Atmeg (old) based MegaDrum only) It can be set to "USB+MIDI", "USB only 1", "USB only 2", "USB only 3". "USB+MIDI" uses standard 31.25k MIDI speed and is compatible with older PIC USB MIDI firmware. "USB only 1", "USB only 2" and "USB only 3" switches the speed to 125k, 187.5k and 250k. Depending on the PCB and soldering quality and chips samples not all "USB only x" will work properly. Switching to higher speeds will only work with a newer version (21/04/2011) of PIC USB MIDI firmware. Switching to higher USB MIDI speeds reduces overall latency over USB by 0.5-1.5ms.
This is a Global setting so when you change this setting it is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####AutoLoad Config:

<AutoLoad Conf >
<          No  >
When set to Yes, MegaDrum will automatically load last saved/loaded config and drum map upon powering up. You can by pass auto loading config even if you set it to Yes by hold the key RIGHT while switching MegaDrum on. It will then load default settings.
This is a Global setting so when you change this setting between Yes and No the setting is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####AltEncoders:

<AltEncoders   >
<          No  >
MegaDrum can be used with two types of rotary encoders - one with one pulse per detent, another with two pulses per detent. For encoders with one pulse per detent set AltEncoders to No, for encoders with two pulses per detent set AltEncoders to Yes. Before the encoders can function properly you first need to set AltEncoders to a proper value with buttons only.
This is a Global setting so when you change this setting between Yes and No the setting is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####MaxInputs:

<MaxInputs     >
<           56 >
Here you can set the maximum number of inputs used. The lower the MaxInputs the more Configs/DrumMaps you can save in non-volatile memory but it will limit you to the number of inputs set here. When you change MaxInputs to a new number don't try to load Configs/Drum Maps saved previously - it can cause MegaDrum to misbehave.
This is a Global setting so when you change this setting it is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####ConfigNamesEn:

<ConfigNamesEn >
<           No >
Enables/disables support for editable Custom Nonfig Names. Default is No (disabled). When set yo Yes, it enables support for editable Custom Config Names and in this case MegaDrum uses more internal non-volatile (EEPROM) memory for storing each Config thus reducing the number of Configs/Drum Maps which can be saved. Custom Config Names themselves can only be changed via SysEx messages, e.g. using MegaDrum Manager.
This is a Global setting so when you change this setting it is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####CustomNamesEn:

<CustomNamesEn >
<           No >
Enables/disables support for editable Custom Pads Names. Default is No (disabled). When set yo Yes, it enables support for editable Custom Pads Names and in this case MegaDrum uses more internal non-volatile (EEPROM) memory for storing each Config thus reducing the number of Configs/Drum Maps which can be saved. Custom Pads Names themselves can only be changed via SysEx messages, e.g. using MegaDrum Manager. The editable Custom Pads names are available as last 32/16/2 names in PadName->Name selection list. The number of available editable Custom Pads Names depends on a chip used: Atmega1284 - 32 editable custom pads names, Atmega644 - 16, Atmega32/324 - 2.
This is a Global setting so when you change this setting it is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####MIDI2ForSySex:

<MIDI2ForSySex >
<           No >
(STM32 based MegaDrum only) When set to Yes the second USB MIDI Port will transmit only SySex messages. Default is No. This is implemented to prevent MIDI softs/synths listening on all MIDI ports from receiving the same Note On/Off messages twice.
This is a Global setting so when you change this setting it is only saved in no-volatile (EEPROM) memory when you exit the Menu. So, as a consequence, if you change it and switch MegaDrum off straight away to test it without exiting the Menu, it will revert to a previous state before the change.

#####Load ROM Kit and Load ROM Map:

<Load ROM Kit  >
<           No >

<Load ROM Map  >
<           No >

Loading predefined Kits/Drum Maps intended for MegaDrum newcomers to get a quick start.
As of now there are 3 predefined kits/maps: Default, Basic and Advanced.
Basic and Advanced kits/maps are developed by Anders ( angr77) to match Addictive Drums MegaDrum map and Anders' reference Basic and Advanced kits.

#####CurrentConfig:

<CurrentConfig >
<           1  >
Shows currently loaded/saved config used by MegaDrum.

#####Save Config:

<Save Config   >
<           No >
When on this screen you can save your current MegaDrum configuration into non-volatile memory. You can save several configurations into different memory slots. The number of Config slots depends on a type of Atmega  and the number of inputs set in MaxInputs. Select a slot you want to save the configuration into with keys UP/DOWN and then press the key RIGHT. After a few seconds it will show 'Done' indicating that the configuration has been saved.

#####Load Config:

<Load Config   >
<           No >
When on this screen you can load a previously saved MegaDrum configuration from non-volatile memory. Select a slot you want to load the configuration from with keys UP/DOWN and then press the key RIGHT. After a few seconds it will show 'Done' indicating that the configuration has been loaded.

#####Save DrumMap:

<Save DrumMap  >
<           No >
When on this screen you can save the current drum map into non-volatile memory. Drum map is a mapping (matching) between pad inputs and notes assigned to those pads. Select a slot you want to save the drum map to with keys UP/DOWN and then press the key RIGHT. After a few seconds it will show 'Done' indicating that the drum map has been saved. The number of DrumMap slots depends on a type of Atmega  and the number of inputs set in MaxInputs.

#####Load DrumMap:

<Load DrumMap  >
<           No >
When on this screen you can load a previously saved drum map from non-volatile memory. Select a slot you want to load the drum map from with keys UP/DOWN and then press the key RIGHT. After a few seconds it will show 'Done' indicating that the drum map has been loaded.

#####SysEx ChainID:

<SysEx ChainID >
<            0 >
When you use MegaDrumManager to control MegaDrum and have two (more?) modules chained together over MIDI ports, you must assign different ChainIDs to each module to be able to control each unit individually. Default ChainID is 0.

#####Send ConfSysex:

<Send ConfSysex>
<              >
From this screen you can manually force MegaDrum to send the full current configuration as a set of SysEx MIDI messages. You may want to do it if you cannot use MegaDrumManager and need to save the configuration externally using e.g. MIDI-OX. You can later send the whole set of SysEx MIDI messages back to MegaDrum, e.g. again using MIDI-OX, to apply saved configuration. While in this screen press the key UP to send the configuration.

#####MIDIThru Enbld:

<MIDIThru Enbld>
<           No >
Enable/disable MIDI Thru. By default it is set to No (disabled). When enabled MegaDrum will send out all MIDI messages it receives over MIDI.

#####NoteOff Delay:

<NoteOff Delay >
<          200 >
This setting configures how many milliseconds should pass before a Note Off MIDI message is sent after a previous Note On message. Can be set between 20 and 2000 milliseconds (0.02 - 2 seconds).

#####PressRoll Time:

<PressRoll Time>
<            0 >
Maximum time out in milliseconds between consecutive hits for "pressroll" detection.  If a next hit follows a previous hit in less than this time out then the note value for the hit will be taken from PNote (PBNote for 3rd zones) rather than from Note or ANote (BNote or ABNote for 3rd zones). Can be set between 0 and NoteOff Delay value.

#####Latency:

<Latency       >
<           40 >
This setting should have probably be called something like Group scan frequency. Internally MegaDrum scans all inputs every 10-30 microseconds for presence of signals. Then, very simplified, every <Latency> period MegaDrum scans inputs states to see if any of the inputs registered signals and sends MIDI messages for triggered inputs. Lowering this setting will reduce latency and may degrade level detection precision. Raising this setting may improve level detection precision and will increase latency. Latency can be changed between 10 and 100 which corresponds to 1 and 10 milliseconds. Default is 40 - 4 millisecond. Also when it is set to an odd value (e.g. 21, 23, 25 and so on) it enables a visual cue to see if pads Thresholds are set too low - when a pad is hit lightly but not enough to exceed Threshold level the VU meter for the pad set to a maximum but no MIDI signal is sent and the LED stays off. If VU meters start to go off without pads being hit then Thresholds for corresponding inputs are set too low.

#####OctaveShift:

<OctaveShift   >
<           No >
It is used to make MegaDrum display all notes names in a desired octave. By default it is set to 2 (maximum value). As an example, with the default OctaveShift the default Kick note (36) will sbe shown as from octave 2.

#####Big VU Meter:

<Big VU Meter  >
<           No >
When set to No (default) each of 32 blocks on an LCD is used as an individual VU meter for every input. The resolution of each of these small VU meters is 16, i.e. one bar per 16 adjacent MIDI levels giving 8 bars for 128 MIDI levels. The resolution of the Big VU Meter is much better, approximately 100 bars for 128 MIDI levels. The next, 'Big VU Split', option determines what is shown in the big VU meter.

#####Big VU Split:

<Big VU Split  >
<           No >
When set to No (default) (and Big VU Meter is set to Yes) the whole top row of the LCD is dedicated to HiHat pedal position and the whole bottom row of the LCD shows hit levels from all inputs on a big single VU meter.
When set to Yes (and Big VU Meter is set to Yes) the whole top row shows hit levels from all even (Head/Bow) inputs and the whole bottom row of the LCD shows hit levels on odd (Rim/Edge) inputs. The HiHat pedal position is not shown in this mode.

#####Quick Access:

<Quick Access  >
<           No >
When set to Yes you can quickly jump between inputs in the Menu rather than navigate to each input using LEFT/RIGHT keys. First enter the Menu, then press the HiHat pedal and then hit a pad you want to configure. Whenever you hit another pad while still holding the HiHat pedal pressed and still in the Menu, it will jump to the last hit pad input. You have to make a Splash (quickly press/release the pedal) twice for Quick Access to become effective. 
When set to No you can quickly load next/previous drum map by pressing keys UP/DOWN while not in the Menu and holding the HiHat pedal pressed. May be useful for live performances to quickly load different drum maps?

#####TriggeredInCC:

<TriggeredInCC >
<           No >
When set to Yes and you hit a pad, MegaDrum will send a special MIDI CC message telling exactly which input was triggered. This option allows MegaDrum Manager (MDM) or MDCommander to quickly switch between inputs configs.

#####AltFalseTrSupp:

<AltFalseTrSupp>
<           No >
When set to Yes, MegaDrum uses alternative (old) algorithm for false triggering suppression which was the default algorithm in firmware versions before the version 20110703. It has an effect on XTalk/Rettriger/DynLvl/DynTime settings.

#####InputsPriority:

<InputsPriority>
<           No >
When set to Yes the first 3/4th of Head/Bow inputs are given slightly higher priority (sampled more often) then the rest of inputs.

#####AltNoteChoking:

<AltNoteChoking>
<           No >
When set to Yes, AltNote from inputs settings is used for cymbals choking instead of Aftertouch. When the choke switch is pressed, MegaDrum will send Note On with AltNote note and when the switch is released MegaDrum will send Note Off with AltNote note.

#####NoiseFilter:

<NoiseFilter   >
<            5 >
(STM32F205 based MegaDrum only). Noise Filtering level. Default is set 5. Setting it too high may have negative effect on Positional sensing.

#####PositionalIn:

<PositionalIn  >
<     SnareH 4 >
Selects which input the further 3 positional sensing settings (PositionalLv, PositionalLow, PositionalHi) are to be configured for. You can choose SnareH (4), RideH (6), CrushH (8) or Tom1H(10) here.

#####PositionalLv:

<PositionalLv  >
<           No >
Enables/disables Positional Sensing (PS) on a selected input. By default it is disabled. To enable PS on a selected input set Positional to 1, 2 or 3 (corresponding to three variations of PS). The next two settings, PositionalLow and PositionalHigh, need to be adjusted for the best PS accuracy. PositionalLow and PositionalHigh are adjusted so that to get a full range of detected positions (and MIDI CC messages) from a rim (PositionalLow) to a centre (PositionalHigh).
The default PositionalLow and PositionalHigh are good starting values for Roland PD-125X with Positional set to 1.
When Positional set to 2 the good starting values for Roland PD-125x are ~16 and ~30. With Positional set to 2, MinScan must be set so that to cover a full half wave which is ~30-40 (3-4ms) for Roland PD-125X.
Positional set to 3 is almost the same as 2 but with slightly different algorithm so you may need to set PositionalLow and PositionalHigh slightly higher.
With PS enabled and LCD showing one of the PS settings, when hitting the snare you can see in the botom left of the LCD the relative position of the hit as calculated by MegaDrum: ^ symbol shown more to the left for centre hits and more to the right for close to rim hits. You will also see the calculated PS value of the hit for currently selected PS algorithm (1, 2 or 3) which you should use for setting PositionalLow and PositionalHi properly.
As experimental feature it may or may not work for you. There are a few requirements:

it may work only with mesh type pads with a centrally positioned piezo.
the pad must not be too hot. If it is too hot it must be "cooled" with a voltage divider.
the first half wave of a signal from a pad should be positive, e.g my Pintech mesh snare is such a pad. Most of other mesh pads out there, like Roland, Drumtec and etc, produce a negative first half wave. In this case you will have to use a full wave precision rectifier. See http://www.megadrum.info/forums/viewtopic.php?f=3&t=1215 for details.

Next two screens are PositionalLow and PositionalHi:

<PositionalLow >
<            10>

<PositionalHi  >
<            20>
Use these two settings to adjust PS accuracy as described in the previous screen.

#####Set All Chnnls:

<Set All Chnnls>
<           No >
Use this screen to globally change MIDI channels on all inputs. Press UP/DOWN to choose a MIDI channel and then press RIGHT to apply this setting to all inputs.

#####Set All Curves:

<Set All Curves>
<           No >
Use this screen to globally change velocity curves on all inputs. Press UP/DOWN to choose a velocity curve and then press RIGHT to apply this setting to all inputs.

#####Set All Ccross:

<Set All Cross >
<           No >
Use this screen to globally change Crosstalk(XTalk) levels on all inputs. Press UP/DOWN to choose a Crosstalk level and then press RIGHT to apply this setting to all inputs.

#####Set All EdgeSw:

<Set All EdgeSw>
<           No >
Use this screen to automatically set Threshold on all inputs which are configured as 'Switch' type for all 2 and 3 zone pads/cymbals. Press UP/DOWN to change it to Yes, then press RIGHT and it will then show 'Working'. Now hit a few times edge zones of all piezo/switch and piezo/switch/switch pads/cymbals. When done, press any button to finish. Note, that you must use only this option to set both Edge and Bell Threshold for Roland style 3 way cymbals.

#####Set All BellSw:

<Set All BellSw>
<           No >
Use this screen to automatically set BThreshold on all inputs which are configured as 'Switch' for all 3 zone Yamaha style pads/cymbals. Press UP/DOWN to change it to Yes, then press RIGHT and it will then show 'Working'. Now hit a few times bell zones of all piezo/switch/switch pads/cymbals. When done, press any button to finish.

#####Set All Thres:

<Set All Thres >
<           No >
Use this screen to globally change Threshold on all inputs. Press UP/DOWN to choose a Threshold and then press RIGHT to apply this setting to all inputs.

#####Set All Retrs:

<Set All Retrs >
<           No >
Use this screen to globally change Rettrigger time on all inputs. Press UP/DOWN to choose Retrigger time and then press RIGHT to apply this setting to all inputs.

#####Set All MinScn:

<Set All MinScn>
<           No >
Use this screen to globally change Minimum scan (MinScan) time on all inputs. Press UP/DOWN to choose Minimum scan time and then press RIGHT to apply this setting to all inputs.

#####Set All DynLvl:

<Set All DynLvl>
<           No >
Use this screen to globally change Dynamic Threshold level (DynLevel) on all inputs. Press UP/DOWN to choose a  Dynamic Threshold level and then press RIGHT to apply this setting to all inputs.

#####Set All DynTim:

<Set All DynTim>
<           No >
Use this screen to globally change Dynamic Threshold Decay time (DynTime) on all inputs. Press UP/DOWN to choose Dynamic Threshold Decay time and then press RIGHT to apply this setting to all inputs.

#####CustomCurve1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16:

<CustomCurve1  >
<P1:         2 >
Here you can configure 16 custom curves which you can use in Curve settings of pads. Each custom curve has 9 sub menus P1-P9. Each of P1-P9 represents a midpoint for setting a relation of input signals to output value where P1 is a weakest possible input signal and P9 is a highest input signal. By default the 4 custom curves are copies of Linear, Log, Exp and S type curves.
Here is a graphical demonstration for 3 examples - Log, Exp and S type curves:

Curves

For the Log curve in the example P1-9 midpoints values are:
2 78 122 157 184 208 226 243 255

For the Exp curve in the example P1-9 midpoints values are:
2 13 30 48 72 99 134 178 255

For the S curve in the example P1-9 midpoints values are:
2 60 100 125 127 130 160 200 255

The minimum value for any midpoint is 2 which will translate into a MIDI velocity level 1
The maximum value for any midpoint is 255 which will translate into a MIDI velocity level 127

#####All Gains Low:

<All Gains Low >
<           No >
(Atmega (old) based MegaDrum only). Not used on newer ARM versions. Setting this to Yes will disable all individual input Gain levels and make Gain even lower than 'Gain Level' 0. It could be used if all your pads are 'hot' and to get a better dynamic range with such pads.

#####AltSamplingAlg:

<AltSamplingAlg>
<           No >
(STM32F205 based MegaDrum only). Enable/disable Alterantive Sampling algorithm (AltSamplingAlg setting) on MegaDrum with the latest STM32F205RCT6 MCU. The new algorithm reduces digital noise and may allow you to set Thresholds lower and as a result it may improve sensitivity.
