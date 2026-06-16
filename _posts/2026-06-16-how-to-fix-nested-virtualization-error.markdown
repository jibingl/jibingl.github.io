---
layout: post
title:  "Troubleshoot Nested Virtualization"
date:   2026-06-16 17:00:00 -0500
categories: felix
---

# How to Fix Nested Virtualization Error?

If you get below error, you are in the right place to fix it.

<img width="222" height="222" alt="nsa_instructor_profile" src="/assets/images/error-continue_without_virtualized_intel_vt-x_rpt.jpg" />

### Step 1: Disable Hyper-V Features
1. Open the Start menu, type **Turn Windows features on or off**, and press **Enter**.
2. Uncheck the following boxes if they are enabled:
   * Hyper-V
   * Virtual Machine Platform
   * Windows Hypervisor Platform
3. Click **OK** and restart your computer.

### Step 2: Run the Complete Hypervisor Wipe Command
Even if features are unchecked in Windows Features, Windows 11 Pro can keep a silent hypervisor state running.

1. Right-click the **Start Button** and select **Terminal (Admin)** or **Command Prompt (Admin)**.
2. Type the following command to completely disable the Microsoft hypervisor at boot:
   ```cmd
   bcdedit /set hypervisorlaunchtype off
   ```
3. Press **Enter**. You should see "The operation completed successfully."

### Step 3: Perform a Full Cold Reboot
A normal "Restart" in Windows 11 often uses "Fast Startup," which hibernates the kernel and preserves the hypervisor state.

1. Close all open applications.
2. Open your Command Prompt/Terminal again and run:
   ```cmd
   shutdown /s /t 0
   ```
3. This forces a complete shutdown. Wait for the computer to power off fully, then turn it back on.
