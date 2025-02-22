# [IBM PC/XT](https://en.wikipedia.org/wiki/IBM_Personal_Computer_XT)  [DeMiSTified](https://github.com/robinsonb5/DeMiSTify)  -  Atlas CYC1000 port

07/07/22 Atlas CYC1000 port DeMiSTified by @somhi from original MiSTer PCXT core  https://github.com/spark2k06/PCXT_MiSTer

[Read this guide if you want to know how I DeMiSTified this core](https://github.com/DECAfpga/DECA_board/tree/main/Tutorials/DeMiSTify).

Read the main [Readme](https://github.com/somhi/PCXT_DeMiSTify) also.

### STATUS

* HDMI to VGA addon required
* **UART port needs to be used to load the OS through the serdrive app.** Load OS using Serial Rx/Tx cable.
* Credits screen not implemented due to lack of BRAM in this board. F11 pauses the core. If you press it, remember to press it again to continue the core execution.
* Adlib sound not implemented due to lack of BRAM in this board.
* Game Blaster sound (C/MS) not implemented due to lack of LEs
* CGA 32 kB implemented. Some Tandy games are now playable like Prince of Persia, Cool Crocks and Sierra's Manhunter.
* ~~CGA not implemented due to lack of BRAM in this board.~~~~Open OSD with F12 key. Go to Video and change CGA to MDA output. The Splash screen should appear. Then Load XT BIOS ROM (and EC00 XT-IDE 16 kB if not included in the main BIOS) and Reset from OSD.~~



## **Features:**

* ~~HDMI video output~~
* VGA 222 video output is available through an HDMI to VGA adapter
* ~~HDMI audio output~~
* Audio Sigma-Delta output
* ~~Audio output (Midi, I2S)~~
* Joystick (tested with a Megadrive gamepad)

**Additional hardware required**:

* PS/2 keyboard 
* ~~USB keyboard~~ 



### Composite output:

		PI_CLK_I2S_DATA			-- Composite output 0		-- pin 23
		PI_CS_MIDI_CLKBD		-- Composite output 1		-- pin 24

### Compile the project in Quartus:

Project already has the Demistify firmware already generated so if you have cloned recursively then you can open the project with Quartus:

```sh
git clone  --recursive https://github.com/somhi/PCXT_DeMiSTify

#Load project in Quartus from /atlas_cyc/PCXT_atlas_cyc.qpf
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
make BOARD=atlas_cyc
#when asked just accept default settings with Enter key
```

After that you can:

* Load project in Quartus from /atlas_cyc/PCXT_atlas_cyc.qpf



### OSD Controls

* F12 show/hide OSD 
* Long F12 toggles VGA/RGB mode
* The user button KEY0 resets the controller (so re-initialises the SD card if it's been changed, reloads any autoboot ROM.) The OSD Reset menu item resets the core itself.

