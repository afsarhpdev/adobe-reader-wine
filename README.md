# Installing Adobe Reader (Latest Version) on Arch Linux with wine: A Comprehensive Guide
## How to Install Adobe Reader on Arch Linux Using Wine

If you're an Arch Linux user and need to run Adobe Reader to view PDFs, you can do so using Wine, a compatibility layer capable of running Windows applications on Linux. Follow these steps to install Wine and Adobe Reader on your Arch Linux system.

### Prerequisites
* A computer running Arch Linux (or any Arch-based distribution like Manjaro)
* Administrative (sudo) access to install software
* Familiarity with basic terminal commands
* Before installing Wine and Adobe Reader, ensure you have Microsoft fonts installed.
  You can obtain Windows 7 ( https://www.w7df.com/7/download.html ) and 10 fonts ( https://www.w7df.com/p/windows-10.html ) or any other reliable source.
  Copy the downloaded fonts to a folder in
  ```
  /usr/share/fonts
  ```
  and execute the following command in a terminal

  ```bash
  sudo fc-cache -vf
  ```

## Installation Steps

### Step 1: Update Your System:
First, make sure your system is up-to-date. Open a terminal and run the following command:
```bash
sudo pacman -Syu
```  

### Step 2: Install Wine:
Open a terminal and run the following command to install Wine along with necessary dependencies:

### Step 3: Install Additional Wine Dependencies:
Install complete Wine dependencies using the following command
```bash
sudo pacman -Syu lib32-libcups dosbox lib32-gst-plugins-base lib32-gst-plugins-base-libs lib32-gst-plugins-good libgphoto2 lib32-libxcomposite lib32-libxinerama lib32-opencl-icd-loader lib32-pcsclite sane lib32-sdl2 unixodbc
```
### Step 4:  Install Wine GUI: 
Execute the following command to install Wine GUI and dependencies:
```bash
yay -Syu winegui vkd3d lib32-vkd3d zenity kdialog
```

### Step 5:  Open Wine GUI and Create Windows 10 32-Bit Wine Prefix:
1. Open Wine GUI
```bash
winegui
```
2. Create a New Wine Prefix:
  * Specify a name for your prefix (e.g., adobereader).
  * Select Windows 10 32-bit as the Windows version.

### Step 6:  Install Required Wine Prefix Dependencies for Adobe Reader: Run the following command in the terminal to install necessary Wine prefix dependencies for Adobe Reader:
The location is relative. Use as per your environment. The Guide shows default locations of user and wine prefix
The command finds the wine prefix and install required dependencies for Adobe Reader Latest Version.
```bash
export WINEPREFIX=/home/YOURUSERNAME/.local/share/winegui/prefixes/YOURPREFIXNAME/ && winetricks allfonts corefonts mspatcha riched20 riched30 atmlib wsh57 msftedit vcrun2005 vcrun2008 vcrun2010 vcrun2012 vcrun2013 vcrun2022
```

### Step 7:  Update Config in Wine GUI:
Once installed, click on "Update Config" button in Wine GUI Top Menu Bar.

### Step 8:  Download Adobe Reader: 
  Download Adobe Reader from the official website.
  Visit the Adobe Reader download page and download the Windows version of the installer (.exe file).
  
### Step 9:  Install Adobe Reader:
In Wine GUI,
  * Click "Run Program" and select the downloaded Adobe Reader installation file.
  * Follow the prompts to complete the installation.
    
### Step 10:  Post-installation Steps: Rename FullTrustNotifier.exe:
In Wine GUI,
  * Navigate to C:\Program Files\Adobe\Acrobat Reader DC\Reader
  * Rename FullTrustNotifier.exe to FullTrustNotifier.exe.old.
Note: combase.dll is not yet implemented by Wine, so renaming this file can prevent periodic crashes and error pop-ups.

### Step 11:  Modify Adobe Reader Settings:
* Open Adobe Reader.
* Press Alt+F, select "Disable New Acrobat Reader," and restart Adobe Reader.
* Go to File > Edit > Preferences.
* Under Security Enhanced, disable protected view.
* Optionally, disable any other settings under preferences that you do not use for PDFs like JavaScript.

### Step 12:  Avoid Opening Welcome PDF:
Do not attempt to open the welcome PDF file; instead, open any other PDF file stored on your system.
You can checkbox the default welcome PDF file and remove from recents to prevent yourself from accidentally clicking on it.

By following these steps, you can successfully install Adobe Reader on Arch Linux using Wine, allowing you to view PDF files seamlessly.

Wine Is Not An Emulator
I Use Arch BTW
