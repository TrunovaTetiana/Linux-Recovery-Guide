# 🛠️ Case 01 — Kali Linux GUI Broke After Upgrade (NVIDIA / X11 “no screens found”)
A real-world Linux recovery case where the graphical interface stopped working after a routine system upgrade. The goal: repair the system without reinstalling Kali Linux.

---

## 📌 Summary
After upgrading my system, Kali Linux stopped loading the GUI. Instead of the login screen, I saw a black screen and could only switch to a TTY.

This report documents how I:
- diagnosed the issue,
- found the cause (NVIDIA / X11 mismatch),
- restored the system manually,
- and brought the OS back to life without reinstalling.

---

## 🐛 Problem Description
Immediately after running:

sudo apt update
sudo apt upgrade

the next reboot resulted in:
- no graphical login screen
- no X11 session
- black screen only

I switched to TTY:

Ctrl + Alt + F2

---

## 🧪 Diagnostics & Logs

### 1. Attempt to start X manually
startx

Result:
(EE) no screens found (EE)

---

### 2. Checking Xorg logs
cat /var/log/Xorg.0.log

Findings:
- no available screens
- wrong GPU modules loaded
- mismatched kernel modules
- broken config referencing old drivers

This indicated a GPU / kernel / X11 mismatch.

---

### 3. Check hardware & modules
lspci | grep -E "VGA|3D"
lsmod | grep nvidia
lsmod | grep i915

Findings:
- NVIDIA modules were still present
- Intel i915 existed but wasn’t used
- X11 attempted to load NVIDIA

---

## 🔍 Root Cause
A mismatch between:
- new kernel version
- leftover NVIDIA modules
- outdated X11 configuration

This caused X11 to detect no valid display → (EE) no screens found.

---

## 🧰 Commands Executed (Full Repair Sequence)

### Remove NVIDIA
sudo apt purge nvidia* -y
sudo apt autoremove --purge -y

### Clean leftover modules
sudo rm -rf /usr/lib/nvidia/*
sudo rm -rf /lib/modules/*/nvidia/*

### Rebuild initramfs
sudo update-initramfs -u -k all

### Reinstall Intel drivers
sudo apt install --reinstall xserver-xorg-video-intel

### Reset X11 configuration
sudo rm -f /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg

### Reboot
sudo reboot

---

## ✅ Final Result
- GUI restored successfully  
- System stable on Intel iGPU only  
- No reinstall required  
- X11 loads normally  
- No NVIDIA conflicts remain

---

## 🗂️ Case Metadata

Date: 24.11.2025  
Issue: X11 “no screens found” after upgrade  
Category: X11 / Kernel / GPU  
Status: Completed  
Reinstall: No  

---

## 🧠 Lessons Learned
- Kernel upgrades often break NVIDIA setups.
- Hybrid GPU systems are fragile under Kali.
- Intel-only mode is the most stable for penetration-testing.
- Xorg.0.log always reveals the real problem.
- initramfs rebuild is essential after GPU driver removal.

---

## 📝 Notes
This case reflects real troubleshooting. Linux systems differ by:
- hardware
- kernel builds
- drivers
- display managers
- initramfs variations

Therefore, this report is not a universal guide but a reference to how this specific issue was resolved.

---

## 🔗 Author
Tetiana Trunova  
Cybersecurity Specialist  
GitHub: https://github.com/TrunovaTetiana  
X/Twitter: https://twitter.com/TrunovaTet73725  
TryHackMe: https://tryhackme.com/p/TetianaTrunova
