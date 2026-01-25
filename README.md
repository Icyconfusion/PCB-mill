# PCB-mill
A small cnc machine for milling FR4 pcbs using an arduino UNO. It is also capable of CNC engraving at low Z travels. You could potentially do laser engraving if you added a laser to it.

I created this project as a means to create PCBs quickly at home, removing the time and cost of ordering PCBs online. Now I can make 2 layer PCBs at home on my desk for quick prototyping. It also taught me a few things about routing with power draws.

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
The components required for this project are a PSU, an MCU, a spindle or spindle kit, stepper motors, stepper drivers, and limit switches. For the MCU I decided on an arduino UNO because of its pin availability and GRBL compatibility. To power the UNO, I will use an LM2596 buck converter connected to the VIN pin. The PSU is 24v logic, 200w. Power is introduced to the PCB by screw terminals, and powers the VMOT pin of drivers, and 5v logic through the arduino. The steppers are Nema 17 because of their cheap cost and reliability. Drivers used to control these are A4988, which support 1/16 microstepping (why all MS pins are connected to 5v).


## Schematic
<img width="1684" height="757" alt="image" src="https://github.com/user-attachments/assets/93f06778-8977-41c3-aa99-a4eb274e7dfb" />


## PCB
The PCB for this project interfaces the power supply, steppers, arduino and endstops. It uses wide traces to deliver power from the PSU screw terminals, and has connectors from leftover pins for future connections.
<img width="1092" height="844" alt="image" src="https://github.com/user-attachments/assets/d6218747-62ee-43d4-b0b5-1abb7ab3e8f1" />



# **Firmware**
The project uses the GRBL library to command the machine. GRBL is a program that instructs the arduino to respond to G-code, sent by a computer. No modifications to GBRL are required other than tweaking default steps/mm, speed, acceleration etc to the machine. To install, copy the edited firmware folder into Arduino IDE libraries, include it in a sketch, and then flash.

# **BOM**









