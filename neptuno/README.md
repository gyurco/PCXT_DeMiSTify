# [IBM PC/XT](https://en.wikipedia.org/wiki/IBM_Personal_Computer_XT)  [DeMiSTified](https://github.com/robinsonb5/DeMiSTify)  - NeptUNO port

07/07/22 NeptUNO port DeMiSTified by @somhi from original MiSTer PCXT core  https://github.com/spark2k06/PCXT_MiSTer

[Read this guide if you want to know how I DeMiSTified this core](https://github.com/DECAfpga/DECA_board/tree/main/Tutorials/DeMiSTify).

Read the main [Readme](https://github.com/somhi/PCXT_DeMiSTify) also.

### STATUS

* CGA VRAM with 128 kB for all Tandy games now available.


* **UART port needs to be used to load the OS through the serdrive app.** Load OS using Serial Rx/Tx cable.
  * **Current binary file uses Rx/Tx from the Edge connector, so either and Edge addon is required or the core must me resintesized to expose the Rx/Tx pins in the PS2 mouse port.**



### Compile the project in Quartus:

Project already has the Demistify firmware already generated so if you clone it recursively then you can open the project with Quartus:

```sh
git clone  --recursive https://github.com/somhi/PCXT_DeMiSTify

#check comments on top of /neptuno/neptuno_top.vhd in case additional actions are needed

#Load project in Quartus from /neptuno/PCXT_neptuno.qpf
```



### Instructions to Full compile the project for a specific board:

```sh
git clone https://github.com/somhi/PCXT_DeMiSTify
cd PCXT_DeMiSTify
#Do a first make (will finish in error) but it will download missing submodules 
make
cd DeMiSTify
#Create file site.mk in DeMiSTify folder 
cp site.template site.mk
#Edit site.mk and add your own PATHs to Quartus (Q18)
gedit site.mk
#Go back to root folder and do a make with board target (deca, neptuno, uareloaded, atlas_cyc). If not specified it will compile for all targets.
cd ..
make BOARD=neptuno
#when asked just accept default settings with Enter key
```

After that you can:

* Load project in Quartus from /neptuno/PCXT_neptuno.qpf



### OSD Controls

* F12 show/hide OSD 
* Long F12 toggles VGA/RGB mode
* The user button KEY0 resets the controller (so re-initialises the SD card if it's been changed, reloads any autoboot ROM.) The OSD Reset menu item resets the core itself.
* The user button KEY1 opens the OSD

