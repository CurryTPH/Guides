# Custom Resolution Utility (CRU) Comprehensive Technical Guide

*Version: 1.5.2 (with subsequent updates noted in the Change Log)*  
*Last Updated: [Insert Date]*

---

## Table of Contents

1. [Introduction](#introduction)
2. [Objectives & Scope](#objectives--scope)
3. [Prerequisites](#prerequisites)
4. [Setup & Installation Instructions](#setup--installation-instructions)
5. [Step-by-Step Procedures](#step-by-step-procedures)
    - [Basic Usage](#basic-usage)
    - [Detailed Resolution Editing](#detailed-resolution-editing)
    - [Editing FreeSync/VRR Ranges](#editing-freesyncvrr-ranges)
    - [Using Extension Blocks](#using-extension-blocks)
    - [Alternative Method for Intel GPUs](#alternative-method-for-intel-gpus)
6. [Parameter & Value Justifications](#parameter--value-justifications)
7. [Testing & Validation Methods](#testing--validation-methods)
8. [Error Handling & Troubleshooting](#error-handling--troubleshooting)
9. [Source & Reference Transparency](#source--reference-transparency)
10. [Annotated Code & Command Samples](#annotated-code--command-samples)
11. [Versioning & Change Logs](#versioning--change-logs)
12. [Performance & Scalability Considerations](#performance--scalability-considerations)
13. [Security Considerations](#security-considerations)
14. [Visual Aids & Diagrams](#visual-aids--diagrams)
15. [Alternative Approaches & Comparative Analysis](#alternative-approaches--comparative-analysis)
16. [Extensibility & Customization Guidelines](#extensibility--customization-guidelines)
17. [Real-World Use Cases & Examples](#real-world-use-cases--examples)
18. [Data Sources & Handling](#data-sources--handling)
19. [Licensing, Credits, & Contributions](#licensing-credits--contributions)
20. [Interactive Components & Community Feedback](#interactive-components--community-feedback)
21. [Final Summary & Additional Resources](#final-summary--additional-resources)
22. [Appendices](#appendices)

---

## 1. Introduction

Custom Resolution Utility (CRU) is an advanced EDID editor designed to allow users to define custom display resolutions, remove unwanted resolution entries, and edit additional parameters such as FreeSync/VRR ranges. CRU creates software EDID overrides stored in the Windows registry—without modifying the hardware EDID. This guide explains every aspect of CRU, from installation and setup to in-depth configuration, and is geared toward advanced users.

---

## 2. Objectives & Scope

### Objectives

- **Define and Modify EDIDs:** Understand how CRU reads, edits, and writes EDID data to create custom resolutions.
- **Customization Capabilities:** Learn to add detailed resolutions, modify refresh rates, and manage FreeSync/VRR parameters.
- **Diagnostics & Troubleshooting:** Gain insights into error handling and testing to ensure a stable configuration.
- **Driver Interaction:** Explore CRU's interaction with AMD/ATI, NVIDIA, and Intel GPU drivers, including the impact of features such as Display Stream Compression (DSC).

### Scope

- **Supported Platforms:** Windows Vista and later (Windows XP is not supported).
- **Supported Hardware:** AMD/ATI, NVIDIA GPUs, and Intel GPUs (with specific driver version requirements).
- **Limitations:**  
  - NVIDIA drivers may ignore EDID overrides when DSC is active.  
  - Limited extension block support on Intel GPUs.

---

## 3. Prerequisites

### Hardware Requirements

- **Display:** A monitor that supports EDID overrides.
- **GPU:**  
  - AMD/ATI or NVIDIA GPU with appropriate drivers.  
  - Intel GPUs: Newer models require the latest drivers; older models (external displays only) use an alternative installation method.

### Software & Environment

- **Operating System:** Windows Vista or later.
- **Drivers:**  
  - **NVIDIA:** Ensure your driver supports EDID overrides; note issues with DSC.  
  - **AMD/ATI:** Latest drivers recommended; be aware of pixel clock limitations.  
  - **Intel:**  
    - Skylake (6th gen): Intel Graphics Driver [15.45] or newer.  
    - Haswell/Broadwell (4th/5th gen): Intel Graphics Driver [15.40].  
    - Haswell (Windows 7/8.1): Intel Graphics Driver [15.36].
- **User Account Control (UAC):** Administrative privileges are required for registry modifications.
- **Recovery Drive Preparedness:** Be familiar with booting Windows in safe mode to recover if display issues occur after EDID changes.

### Background Knowledge

- **EDID Structure:** Basic understanding of Extended Display Identification Data.
- **Display Standards:** Familiarity with VESA DMT, CTA-861, CVT, and CVT-RB.
- **Technical Terminology:** Pixel clock, refresh rates, and scaling concepts.

---

## 4. Setup & Installation Instructions

### 4.1 Downloading and Running CRU

1. **Obtain CRU:** Download the latest version of CRU from the official source or a trusted repository.
2. **Extract Files:** Unzip the downloaded package to a secure directory.
3. **Launch Application:**  
   - Run `CRU.exe`.  
   - Approve the UAC prompt to allow registry modifications.

### 4.2 Registry Considerations

- **EDID Overrides:** CRU writes EDID overrides to the Windows registry without modifying the physical hardware.
- **Backup Registry:** Back up your registry before making any changes.

### 4.3 Restarting the Graphics Driver

- **Using the Restart Utility:**  
  - Run `restart.exe` (or `restart64.exe` on 64-bit systems) after saving changes.
  - If the display does not return within 15 seconds, press **F8** to load recovery mode, temporarily unloading the overrides.

---

## 5. Step-by-Step Procedures

### Basic Usage

1. **Launch CRU.exe:**  
   - Select the desired display from the drop-down list.  
   - Displays marked as “(active)” are currently connected.  
   - An asterisk (“*”) indicates an existing override.
2. **Edit Resolutions:**  
   - Use the “Copy” and “Paste” buttons to duplicate or import resolution sets (resolutions, extension blocks, and range limits).
   - Click **OK** to commit your changes to the registry.
3. **Restart the Graphics Driver:**  
   - Execute `restart.exe` to apply the new settings.
4. **Apply the Resolution:**  
   - Navigate to Windows display settings to select the new resolution and refresh rate.  
     - **Windows 10:** Right-click the desktop → **Display settings** → **Advanced display settings** → **Display adapter properties** → **Monitor** tab.  
     - **Older Versions:** Right-click the desktop → **Screen resolution** → **Advanced settings** → **Monitor** tab.

### Detailed Resolution Editing

- **Detailed Resolutions:**  
  - The first detailed resolution is the native/preferred resolution.
  - Additional detailed resolutions can be added using extension blocks if the resolution exceeds the EDID limits (4095×4095 pixels, 655.35 MHz pixel clock).
- **Timing Options:**  
  CRU offers multiple timing methods:
  - **Manual:** Full control over timing parameters.
  - **Automatic PC/HDTV/CRT:** Auto-configures values based on industry standards (CTA-861, VESA DMT, CVT-RB).
  - **Exact Options:** “Exact”, “Exact reduced”, and “Exact CRT” for achieving integer refresh rates.
  - **Vertical Total Calculator:** Useful for implementing Quick Frame Transport (QFT).

### Editing FreeSync/VRR Ranges

- **DisplayPort:**  
  - Click the **Edit…** button to modify the “V rate” in the range limits.
  - Ensure the option **Include if slot available** is enabled.
- **HDMI FreeSync and HDMI 2.1 VRR:**  
  - Edit the respective data blocks (FreeSync range and HDMI 2.1 support) in the CTA-861 extension block.
  - **Note for NVIDIA:** Some ranges are hard-coded; a workaround is to change the device ID (e.g., to “ABC1234”).

### Using Extension Blocks

- **Purpose:**  
  Extension blocks enable the addition of extra detailed resolutions, TV resolutions, audio formats, and HDMI/DisplayPort support.
- **Types of Extension Blocks:**  
  - **CTA-861:** Contains detailed resolutions and data blocks.
  - **VTB-EXT:** Adds more standard resolutions (only one allowed on AMD/ATI and must be the last block).
  - **DisplayID:** Supports resolutions beyond standard EDID limits.
- **Importing Blocks:**  
  - Import pre-made extension block files (e.g., `hdmi.dat`, `hdmi-audio.dat`, `hdmi2.dat`) as a starting point.

### Alternative Method for Intel GPUs

- **Older Intel GPUs:**  
  - Use the **Export…** button and select **EXE file** to create a self-contained EDID override installer.
  - Run the resulting `.exe` and select **Install EDID** to apply the override on all matching displays.

---

## 6. Parameter & Value Justifications

- **Resolution Limits:**  
  EDID detailed resolutions are capped at 4095×4095 pixels and 655.35 MHz pixel clock due to protocol constraints. Use DisplayID for higher values.
- **Timing Parameters:**  
  Automatic timing modes (e.g., PC/HDTV/CRT) leverage industry standards (CTA-861, VESA DMT, CVT-RB) to balance compatibility and performance.
- **Pixel Clock Constraints:**  
  Single-link DVI is limited to 165 MHz; dual-link to 330 MHz; HDMI/DisplayPort limits vary by GPU. Patching tools (e.g., AMD/ATI or NVIDIA Pixel Clock Patcher) may be required for non-standard setups.
- **FreeSync/VRR Considerations:**  
  Adjusting the “V rate” or data block parameters ensures the display operates within the supported variable refresh range.

---

## 7. Testing & Validation Methods

### Unit and Integration Testing

- **Visual Confirmation:**  
  Verify the custom resolution appears in Windows display settings and is selectable.
- **Driver Restart Testing:**  
  After running `restart.exe`, confirm the driver reloads the new EDID override without crashing.
- **Timing and Refresh Rate Validation:**  
  Test various timing modes and refresh rates using built-in display diagnostics or third-party tools.

### Expected Outcomes

- **Resolution Listing:**  
  The selected display should list all detailed and standard resolutions, with the native resolution flagged.
- **Functionality:**  
  Switching resolutions should occur without screen artifacts or driver crashes.
- **Recovery Mode:**  
  If display issues occur, using recovery mode (F8 during restart) should unload overrides and restore defaults.

---

## 8. Error Handling & Troubleshooting

### Common Issues

- **Display Not Returning After Changes:**  
  Wait 15 seconds for the driver to reload. If the display does not appear, press **F8** to enter recovery mode.
- **Driver Crashes:**  
  If the driver crashes during restart, re-run `restart.exe` to re-enable the graphics driver.
- **Non-Recognized EDID Overrides:**  
  NVIDIA drivers may ignore EDID overrides when Display Stream Compression (DSC) is active. Report such issues to NVIDIA.

### Debugging Tips

- **Registry Verification:**  
  Check that registry entries under the EDID override keys are correctly written.
- **Log Files and Diagnostic Utilities:**  
  Use Windows Event Viewer or third-party tools to inspect errors during driver restart.
- **Safe Mode:**  
  Use Windows Safe Mode (via a recovery drive) to remove problematic overrides using the **Delete** button or `reset-all.exe`.

---

## 9. Source & Reference Transparency

- **Official CRU Documentation:** Refer to the README and change log included with CRU.
- **Third-Party Tools:**  
  - [AMD/ATI Pixel Clock Patcher](#)  
  - [NVIDIA Pixel Clock Patcher](#)
- **Standards & Protocols:**  
  - VESA DMT, CTA-861, CVT, CVT-RB specifications.
- **Community Resources:**  
  - [Overclock.net](https://www.overclock.net/)  
  - [Reddit’s r/overclocking](https://www.reddit.com/r/overclocking/)

---

## 10. Annotated Code & Command Samples

Although CRU is primarily a GUI-based tool, several command-line utilities are provided.

### Restarting the Graphics Driver

```batch
:: Restart the graphics driver quietly
restart.exe /q
