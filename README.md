# PCB-mill
A small cnc machine for milling FR4 pcbs using an arduino UNO. It is also capable of CNC engraving at low Z travels. You could potentially do laser engraving if you added a laser to it.

**Note to reveiwer:** I have exported the assembly as .STEP, but I had trouble so there is a zipped .stl of the assembly just in case the .step doesn't work. Also I am updating my BOM with the current prices (since submission) so it might be slightly different (most are cheaper) from my cart pictures. Thank you :) Also, yes the spindle is the cheapest option (prices are in AUD so 50-60 USD is 75-90 AUD). The spindle I am purchasing also includes PSU.

I created this project as a means to create PCBs quickly at home, removing the time and cost of ordering PCBs online. Now I can make 2 layer PCBs at home on my desk for quick prototyping. It also taught me a few things about routing with power draws. To use the project, you simply stream Gcode to the machine over usb form a computer, and the machine will replicate it.

# **Assembly**
<img width="1024" height="651" alt="image" src="https://github.com/user-attachments/assets/3a24b912-21b6-4d6f-9ddc-5160c301b258" />

The assembly of the project is made up of a few key components. The idea is a stationary, square base with linear rails making the Y axis. The H frame moves along thiscarrying the X and Z axis. Motion is achieved through leadscrews.

To start assembly, there is the base frame that the whole machine is supported by. 4 2020 300m T slot Aluminium profiles are arranged in a square, with M5 T nuts and 90 degree connectors holding them in place. Two 300mm MGN12 linear rails are attached to the top edge of the profiles using M3 T nuts.
<img width="1089" height="644" alt="image" src="https://github.com/user-attachments/assets/490b81c1-1939-444a-aea6-3aca947da96d" />

Now onto the H. The H moves back and forth along the linear rails attached before, this is the Y axis. The H moves along the rails by a 3d printed bracket, to attach it to the MGN12H carriage. Use 4 M2 screws to attach each bracket to the carriages, then 4 M5 T nuts to attach profiles to each bracket.
<img width="613" height="446" alt="image" src="https://github.com/user-attachments/assets/79e0e39d-4e84-4223-8bc2-4bce063246a1" />
<img width="780" height="579" alt="image" src="https://github.com/user-attachments/assets/2a779015-88fb-41a6-a0e0-ce61f2bf4928" />
<img width="588" height="477" alt="image" src="https://github.com/user-attachments/assets/4fe5808b-c22d-4e51-a419-aaf3d8ebdfbd" />
<img width="434" height="283" alt="image" src="https://github.com/user-attachments/assets/888a1089-d213-489c-bda3-c1692ebfec8b" />

We now have the two pillars of the H. Attach to 2060 profile to the pillars using M5 T nuts and 90 degree connectors. The bottom edge of the 2060 should be roughly 4 cm from the top of the bracket we assembled (Exactness is not needed as Z leveling and the spindle height on the mount will compensate for this). Attach the linear rails as before.
<img width="1055" height="593" alt="image" src="https://github.com/user-attachments/assets/cd20d2d8-35e7-4cb1-a864-735957b2e14b" />

To assemble the gantry, screw on both rear MGN12H carriages, and linear rails. Attach the limit switch and press the bearing into place. Then assemble the spindle plate and slide onto the gantry.
<img width="752" height="578" alt="image" src="https://github.com/user-attachments/assets/f44e18b0-d7fe-4c03-bc28-d2c4e75edbd2" />
<img width="555" height="541" alt="image" src="https://github.com/user-attachments/assets/6ad73dcc-60b5-4a4f-bbe9-874fa794e95b" />
<img width="580" height="732" alt="image" src="https://github.com/user-attachments/assets/0834425a-e174-40bb-bef8-57d840088f43" />

Finally, attach the motor, coupler, nutblock and rod, and then slide onto the H frame. The H frame can now slide onto the base frame rails.
<img width="731" height="541" alt="image" src="https://github.com/user-attachments/assets/290e100c-cd19-4da7-9dc5-4cf3fc8e62cc" />
<img width="779" height="616" alt="image" src="https://github.com/user-attachments/assets/439dbb93-7448-4d89-9226-ee322ee0df0a" />

Last steps, attach a bed/spoilboard of wood with M5 T nuts. Screw nutblocks to each Y carriage, then mount all 4 Y axis brackets, and their fixing blocks (plus limit switch on one). Now you can feed the rods through and attach the GT2 gears.
<img width="524" height="372" alt="image" src="https://github.com/user-attachments/assets/7470526b-8d08-4dcc-94e6-0ab97417f92c" />

Mount the belt plate, motor and drive gear using M5 T nuts, then attach the pulleys.
<img width="596" height="542" alt="image" src="https://github.com/user-attachments/assets/bf0459b4-7219-4b21-ba52-0b83df87b225" />
<img width="403" height="361" alt="image" src="https://github.com/user-attachments/assets/7d8999be-178d-48d5-b1a3-c8fd64c451cc" />

Finally, attach the X motor bracket, motor and limit switch. The fixing block attaches to the profile on the other side using the T nuts already installed on it. Now you can feed through the leadscrew and assembly is done.
<img width="1080" height="447" alt="image" src="https://github.com/user-attachments/assets/5d7e3d8c-4780-47ba-9eac-86854904ca0c" />
<img width="974" height="546" alt="image" src="https://github.com/user-attachments/assets/2d909ee4-6a4a-4774-bdd7-7d54f5e173b4" />

# **Electronics**
The components required for this project are a PSU, an MCU, a spindle or spindle kit, stepper motors, stepper drivers, and limit switches. For the MCU I decided on an arduino UNO because of its pin availability and GRBL compatibility. To power the UNO, I will use an LM2596 buck converter connected to the VIN pin. The PSU is 24v logic, 200w. Power is introduced to the PCB by screw terminals, and powers the VMOT pin of drivers, and 5v logic through the arduino. The steppers are Nema 17 because of their cheap cost and reliability. Drivers used to control these are A4988, which support 1/16 microstepping (why all MS pins are connected to 5v). The 500w spindle comes as a kit including a mount and dedicated PSU. This kit also has speed control to stop the spindle. I am using standard 3 pin limit switches.


## Schematic
<img width="1684" height="757" alt="image" src="https://github.com/user-attachments/assets/93f06778-8977-41c3-aa99-a4eb274e7dfb" />
Cirkit designer: https://app.cirkitdesigner.com/project/915723a2-d3f0-4d32-8109-c895c4144bcc
<img width="841" height="672" alt="Screenshot 2026-02-18 115255" src="https://github.com/user-attachments/assets/ba750bf0-12a6-4a1e-b29a-8d592fe65479" />



## PCB
The PCB for this project interfaces the power supply, steppers, arduino and endstops. It uses wide traces to deliver power from the PSU screw terminals, and has connectors from leftover pins for future connections.
<img width="1092" height="844" alt="image" src="https://github.com/user-attachments/assets/d6218747-62ee-43d4-b0b5-1abb7ab3e8f1" />



# **Firmware**
The project uses the GRBL library to command the machine. GRBL is a program that instructs the arduino to respond to G-code, sent by a computer. No modifications to GBRL are required other than tweaking default steps/mm, speed, acceleration etc to the machine. To install, copy the edited firmware folder into Arduino IDE libraries, include it in a sketch, and then flash. **It is installed as a zip.**

# **BOM**

### CAD

|Quantity|Name|Picture|
|--------|----|-------|
| 1 | Spindle plate | <img width="675" height="451" alt="image" src="https://github.com/user-attachments/assets/f4f76d41-1838-4317-9d8a-ff709e15b6e5" /> |
| 1 | Gantry plate | <img width="567" height="614" alt="image" src="https://github.com/user-attachments/assets/6285ef4c-a36e-4e26-aa71-f8b299501174" /> |
| 1 | X motor bracket | <img width="518" height="576" alt="image" src="https://github.com/user-attachments/assets/648021ec-2702-491f-81de-490d8c67f869" /> |
| 2 | Y carriage | <img width="632" height="555" alt="image" src="https://github.com/user-attachments/assets/f7edcb3a-454c-4e05-9fb7-dee49ce696b4" /> |
| 1 | Y bearing bracket with switch | <img width="757" height="593" alt="image" src="https://github.com/user-attachments/assets/935fea4a-20db-482b-b633-ecb436667b53" /> |
| 3 | Y bearing bracket | <img width="523" height="515" alt="image" src="https://github.com/user-attachments/assets/b4236f06-82d1-4c1a-9237-2909b8e5005b" /> |
| 1 | Belt plate | <img width="731" height="601" alt="image" src="https://github.com/user-attachments/assets/acbe5c30-0acc-4a8e-8016-523317a8e281" /> |

### PCB

2 layer PCB that is 127x118mm.
<img width="1092" height="844" alt="image" src="https://github.com/user-attachments/assets/d6218747-62ee-43d4-b0b5-1abb7ab3e8f1" />

### Parts
3x Nema 17 stepper motor

1x Arduino uno

3x A4988 stepper driver

1x 24v 200w PSU

1x 500w Spindle kit

1x LM2596 Buck converter

3x Limit switch

1x V bit

1x Drill bit

1x End mill

1x Collet

6x 300mm 2020 T slot aluminium profile (can do 4x300mm and 2x 200mm, but 6x300mm ended up being cheaper)

1x 300mm 2060 T slot profile

8x 90 degree connector

42x M5 T nut

42x M5 screw

32x M3 screw

32x M3 T nut

1x 100mm T8x8 Leadscrew

3x 300mm T8x8 leadscrew

2x 100mm MGN12 linear rail (with MGN12H carriage)

4x 300mm MGN12 linear rail (with MGN12H carriage)

4x T8x8 nutblock 2mm pitch

2x 5x8mm shaft coupler

1x 5mm bore GT2 timing gear

2x 8mm bore GT2 timing gear

1x GT2 belt (at least 600mm)

2x Toothed GT2 idle pulley

2x Smooth GT2 idle pulley

4x Leadscrew fixing block

1x 16x8x5 bearing

1x spoilboard (any wooden sheet)














