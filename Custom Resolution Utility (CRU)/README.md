# Custom Resolution Utility (CRU) Guide for Everyday Users

Welcome to the simple guide for using the Custom Resolution Utility (CRU)! This tool lets you change how your monitor shows resolutions without any complicated technical steps. Follow this guide to safely add, remove, or modify display resolutions on your Windows computer.

---

## What Is CRU?

CRU is a program that helps you:
- **Add custom resolutions:** Set up new screen resolutions.
- **Remove unwanted resolutions:** Clean up the list of available resolutions.
- **Adjust settings:** Tweak refresh rates and other display options.

**Note:** CRU makes changes in Windows’ registry (a special system database) but does not change your monitor’s hardware.

---

## Requirements

- **Operating System:** Windows Vista or later (Windows XP is not supported)
- **Graphics Card:** Any AMD, NVIDIA, or Intel GPU with the proper drivers installed.
- **Backup:** It’s a good idea to create a system restore point or backup your system before making changes.

---

## Getting Started

1. **Download CRU:**  
   Get the latest version of CRU from the [official download page](#).

2. **Extract the Files:**  
   Unzip the downloaded package into a folder you can easily access.

3. **Run CRU:**  
   Double-click on `CRU.exe`. You might see a prompt asking for permission—click **Yes**.

---

## How to Use CRU

### 1. Choose Your Display

- **Select the Monitor:**  
  At the top of the CRU window, use the drop-down menu to choose the display you want to modify.  
  - Displays marked as **(active)** are currently connected.
  - An asterisk (`*`) means an override has already been applied.

### 2. Edit Resolutions

- **To Add or Change a Resolution:**  
  Click on the resolution you want to modify and adjust the settings.
  
- **To Remove a Resolution:**  
  Select the resolution and click the **Delete** button.

- **Copy & Paste Settings:**  
  Use the **Copy** and **Paste** buttons if you want to duplicate settings from one resolution to another.

### 3. Save and Apply Your Changes

- **Save Changes:**  
  Click **OK** in CRU to save your new settings to the registry.
  
- **Restart the Graphics Driver:**  
  Run `restart.exe` (or `restart64.exe` if you have a 64-bit system).  
  - **Tip:** If nothing happens within 15 seconds, press **F8** to load recovery mode (this unloads the changes temporarily).

### 4. Set Your New Resolution in Windows

1. **Right-Click on the Desktop:**  
   Choose **Display settings** (or **Screen resolution** on older versions of Windows).

2. **Advanced Settings:**  
   Click **Advanced display settings** and then **Display adapter properties**.

3. **Select the Monitor Tab:**  
   Choose your new resolution and refresh rate from the list.

---

## Troubleshooting Tips

- **Screen Not Coming Back:**  
  If your screen doesn’t appear after restarting the driver, wait 15 seconds. If it still doesn’t work, press **F8** to enter recovery mode.

- **Driver Crashes:**  
  If your graphics driver crashes, simply run `restart.exe` again.

- **Reset to Default Settings:**  
  To go back to your original settings, open CRU, click the **Delete** button for the override, then run `reset-all.exe` and restart your computer.

---

## Special Notes

- **For Older Intel GPU Users:**  
  If you have an older Intel graphics card, click the **Export...** button in CRU and choose **EXE file**. Run the created installer to apply the changes.

- **For NVIDIA Users:**  
  Some NVIDIA drivers may ignore changes when Display Stream Compression (DSC) is active. If you have issues, check your NVIDIA settings or look for driver updates.

---

## Final Thoughts

Changing your display resolution with CRU can make your computer work exactly the way you want it to, whether you’re gaming, watching videos, or just browsing. Just remember:
- **Backup First:** Always create a restore point before making changes.
- **Follow the Steps:** Take your time and follow the guide step-by-step.
- **Ask for Help:** If you get stuck, check out online forums or ask a friend.

Happy customizing!

---

## Additional Resources

- [Official CRU Download](#)
- [Community Forums & Help](#)
