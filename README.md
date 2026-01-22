# PCB-mill
A small cnc machine for milling FR4 pcbs using an arduino UNO. It is also capable of CNC engraving at low Z travels. You could potentially do laser engraving if you added a laser to it.

I created this project as a means to create PCBs quickly at home, removing the time and cost of ordering PCBs online. Now I can make 2 layer PCBs at home on my desk for quick prototyping. It also taught me a few things about routing with power draws.

# **Assembly**
<img width="1024" height="651" alt="image" src="https://github.com/user-attachments/assets/3a24b912-21b6-4d6f-9ddc-5160c301b258" />

The assembly of the project is made up of a few key components. To start assembly, there is the base frame that the whole machine is supported by. 4 2020 300m T slot Aluminium profiles are arranged in a square, with M5 T nuts and 90 degree connectors holding them in place. Two 300mm MGN12 linear rails are attached to the top edge of the profiles using M3 T nuts.
<img width="1089" height="644" alt="image" src="https://github.com/user-attachments/assets/490b81c1-1939-444a-aea6-3aca947da96d" />

Now onto the H. The H moves back and forth along the linear rails attached before, this is the Y axis. The H moves along the rails by a 3d printed bracket, to attach it to the MGN12H carriage. Use 4 M2 screws to attach each bracket to the carriages, then 4 M5 T nuts to attach profiles to each bracket.
<img width="613" height="446" alt="image" src="https://github.com/user-attachments/assets/79e0e39d-4e84-4223-8bc2-4bce063246a1" />
<img width="780" height="579" alt="image" src="https://github.com/user-attachments/assets/2a779015-88fb-41a6-a0e0-ce61f2bf4928" />
<img width="588" height="477" alt="image" src="https://github.com/user-attachments/assets/4fe5808b-c22d-4e51-a419-aaf3d8ebdfbd" />
<img width="434" height="283" alt="image" src="https://github.com/user-attachments/assets/888a1089-d213-489c-bda3-c1692ebfec8b" />

We now have the two pillars of the H. Attach to 2060 profile to the pillars using M5 T nuts and 90 degree connectors. The bottom edge of the 2060 should be roughly 4 cm from the top of the bracket we assembled (Exactness is not needed as Z leveling and the spindle height on the mount will compensate for this).







