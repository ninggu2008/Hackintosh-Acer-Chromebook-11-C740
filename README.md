# Hackintosh-Acer-Chromebook-11-C740
Files and notes to get MacOS running on a Acer Chromebook 11 C740

Confirmed working on:

MacOS: Big Sur 11.0.1		

MrChromebox coreboot: 4.12		

OpenCore: 0.6.3		

Disclaimer: This is not meant to be a thorough guide or walkthrough. It is merely a dump of files and notes to get MacOS working on a Acer Chromebook 11 C740. I will try to keep this updated as I update my Chromebook to future MacOS releases. It's not guaranteed to work on your specific device. If it doesn't, you likely need to make some sort of changes to the supplied config.plist. I do not know what those changes may be. I am not responsible for any damage done or data lost by attempting this.		

Update 11/29/2020

OpenCore 0.6.3		
Confirm Big Sur official release compatibility		
Requirements:		

Core i3 or Core i5 processor		
MrChromebox's coreboot firmware 4.12		
OpenCore 0.6.3		
Minimum of a 32GB SSD		
Minimum 64GB recommended		
Origin WiFi&Bluetooth card AC3160（https://github.com/OpenIntelWireless/itlwm）		
MacOS installer flash drive		
See the guides linked in Basic Installation Steps below		
Notes:
Most top row keys are mapped with the custom VoodooPS2Controller.kext		
Back arrow key = Previous track		
Forward arrow key = Next track		
Refresh key = Play/Pause		
Brightness down key = Brightness down		
Brightness up key = Brightness up		
Mute key = Mute		
Volume down key = Volume down		
Volume up key = Volume up		
What's Working:		

Just about everything!		
Graphics（HDMI with Audio out）		
Audio out		
Bluetooth		
Wifi		
LCD Backlight Control		
Touchpad		
Keyboard with key remapped		
Sleep		
etc……		

What's Not Working:

Most DRM does not work. This means no Apple TV shows, Hulu, Netflix (in Safari), Amazon Prime streaming, etc.
This isn't specific to the Dell CB13. DRM simply does not work on an iGPU only Hackintosh			
Internal Microphone		

To Do:

Enjoy MacOS!		
Before Getting Started		

I strongly suggest becoming familiar with Hackintoshing before jumping into this. Know the downsides, shortcomings, and difficulties. Read through the dortania guide, poke around on r/hackintosh, have a look around InsanelyMac and TonyMacX86 (even though their tools aren't used here, they still have a lot of useful information), and do some general web searches. Even if a lot of it doesn't make sense, just reading through it and becoming familiar with terms will be helpful!
Updates to MacOS, OpenCore, or firmware may break your installation! I will likely be keeping my device up to date so check back here before doing any MacOS, OpenCore, or firmware updates! The latest confirmed working versions will always be at the top of the this page.
Don't let this section scare you off! Once MacOS is up and running on your system, it is very stable!		
Basic Installation Steps		

Install/update MrChromebox coreboot firmware if you haven't already		
Create a MacOS installer flash drive		
A guide can be found here		
Download OpenCore 0.6.3 and copy only the files shown in this screenshot to your flash drive, keeping the folder structure as seen in the image		
Download all of the required files		
Be sure to make any edits mentioned - particularly to config.plist and VoodooI2CElan.kext		
Move the required files to their appropriate locations on your installer flash drive		
Your EFI folder should look like this - make sure all of the files are there 		
Boot to your installer and install MacOS		
Boot into MacOS using your installer flash drive and copy the EFI folder from you installer flash drive to the EFI partition of your internal SSD - you can mount the EFI partition with MountEFI		
More info can be found here		
Follow the post install steps below		
Post-Install		

Disable force click in trackpad settings		
Disable hibernate with "sudo pmset -a hibernatemode 0"		
Map Full Screen and Mission Control keys		
Map Full Screen button (F4) to full screen in: System Preferences > Keyboard > Shortcuts > App Shortcuts		
Example screenshot		
Map Mission Control key (F5) Mission Control in: System Preferences > Keyboard > Shortcuts > Mission Control		
Example screenshot		
Optional: Give OpenCore a GUI menu and boot chime		
Use this OCEFIAudio_VoiceOver_Boot.wav as it is resampled to work with the CB13		
If you want a full Hackintosh guide (not Chromebook specific), I suggest this one: https://dortania.github.io/OpenCore-Install-Guide/ - most of the files in this repo were created using this guide so you won't need to generate them yourself. Simply pull them from here as you go through the guide.		

Required Files		

OpenCore Config		

Place config.plist in /EFI/OC/		

Use ProperTree to make the following edits to the config-base.plist file		

Follow the PlatformInfo portion of this guide to edit the config.plist		
You can use GenSMBIOS to generate the SMBIOS info		
Use a MacBookPro12,1 profile		
In the config.plist, you need to fill in values for: SystemProductName, SystemSerialNumber, MLB, SystemUUID, and ROM		
Use your MAC address without the colons for the ROM field (You did get your MAC address, right?)		
Be sure to rename the config file to config.plist		
OpenCore Drivers		

These are included with the OpenCore download unless noted otherwise. Place these in /EFI/OC/Drivers		

AudioDxe.efi		
HfsPlus.efi		
OpenCanopy.efi		
OpenRuntime.efi		

SSDT files		
Place these in /EFI/OC/ACPI		

SSDT-EC.aml		
Creates a phony EC controller - required to boot Catalina		
SSDT-PLNF.aml		
Enables LCD backlight control		
SSDT-PLUG.aml		
Enables proper CPU power management		
SSDT-KBBL.aml		
Required for keyboard backlight control		

Required Kexts		

Place these in /EFI/OC/Kexts		

AppleALC.kext		
Lilu.kext		
WhateverGreen.kext		
VirtualSMC.kext		
SMCBatteryManager.kext		
SMCProcessor.kext		
SMCSuperIO.kext		
AirportItlwm.kext		
IntelBluetoothFirmware.kext		
IntelBluetoothInjector.kext		
USBPorts.kext		
VoodooI2C.kext		
VoodooI2CElan.kext		



Credits & Sources (in no particular order and maybe missing some)		

Apple		
https://github.com/MrChromebox		
https://github.com/acidanthera		
https://github.com/alexandred		
https://github.com/RehabMan		
https://github.com/corpnewt		
https://www.insanelymac.com/		
https://www.tonymacx86.com/		
https://reddit.com/r/hackintosh		
https://reddit.com/r/chrultrabook		
https://github.com/TheRandMan/VoodooPS2-CB13/		
https://dortania.github.io/vanilla-laptop-guide/		
