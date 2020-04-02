# MigitePad
## *__MigitePad!__* A Numpad/Nav Cluster with QMK Firmware/Kailh Hotswap/OLED/Rotary Encoder! 
![Built Board](/Images/o23xelcs54o41.jpg)
![PCB](/Images/MigitePadPCB.PNG)
Even reversable for you crazies who want a backwards Numpad!*
*OLED will need to be trace cut and bodged if you want it to work backwards

Materials needed:
* 31x Kailh Hotswap Sockets (Technically optional, hotswap through holes are plated)
* 31x 1N4148 or SOD-123F Diodes
* 31x MX style switches
* 1x MJTP1117 Reset Switch
* 1x Pro Micro or equivilant (Pro Micro chip side up for normal orientation, bottom side up for reversed.)
* 3x 2u stabilizers
* 1x EC11 Rotary Encoder
* 1x SSD1306 OLED (Optional)

For the 3D Printable Case:
* 6x 6mm M2 standoffs
* 12x M2 4mm or 5mm screws

OLED and Rotary Encoder code would need to be added to the end of your keymap.c. Still working on a more official OLED config. Example code borrowed and tested as working from the RoMac+, and is located in "QMK Keyboard Folder/migitepad/keymaps/default/keymap.c". Also encluded a default hex file in the QMK Keyboard Folder.
