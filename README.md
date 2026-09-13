# ALL CREDIT GOES TO PORTALRUNNER OR p2r3 I DO NOT OWN THIS SOFTWARE I JUST MADE EDITS AND MADE IT RUN ON KINDLES SPECIFICALLY E-READERS NOT KINDLE FIRES
# Kindle Server Installation and Compatibility Guide

Use this guide to identify your specific Amazon Kindle model, choose the correct server file version based on its firmware, and view the setup steps.

---

## Device and Firmware Compatibility Matrix

Your target Kindle requires either the **Hard Float (HF)** or **Soft Float (SOFT)** version of the server depending on both its hardware generation and its current software firmware version. 

Amazon officially changed the system compiling environment from a soft-float architecture to a hard-float architecture starting exactly at firmware version **5.16.3**. 

| Kindle Generation / Models | Firmware Version Range | Float ABI Mode | Recommended File Download |
| :--- | :--- | :--- | :--- |
| **Touch, PW1, PW2, PW3** | All supported firmwares | Soft Float Only | `bareiron_legacy_soft` |
| **PW4, PW5, Oasis 2, 3** | Firmware **5.16.2.1.1 and older** | Soft Float | `bareiron_midrange_soft` |
| **PW4, PW5, Oasis 2, 3** | Firmware **5.16.3 and newer** | Hard Float | `bareiron_midrange` |
| **11th Gen and Newer** | Firmware **5.16.2.1.1 and older** | Soft Float | `bareiron_modern_soft` |
| **11th Gen and Newer** | Firmware **5.16.3 and newer** | Hard Float | `bareiron_modern` |

---

## Part 1: How to Transfer the Server File to Your Kindle

1. Connect your jailbroken Kindle to your computer using a USB cable.
2. Open the Kindle drive on your computer when it appears in your file explorer.
3. Drag and drop your chosen downloaded server file (such as `bareiron_modern`) straight into the main root storage directory of your Kindle.
4. Safely eject the Kindle from your computer and unplug the USB cable.

---

## Part 2: How to Launch the Server Using KTerm

Open the **KTerm** terminal app directly on your jailbroken Kindle screen and run the following commands sequentially.

1. Turn off the Kindle reading user interface so it stops draining system RAM and CPU resources in the background:
   ```bash
   stop lab126_gui
   ```

2. Navigate into the main storage folder where you copied the file:
   ```bash
   cd /mnt/us/
   ```

3. Give the operating system permission to execute your downloaded server file:
   ```bash
   chmod +x bareiron_target_filename
   ```
   *(Note: Replace `bareiron_target_filename` with the exact name of the file you downloaded, like `bareiron_modern`).*

4. Run the binary to spin up your Minecraft server:
   ```bash
   ./bareiron_target_filename
   ```

---

## Part 3: How to Safely Stop the Server

Because virtual touch keyboards on e-ink devices can make typing complex key combinations like `Control + C` unreliable, use this method to close your active server session safely:

1. Open a secondary tab or a new execution window inside your running **KTerm** application.
2. Force-kill the process and restore your normal reading screen by typing these two commands:
   ```bash
   killall bareiron_target_filename
   start lab126_gui
   ```
