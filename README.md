# WinCE 4.2-Windows Mobile 5/6 Debug Guide for Windows 10
A guide on setting up debugging for emulated windows mobile devices
- **1. Install Microsoft Device Emulator**
  - Install the emulator via `vs_emulator_x64_vista.exe` (64 bit) or `vs_emulator.exe` (32 bit)
- **2. Install Windows Mobile Device Center**
  - Install the WMDC via `drvupdate-amd64.exe` (64 bit) or `drvupdate-x86.exe` (32 bit)
  - Install the WDMC Win 10 Fixes via [wmdc-fixes-for-win10.msi](https://junipersys.com/index.php/support/knowledge-base/support-knowledge-base-topics/desktop-connection-activesync-or-windows-mobile-device-center/wmdc-in-windows-10)
  - Open services (services.msc) and find `"Windows Mobile-2003-based device connectivity"` and `"Windows Mobile-based device connectivity"`, right click, properties, 'Log on' tab, and click the radio button "Local system account" for both services.
  - Restart Windows.
- **3. Optional - Get Emulation .bin files**
  - To get Pocket PC/Smartphone 2003 emulation files, install Visual Studio 9.0 (2008) from here via [en_visual_studio_2008_professional_x86_dvd_x14-26326.iso](https://archive.org/download/en_visual_studio_2008_professional_x86_dvd_x14-26326_202310)
  - To get Windows Mobile 5.0 files, install `efp.msi`
  - To get Windows Mobile 6.0, install files [here](https://www.microsoft.com/en-us/download/details.aspx?id=7974)
- **4. Debugging**
  - I use IDA Pro 7.0, any IDA version below 7.0 or below has ActiveSync debugging.
  - **Note for Pocket PC 2003**: I can only attach to processes in IDA versions 6.5-7.0, I cannot start them automatically. If you need to start them automatically, you'll have to use IDA 6.1 or below
  - Open Microsoft Device Emulator, and select your emulator, right click and select connect. Once booted, right click again and select cradle. (It should auto connect via DMA to ActiveSync)
  - Load your binary in IDA, and select "Remote WinCE debugger (ActiveSync)"
  - If not attach debugging, for the debugger settings, set "Application" to the exe's file path **on the emulator**, such as `\Program Files\Abc\xyz.exe`

- **Notes:** If your emulator still wont connect when cradled, try running 'rapi1.reg' and 'WcesComm.reg', and reboot windows. This may resolve it.
