# ASUS ROG STRIX B360-I GAMING with UHD630 iGPU

## Specifics

- CPU : Intel® Core™ i7-8700 Processor (12M Cache, up to 4.60 GHz)
- Mainboard : ASUS ROG STRIX B360-I GAMING
- Graphics : Intel® UHD Graphics 630, SAPPAIRE RX 570 4GB
- Sound : Realtek ALCS1220A
- Memory : Essencore KLEVV DDR4 16G PC4-21300 CL16 2666MHZ (8GB * 2 Dual Channel)
- M.2 NVME SSD : Samsung PM961 512GB
- 2.5 SATA SSD : Samsung 960 EVO 250GB
- Wireless : BCM94360NG


## BIOS/Clover Bootloader/macOS Version

- BIOS : 2418
- Clover Bootloader : Above v5.0
- macOS : 10.14.X, 10.15.X


## BIOS Setup

- Load Optimized Defaults
- iGPU Multi-Monitor : Enabled

## DSDT Patch

- [sys] Add IMEI
- [sys] Fix _WAK Arg0 v2
- [sys] Fix Mutex with non-zero SyncLevel
- [sys] Fix PNOT/PPNT
- [sys] HPET Fix
- [sys] IRQ Fix
- [sys] OS Check Fix (Windows 10)
- [sys] RTC Fix
- [sys] Shutdown Fix v2
- [sys] SMBUS Fix
- Rename ```HECI``` to ```IMEI```

***Need these MaciASL patch sources  
_RehabMan Laptop [http://raw.github.com/RehabMan/Laptop-DSDT-Patch/master]***  
***Modify DSDT on your system to prevent kernel panic***


## SSDT

- SSDT-EC-USBX.aml [USB Power Control]
- SSDT-PLUG.aml [PluginType=1]
- SSDT-PMC.aml [NVRAM]
- SSDT-UPRW.aml [Prevent wake from USB, Fix some USB issues]
- SSDT-XOSI.aml [OS Check Fix]


## CLOVER ACPI Hotpatch

- change GFX0 to IGPU [IGPU Fix]
- change HDAS to HDEF [Audio Fix]
- change HECI to IMEI
- change MEI to IMEI
- change ECDV to EC [USB Fix]
- change OSID to XSID [OS Check Fix]
- change \_OSI to XOSI [OS Check Fix]
- change UPRW to XPRW [Prevent wake from USB]
- change GPRW to YPRW [Prevent wake from USB]
- Fix RTC [Prevent RTC Bug]

***If you want to wake up the sleep with USB input devices, disable 'change GPRW to YPRW'***


## Drivers64UEFI

- ApfsDriverLoader.efi [acidanthera_AppleSupportPkg]
- OcQuirks.efi [ReddestDream_OcQuirks]
- OpenRuntime.efi [ReddestDream_OcQuirks]
- VBoxHfs.efi [acidanthera_AppleSupportPkg]
- VirtualSmc.efi [acidanthera_VirtualSMC]


## Kexts

- AGPMInjector.kext    -    Generated with AGPMInjector by Pavo-IM
- AirportBrcmFixup.kext    -    For edit Country Code to #a
- AppleALC.kext
- CPUFriend.kext
- CPUFriendDataProvider.kext    -    Generated with one-key-cpufriend by stevezhengshiqi
- EFICheckDisabler.kext
- IntelMausiEthernet.kext
- Lilu.kext
- SMCBatteryManager.kext
- SMCLightSensor.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- USBPorts.kext    -    Generated with Hackintool
- VirtualSMC.kext
- VoodooPS2Controller.kext    -    Power Button to Sleep/Power Menu Display
- WhateverGreen.kext

***AGPMInjector.kext, CPUFriend.kext, CPUFriendDataProvider.kext are not mandatory kext  
But creating it for your system will help you manage power***


## CLOVER Boot Arguments

- darkwake=10 [Prevent Sleep, Powernap Issue]
- dart=0 [Sidecar Activation]
- brcmfx-country=#a [Set Country Code for Universal]


## CLOVER Devices-Properties

- Set Audio Layout-ID, Enable Display Audio
```
			<key>PciRoot(0x0)/Pci(0x1f,0x3)</key>
			<dict>
				<key>device-id</key>
				<data>
				cKEAAA==
				</data>
				<key>layout-id</key>
				<data>
				AQAAAA==
				</data>
			</dict>
```
- Intel® UHD Graphics 630 [Headless with dGPU]
```
			<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
			<dict>
				<key>AAPL,GfxYTile</key>
				<data>
				AQAAAA==
				</data>
				<key>AAPL,ig-platform-id</key>
				<data>
				AwCSPg==
				</data>
				<key>device-id</key>
				<data>
				kj4AAA==
				</data>
				<key>framebuffer-con0-busid</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con0-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con0-flags</key>
				<data>
				IAAAAA==
				</data>
				<key>framebuffer-con0-index</key>
				<data>
				/////w==
				</data>
				<key>framebuffer-con0-pipe</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con0-type</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con1-busid</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con1-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con1-flags</key>
				<data>
				IAAAAA==
				</data>
				<key>framebuffer-con1-index</key>
				<data>
				/////w==
				</data>
				<key>framebuffer-con1-pipe</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con1-type</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con2-busid</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con2-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con2-flags</key>
				<data>
				IAAAAA==
				</data>
				<key>framebuffer-con2-index</key>
				<data>
				/////w==
				</data>
				<key>framebuffer-con2-pipe</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con2-type</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con3-busid</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con3-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con3-flags</key>
				<data>
				IAAAAA==
				</data>
				<key>framebuffer-con3-index</key>
				<data>
				/////w==
				</data>
				<key>framebuffer-con3-pipe</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con3-type</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-fbmem</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-patch-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-stolenmem</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-unifiedmem</key>
				<data>
				AAAAgA==
				</data>
			</dict>
```
- Intel® UHD Graphics 630 [iGPU without dGPU]
```
			<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
			<dict>
				<key>AAPL,GfxYTile</key>
				<data>
				AQAAAA==
				</data>
				<key>AAPL,ig-platform-id</key>
				<data>
				BwCbPg==
				</data>
				<key>device-id</key>
				<data>
				kj4AAA==
				</data>
				<key>framebuffer-con0-busid</key>
				<data>
				BQAAAA==
				</data>
				<key>framebuffer-con0-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con0-flags</key>
				<data>
				xwMAAA==
				</data>
				<key>framebuffer-con0-index</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con0-pipe</key>
				<data>
				EgAAAA==
				</data>
				<key>framebuffer-con0-type</key>
				<data>
				AAQAAA==
				</data>
				<key>framebuffer-con1-busid</key>
				<data>
				BgAAAA==
				</data>
				<key>framebuffer-con1-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con1-flags</key>
				<data>
				xwMAAA==
				</data>
				<key>framebuffer-con1-index</key>
				<data>
				AgAAAA==
				</data>
				<key>framebuffer-con1-pipe</key>
				<data>
				EgAAAA==
				</data>
				<key>framebuffer-con1-type</key>
				<data>
				AAgAAA==
				</data>
				<key>framebuffer-con2-busid</key>
				<data>
				BAAAAA==
				</data>
				<key>framebuffer-con2-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con2-flags</key>
				<data>
				xwMAAA==
				</data>
				<key>framebuffer-con2-index</key>
				<data>
				AwAAAA==
				</data>
				<key>framebuffer-con2-pipe</key>
				<data>
				EgAAAA==
				</data>
				<key>framebuffer-con2-type</key>
				<data>
				AAgAAA==
				</data>
				<key>framebuffer-con3-busid</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con3-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con3-flags</key>
				<data>
				IAAAAA==
				</data>
				<key>framebuffer-con3-index</key>
				<data>
				/////w==
				</data>
				<key>framebuffer-con3-pipe</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-con3-type</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-fbmem</key>
				<data>
				AAAAAA==
				</data>
				<key>framebuffer-patch-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-stolenmem</key>
				<data>
				AACQAw==
				</data>
				<key>framebuffer-unifiedmem</key>
				<data>
				AAAAgA==
				</data>
			</dict>
```


## ETC

***After Installation***
- Remove these Boot Arguments  
    -v  
    debug=0x100  
    keepsyms=1
- Additional patches are required for iMessage and Facetime activation (Board Serial Number, Serial Number, SmUUID)
- Depending on the case and built-in wireless card installed, additional patches of the internal USB port might be required
- Add a HiDPI patch based on your display resolution

***Intel® Core™ i7-8700 Processor***
- CPUFriendDataProvider.kext has been modified to manage the operation of the 'Intel® Core™ i7-8700 Processor'  
  If your CPU is not 'Intel® Core™ i7-8700 Processor', remove or regenerate the CPUFriendDataProvider.kext

***Intel® UHD Graphics 630***  
- If your iGPU is 'Intel® UHD Graphics 630' and there is no AMD dGPU, use 'config_igpu.plist'  
  DP and HDMI ports work normally, and DVI and VGA ports have black screen after booting
- 'AGPMInjector.kext' must be recreated for each type of AMD dGPU being used.

***Works in headless mode***
- The output ports of all iGPU are the dummy port

***Audio***
 - Built-in Output = Green [Front Left, Front Right] (Share with Front Panel Audio)
 - Built-in Line Output 1 = Orange [Front Center, LFE]
 - Built-in Line Output 2 = Black [Rear Left, Rear Right]
 - Built-in Digital Output = Optical S/PDIF
 - Built-in Input = Pink (Share with Front Panel Audio)
 - Built-in Line Input = Blue


## Issues

- Internal USB 2.0 Header(HS10), Aura LED Controller Header(HS11) are disabled to keep macOS USB port limited


## Screenshots

![strix](https://user-images.githubusercontent.com/46496967/77813822-00bb7000-70ef-11ea-8ee4-9a66eca69fdb.jpg)
