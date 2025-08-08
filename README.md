# OC-asus_z97_Pro_Gaming-rx570-hackintosh
Opencore Bootloader For Asus Z97-Pro Gaming With Radeon rx570 GPU to boot and use MacOS 

## Screenshots
![Screenshot 2024-12-22 at 1 17 32 PM](https://github.com/user-attachments/assets/4aeea4e8-9533-4b1c-b5b9-f9bbec8c5a1e)


## Hardware Specs
| Components      | Name                                    |  Brand Links                                                                                                                                               |
| --------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Motherboard** | `Asus H97-Gaming`                         | [`PcCaseGear`](https://www.pccasegear.com/products/28542/asus-h97-pro-gamer-motherboard)                                                                                |
| **Power Supply** |`Corsair cv450 Bronze`   | [`Cosair`](https://www.corsair.com/us/en/p/psu/cp-9020209-na/cv-series-cv450-450-watt-80-plus-bronze-certified-psu-cp-9020209-na)                                                                                  |
| **CPU**         | `Intel® Core® i7 4790`                  | [`Intel Haswell`](https://www.intel.com/content/www/us/en/products/sku/80806/intel-core-i74790-processor-8m-cache-up-to-4-00-ghz/specifications.html)      |
| **iGPU**        | `Intel® HD Graphics 4600`               | [`Intel Haswell`](https://ark.intel.com/content/www/us/en/ark/search.html?_charset_=UTF-8&q=HD+Graphics+4600)                                              |
| **dGPU**        | `AMD Radeon RX 570 8GB`                 | [`Sapphire Pulse`](https://www.sapphiretech.com/en/consumer/pulse-rx-570-8g-g5)                                                                        |
| **Ram**         | `DDR3 32GB / 1600Mhz`                   |                                                                                          |
| **Ethernet**    | `Intel Gigabit Ethernet Connection 1218V2`             | [`Intel`](https://www.intel.com/content/www/us/en/products/sku/71305/intel-ethernet-connection-i218v/specifications.html)                                                                                               |
| **Audio**       | `Realek Codec ALC1150`                          | [`Realtek`](https://www.chipset-ic.com/datasheet/ALC1150.pdf)                                                                                                |

## Bios Settings

|       Disable                                                          |    Enable                                                                           |
|----------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Fast Boot                                                              | VT-x                                                                                |
| Secure Boot                                                            | Above 4G Decoding                                                                   |
| Serial/COM Port                                                        | Hyper-Threading                                                                     |
| Parallel Port                                                          | Execute Disable Bit                                                                 |
| VT-d (can be enabled if you set DisableIoMapper to YES)                | EHCI/XHCI Hand-off                                                                  |
| Compatibility Support Module (CSM)                                     | OS type: "Other OS"                                                                 |
| Intel SGX                                                              | UEFI Mode                                                                           |
| Intel Platform Trust                                                   | DVMT Pre-Allocated(iGPU Memory): 64MB or higher                                     |
| CFG Lock (MSR 0xE2 write protection)                                   | SATA Mode: AHCI                                                                     |


## MacOS Operating System that works
✅ My computer has been fully tested on the following operating systems:

| Name           | Version | Build      | Image links                                                                                                                                                                                                                                                           |
| -------------- | ------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `macOS Sonoma` |`14.6.1` | `23G93`    | [`DMG`](https://drive.google.com/file/d/1kTcAHoKdAfEp-l8bTtwps7EyKTbYqr4V/view?usp=sharing) / [`rdr`](https://rutracker.org/forum/viewtopic.php?t=6372743)                                                                                                            |
| `macOS Ventura`| `13.6.7`| `22G720`   | [`DMG`](https://drive.google.com/file/d/1YBoZio8yaiURgJNl7SIXly0l2dvI8Fvt/view?usp=sharing) / [`rdr`](https://rutracker.org/forum/viewtopic.php?t=6223477)                                                                                                            | 
|`macOS Monterey`| `12.7.5`| `21H1222`  | [`DMG`](https://drive.google.com/file/d/1fnlLVPrWgrMpAeC_3GjGk5vIV5-3tO4b/view?usp=sharing) / [`rdr`](https://rutracker.org/forum/viewtopic.php?t=6066530)                                                                                                            |
| `macOS Big Sur`|`11.7.10`| `20G1427`  | [`DMG`](https://drive.google.com/file/d/1urRARlkOi6NVc5b6CM0RFLvDLhsCcU5D/view?usp=sharing) / [`rdr`](https://rutracker.org/forum/viewtopic.php?t=5928524)                                                                                                            |

## Configuring your Config.plist

<details>
<summary><strong>Adding SMBIOS</strong></summary>
</br>

You will need to generate your own SMBIOS and configure, since is required to work fully with macOS. As per you can use the following SMBIOS:

|  SMBIOS    |  Hardware                                     |  macOS Big Sur              |  macOS Monterey            |  macOS Ventura   |  macOS Sonoma  |
| ---------- | --------------------------------------------- | --------------------------- | -------------------------- | ---------------- | -------------- |
| Macmini7,1 | Haswell with only iGPU                        |  full supported             |  full supported            | not supported    | not supported  |
| iMac14,4   | Haswell with only iGPU                        |  full supported             |  not supported             | not supported    | not supported  |
| iMac15,1   | Haswell with dGPU (Enabled iGPU Acceleration) |  full supported             |  not supported             | not supported    | not supported  |
| iMac16,2   | Haswell with only iGPU                        | supported (not recommended) |supported (not recommended) | not supported    | not supported  |
| iMac17,1   | Haswell with dGPU (Enabled iGPU Acceleration) | supported (not recommended) |  full supported            | not supported    | not supported  |
| iMacPro1,1 | Haswell only dGPU (Disabled iGPU Acceleration)|  full supported             |  full supported            | full supported   | full supported |
| MacPro7,1  | Haswell only dGPU (Disabled iGPU Acceleration)|  full supported             |  full supported            | full supported   | full supported |

⚠️ It's fully **required** to generate your own serials with [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and put it in your config.plist.

- Config.plist -> PlatformInfo -> Generic

![SMBIOS on config.plist screenchot](https://dortania.github.io/OpenCore-Install-Guide/assets/img/smbios.65baf9a9.png "SMBIOS on config.plist screenchot")
</details>


<details>  
<summary><strong>Enable Apple Services</strong></summary>
</br>

1. Run the following script in Terminal

```bash
git clone https://github.com/corpnewt/GenSMBIOS && cd GenSMBIOS && chmod +x GenSMBIOS.command && ./GenSMBIOS.command
```

2. Type `3` to Generate SMBIOS, then press ENTER
3. Type `MacPro7,1 5`, then press ENTER. Leave this Terminal window open.
4. Open `/EFI/OC/Config.plist` with any editor and navigate to `PlatformInfo -> Generic`
5. Add the script's last result to `MLB, SystemSerialNumber and SystemUUID`

```diff
<key>PlatformInfo</key>
<dict>
   <key>Generic</key>
   <array>
      </dict>
         <key>AdviseWindows</key>
         <false/>
         <key>SystemMemoryStatus</key>
         <string>Auto</string>
         <key>MLB</key>
+        <string>M0000000000000001</string>
         <key>ProcessorType</key>
         <integer>0</integer>
         <key>ROM</key>
         <data>ESIzRFVm</data>
         <key>SpoofVendor</key>
         <true/>
         <key>SystemProductName</key>
         <string>MacBookPro16,3</string>
         <key>SystemSerialNumber</key>
+        <string>W00000000001</string>
         <key>SystemUUID</key>
+        <string>00000000-0000-0000-0000-000000000000</string>
      </dict>
   </array>
</dict>
```

6. Save and reboot the system

</details>

<details>
<summary><strong>Setting a NVRAM variable</strong></summary>
</br>


| Boot Arguments             |    Сomments                                                                                                                       |
|--------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `-v`                       | This enables verbose mode, which shows all the behind-the-scenes text that scrolls by as you're booting instead of the Apple logo and progress bar. |
| `revpatch=sbvmm`           | Enable macOS Ventura and macOS Sonoma system updates                                                                              |
| `-no_compat_check`         | Сancel scan system board id                                                                                                       |
| `-wegnoegpu`               | Disable all external GPUs                                                                                                         |
| `-wegnoigpu`               | Disable internal GPU                                                                                                              |
| `nv_disable=1`             | Forces GPU into VESA mode(no GPU acceleration), useful for troubleshooting and when having issues installing Nvidia's WebDrivers. |
| `-igfxvesa`                | Forces GPU into VESA mode(no GPU acceleration), useful for troubleshooting                                                        |
| `igfxonln=1`               | Forces all displays online, useful for resolving screen wake issues in 10.15.4+ on Coffee and Comet Lake                          |
| `igfxfw=2`                 | Enables loading Apple's GUC firmware for iGPUs, requires a 9th Gen chipset or newer(ie Z390)                                      |
| `-igfxdvmt`                | Fix the kernel panic caused by an incorrectly calculated amount of DVMT pre-allocated memory on Intel ICL platforms               |
| `enable-dvmt-calc-fix`     | Property on IGPU                                                                                                                  |
| `-igfxblt`                 | An alternative to the Backlight Registers Fix and make Backlight Smoother work on KBL/CFL platforms running macOS 13.4 or later.  |
| `enable-backlight-registers-alternative-fix`| Property on IGPU                                                                                                 |
</details>


## What Working?

- [x] `AMD Radeon Rx570 Graphics` acceleration.
- [x] dGPU & CPU Power Management.
- [x] `HDMI Sound` Working
- [x] `On-Board Sound` Working
- [x] Apple Services `iCloud, App Store, iMessage, FaceTime` Working
- [x] Restart, Sleep and Shutdown Working
- [x] USB 2.0 & USB 3.0 Working
- [x] LCD Brightness Control Working `Requires 3rd Party to working`
- [x] macOS Update `Can enable/disable through boot arguments`

## What is not Working?
- [ ] onboard vga not working
- [ ] airdrop not work
- [ ] In the macOS Sonoma, onboard audio is not working, Even updating the Applealc.kext does not work well!
