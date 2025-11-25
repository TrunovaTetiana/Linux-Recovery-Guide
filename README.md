# Linux-Recovery-Guide
Real-world Linux troubleshooting and system recovery cases
```
 _      _____ _   _ _   _ __   __
| |    |_   _| \ | | | | |\ \ / /
| |      | | |  \| | | | | \ V / 
| |      | | | . ` | | | | > <  
| |____ _| |_| |\  | |_| | / . \ 
|______|_____|_| \_|\___/ /_/ \_\

       Linux System Recovery Guide

```
      

 <img src="https://img.shields.io/badge/Linux-Diagnostics-yellow?style=for-the-badge&logo=linux">
  <img src="https://img.shields.io/badge/Kali-Blue?style=for-the-badge&logo=kalilinux">
  <img src="https://img.shields.io/badge/Kernel-Debugging-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/X11%20Errors-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Troubleshooting-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/No_Reinstall_Required-success?style=for-the-badge">
</p>
📑 Table of Contents
	•	📌 Overview￼
	•	📁 Repository Structure￼
	•	🕵️ Case Index￼
	•	🧠 Case Categories￼
	•	🛠️ Tools Used￼
	•	🚀 Goals￼
	•	👩‍💻 About Me￼
	•	🔗 Connect￼
	•	📌 Notes￼

⸻

📌 Overview

This repository documents real-world Linux failures that I diagnosed and repaired manually —
from broken kernels, missing modules, and X11 crashes to DNS, TLS, and system time issues.

Each report reflects how deep debugging happens in real life when the desktop is gone,
the GUI won’t load, and only TTY is available.

This repo shows how a cybersecurity engineer handles full-scale OS failures.

⸻

📁 Repository Structure
Linux-Recovery-Guide/
│
├── kali-nvidia-recovery.md       # Case 01: GUI fails after NVIDIA/X11 mismatch
│
├── assets/                       # Screenshots, logs, diagrams
│     ├── xorg-errors/
│     ├── kernel-modules/
│     └── nvidia-conflicts/
│
└── README.md                     # You are here
Each case includes:

✔ Problem description
✔ Log analysis
✔ Kernel + initramfs diagnostics
✔ Graphics/X11 repair steps
✔ DNS/TLS fixes
✔ Final reboot validation
✔ “Lessons learned”
🕵️ Case Index
Case #
Title
Category
Status
Report
01
Kali Linux GUI broke after upgrade (NVIDIA mismatch, X11 “no screens found”)
X11 / Kernel / GPU
✅ Completed
View Report￼
More cases will be added as I document new real debugging sessions.
🧠 Case Categories

🎨 Graphics (X11 / Wayland / GPU)
	•	“(EE) no screens found”
	•	Xorg crashes
	•	NVIDIA / Intel hybrid conflicts
	•	modeset / DRM errors

🐧 Kernel & Boot
	•	initramfs rebuild failures
	•	missing modules
	•	wrong kernel loaded
	•	boot loops

🌐 Networking
	•	DNS misconfiguration
	•	resolv.conf issues
	•	NTP/time drift
	•	TLS errors (curl: (60) SSL certificate problem…)

⚡ System Services
	•	broken display managers
	•	failing systemd units
	•	login failures

⸻

🛠️ Tools Used
journalctl       dmesg          lsmod          systemctl  
xrandr           update-initramfs     modinfo  
ping             timedatectl    nslookup       nano /etc/*
Xorg.0.log       dpkg            uname -r
These tools form the backbone of Linux recovery work.
🚀 Goals
	•	Build a library of real troubleshooting cases
	•	Show full technical depth in system diagnostics
	•	Provide reference material for others facing similar issues
	•	Demonstrate engineering-level problem solving
	•	Strengthen my cybersecurity & Linux administration portfolio

⸻

👩‍💻 About Me

I’m a cybersecurity specialist focusing on:
	•	Linux debugging & system internals
	•	Web security (XSS, SQLi, IDOR, logic flaws)
	•	Pentesting with Burp Suite, Nmap, Hydra, Wireshark, Metasploit
	•	Real-world incident analysis
	•	Creating clean, structured technical documentation

My goal is to become a strong penetration tester with deep system knowledge.

⸻

🔗 Connect
	•	GitHub: https://github.com/TrunovaTetiana
	•	Twitter/X: https://twitter.com/TrunovaTet73725
	•	TryHackMe: https://tryhackme.com/p/TetianaTrunova

⸻

📌 Notes

This repository contains real recovery reports, not universal guides.
Linux systems differ by:
	•	hardware
	•	kernel versions
	•	drivers
	•	display managers
	•	installed tools

These cases show how I solved each issue in my environment,
so others can learn, compare, and adapt the methodology.
