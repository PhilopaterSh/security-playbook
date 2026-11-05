# Mobile Penetration Testing

# Mobile Penetration Testing & Android Security Architecture

What Does It Take to Build Secure Mobile Applications?

1. Understand how mobile applications work.
2. Get familiar with tools and guides.
3. Practice, Practice, and Practice.

## Mobile Attack Surface

- **Code vulnerabilities:** Errors or weaknesses in the app's code, such as insecure data storage, improper input validation, and insecure authentication mechanisms.
- **Data exposure:** Unauthorized access to sensitive user data, either stored within the app or transmitted over the network.
- Network communication: Vulnerabilities in the app's communication with servers, including insecure data transfer and exposure to man-in-the-middle attacks.
- **Third-party components:** Risks associated with using external libraries or SDKs, such as vulnerabilities in those components or improper integration.
- **Platform interactions:** Potential issues arising from the app's interactions with the device's operating system or other applications, such as excessive permissions or data leakage.
APK Attack Surface [web, network, software, interact with system]
APK Area of Analysis [Static Analysis, Dynamic Analysis, Network Analysis, Web Analysis]

# Android Architecture

**Linux Kernel:** The core, providing core functionalities like device drivers and memory management. It also enforces app sandboxing through mechanisms like user IDs.
**Android Runtime (ART):** Executes Android applications. It translates bytecode (machine code for the virtual machine) into machine code the device can understand.
**Android Framework:** Provides a set of tools and APIs for app development. It acts as a middle layer between the applications and the lower levels, offering services like Ul toolkit, resource management, and security features like permission management. 
**Applications:** The topmost layer where user-installed apps reside. These apps leverage the functionalities provided by the Android Framework to deliver their features.
!Attachments/Cybersecurity/Pentesting Methodology/Pasted image 20260720142114.png

# API Version and Android Version

Key Terms in Development
1. minSdkVersion
	- The minimum API level your app supports.
	- Devices below this version cannot install your app.
2. targetSdkVersion
	- The API level your app is tested against.
	- Tells Android how your app should behave (older behavior or new behavior).
3. compileSdkVersion
	- The API level used to compile your app.
	- You can only use APIs available in this version or lower.
- Each Android version corresponds to a specific API Level. For example:
	- If your app uses a feature introduced in API level 33 (Android 13), it won't work on a device with API level 30 (Android 11) unless you handle it with compatibility code
- Why API Level matters:
	- It tells developers what Android features are available.
	- It allows apps to target or require specific platform capabilities.

# Android Security Architecture


# Mobile Pentest Lab Setup Guide

This document provides a comprehensive guide to building a professional Android penetration testing laboratory. It covers two primary environments: **Android 9 (Stable Legacy)** and **Android 10 (Modern Standard)**, explaining the purpose of every command used.

---

## Step 1: Install Android Command-line Tools
Verify and install the essential Android SDK tools required to manage emulators and interact with devices via the terminal.
- **Path:** `C:\Users\Admin\AppData\Local\Android\Sdk\cmdline-tools\latest`
- **Platform-Tools Path:** `E:\Programs\Android\platform-tools`

### Adding Platform-Tools to Windows PATH (Global Access)
To run `adb`, `fastboot`, and other Android SDK tools from any directory or terminal:

```powershell
# Add platform-tools to User PATH permanently via PowerShell
$target = 'E:\Programs\Android\platform-tools'
$old = [Environment]::GetEnvironmentVariable('Path', 'User')

if ($old -notlike "*$target*") {
    $new = ($old.TrimEnd(';') + ';' + $target)
    [Environment]::SetEnvironmentVariable('Path', $new, 'User')
    Write-Host "Successfully added to User PATH!"
} else {
    Write-Host "Path already exists in PATH."
}
```

**Verification:**
Open a new PowerShell / Command Prompt window and verify:
```powershell
adb version
```

---

---

## ADB Mindset: How to Think When Working with a Physical Device

> [!NOTE]
> ADB is not just a tool to install APKs. It is a direct bridge into the Android Linux kernel, equivalent to having an SSH session with root-adjacent access to the device's filesystem and process table.

### The Core Mental Model

When connecting to any Android device via ADB, think in three sequential layers:

```
RECON    ->   ANALYSIS    ->   ACTION
(what exists)  (what matters)   (what to do)
```

**Layer 1, Recon:** Understand the device before touching it.

```powershell
# OS version, API level, security patch, CPU architecture
adb shell getprop ro.product.brand
adb shell getprop ro.build.version.release
adb shell getprop ro.build.version.sdk
adb shell getprop ro.build.version.security_patch
adb shell getprop ro.product.cpu.abi

# Storage overview
adb shell df -h /data

# Battery state
adb shell dumpsys battery | grep level
```

**Layer 2, Analysis:** Find what consumes resources or contains targets.

```powershell
# Per-app data sizes (outputs Package Names + App/Data/Cache sizes)
adb shell dumpsys diskstats

# SD card and volume mounts
adb shell sm list-volumes all

# Inspect a specific folder size
adb shell du -sh /sdcard/Android/data/<package>/*
```

**Layer 3, Action:** Modify only after you understand the impact.

```powershell
# Remove files
adb shell rm -rf /path/to/target/*

# Move files to SD card
adb shell cp -a /storage/emulated/0/Folder/. /storage/<SD-ID>/Folder/

# Trim system cache
adb shell pm trim-caches 4000000000

# Reboot — forces Media Scanner re-index after bulk file deletions
adb reboot
```

---

### Authorization Troubleshooting: Device Shows `unauthorized`

> [!IMPORTANT]
> ADB requires an RSA key handshake between the PC and the device. If the authorization dialog never appears on the phone, the key exchange is blocked.

**Fix, Force Key Regeneration:**

```powershell
# Kill the daemon and delete existing keys
adb kill-server
Remove-Item "$env:USERPROFILE\.android\adbkey*" -Force

# Relaunch — device receives a fresh key and shows the Allow dialog
adb devices
```

> [!WARNING]
> On Samsung devices running Android 12+, the Auto Blocker feature (Settings > Security and Privacy > Auto Blocker) silently prevents the USB debugging authorization dialog from appearing. Disable it before attempting to authorize.

| Symptom | Cause | Fix |
| :--- | :--- | :--- |
| Dialog never appears | Screen locked during plug-in | Unlock screen, replug cable |
| Dialog never appears | Auto Blocker active | Settings > Security > Auto Blocker > Off |
| `unauthorized` persists after Allow | Old key not cleared | Developer Options > Revoke USB Debugging Authorizations |
| Device not detected at all | USB mode wrong | Notification bar > USB > File Transfer (MTP) |

---

### Safe Deletion Rule

> [!WARNING]
> Never delete via ADB without verifying the path and size first. The shell has no Recycle Bin.

```powershell
# 1. Verify what will be deleted
adb shell du -sh /path/to/target

# 2. Pull a backup to the PC if needed
adb pull /path/to/target C:\Backup\

# 3. Delete only after confirmation
adb shell rm -rf /path/to/target/*
```

---

### ADB as a Pentesting Surface Map

| Surface | Command | What to Look For |
| :--- | :--- | :--- |
| Installed packages | `pm list packages -f` | Third-party, debug, or suspicious apps |
| App permissions | `dumpsys package <pkg>` | Overprivileged apps |
| Running processes | `adb shell top` | Unexpected background services |
| Network connections | `adb shell ss -tulnp` | Open ports and listeners |
| Live logs | `adb logcat` | Sensitive data leaking in plaintext |
| Exported components | `dumpsys package` + grep `exported=true` | Attack surface entry points |

> [!TIP]
> After any bulk file deletion via ADB, run `adb reboot` to force the Android Media Scanner to re-index storage. Without this, the Settings > Storage screen will continue to display pre-deletion numbers.

---

## Step 2: Download the System Image

We use different system images depending on the testing requirements. 

### Option A: Android 9.0 (API 28)
Best for stability and legacy tools.
```powershell
sdkmanager.bat "system-images;android-28;google_apis;x86" "platforms;android-28"
```

### Option B: Android 10.0 (API 29)
Best for modern app compatibility and TLS 1.3.
```powershell
sdkmanager.bat "system-images;android-29;google_apis;x86_64" "platforms;android-29"
```

**Command Breakdown:**
- `sdkmanager.bat`: The tool used to download and update Android SDK packages.
- `"system-images;..."`: Downloads the actual OS image.
- `"platforms;..."`: Downloads the platform-specific files for that API level.

---

## Step 3: Create the Android Virtual Device (AVD)
We create distinct virtual devices for each testing scenario.

### 1. Create Android 9 Device (Pixel)
```powershell
avdmanager.bat create avd -n "PentestDevice_9" -k "system-images;android-28;google_apis;x86" --device "pixel"
```

### 2. Create Android 10 Device (Pixel 4)
```powershell
avdmanager.bat create avd -n "Pentest_Android10" -k "system-images;android-29;google_apis;x86_64" --device "pixel_4"
```

**Command Breakdown:**
- `avdmanager.bat`: The tool for creating and managing virtual devices.
- `-n "Name"`: Sets the name of your emulator.
- `-k "..."`: Specifies the "Kernel" or system image to use.
- `--device "..."`: Defines the hardware profile (e.g., Pixel or Pixel 4).

---

## Step 4: Run the Emulator with Writable System
Crucial for rooting and installing Burp Suite certificates.

**Command for Android 10:**
```powershell
emulator.exe -avd "Pentest_Android10" -writable-system -no-snapshot-load
```

**Command Breakdown:**
- `emulator.exe`: The program that runs the virtual machine.
- `-writable-system`: **(Crucial)** Allows modifying the system partition to install root certificates.
- `-no-snapshot-load`: Ensures a clean boot every time to avoid persistent state errors.

---

## Step 5: Verify Connection & Management

Android Debug Bridge (ADB)

### 1. Verification via ADB
```powershell
# List connected devices
adb.exe devices

# Verify OS version
adb.exe shell getprop ro.build.version.release
```

### 2. Troubleshooting & Maintenance
If the emulator hangs or shows a black screen:
```powershell
# 1. Kill hanging processes
taskkill /F /IM emulator.exe
taskkill /F /IM qemu-system-x86_64.exe
taskkill /F /IM adb.exe

# 2. Remove lock files (if emulator won't start)
Get-ChildItem -Path "$env:USERPROFILE\.android\avd\*.avd" -Filter *.lock -Recurse | Remove-Item -Force -Recurse

# 3. Black Screen Fix: 
# Disable "Launch in a tool window" in Android Studio Settings > Tools > Emulator.
```

---

## Why Android 9 (API 28) for Pentesting?
1. **Bypassing HTTPS (SSL Trust):** In Android 9, it is much easier to move certificates into the **System Store** once you have root access.
2. **Reliable Remounting:** Supports the `adb remount` command very reliably compared to newer versions with dynamic partitions.
3. **Tool Stability:** Analysis tools like **Frida** and **Xposed** are extremely stable on this version.
4. **Broad Compatibility:** Most modern apps still function on Android 9, making it a safe baseline.

---

## Why Android 10 (API 29) is the "New Standard"?
1. **Modern App Support:** Many banking and crypto apps now require at least Android 10 to run.
2. **Scoped Storage Testing:** Allows testing of newer Android permission models and storage restrictions.
3. **TLS 1.3 Support:** Necessary for intercepting traffic from apps that use the latest encryption standards.
4. **Frida/Magisk Maturity:** These tools are now fully stable on Android 10, providing a more modern testing environment.

---

# Quick Start Guide

### Launch Android 9
```powershell
& "$env:LOCALAPPDATA\Android\Sdk\emulator\emulator.exe" -avd "PentestDevice_9" -writable-system -no-snapshot-load
```

### Launch Android 10
```powershell
& "$env:LOCALAPPDATA\Android\Sdk\emulator\emulator.exe" -avd "Pentest_Android10" -writable-system -no-snapshot-load
```

### Establish Root Connection (Common for both)
```powershell
adb root
adb remount
adb shell whoami  # Should return 'root'
```

It is possible to use tools like "Mobile Security Framework" (MobSF) to test the security of mobile applications on platforms like Android and iOS

---
*Lab setup updated on 2026-04-20. Full documentation for both Android 9 and 10 environments.*

## Mobile Application Pentesting & Security Resources

### Courses & Structured Learning
1. [Hextree Android Map](https://app.hextree.io/map/android) — Visual interactive learning roadmap for Android application security.
2. [NowSecure Academy Learning Hub](https://www.nowsecure.com/academy-learning-hub/) — Comprehensive training courses covering Android and iOS security fundamentals.
3. [Android Application Security – MobileHackingLab](https://academy.mobilehackinglab.com/course/free-android-application-security-course) — Free structured training course on Android vulnerability assessment.
4. [iOS Application Security – MobileHackingLab](https://academy.mobilehackinglab.com/course/free-ios-application-security-course) — Free structured course for iOS application penetration testing.
5. [Awesome Mobile Security Collection – 8kSec](https://github.com/8kSec/awesome-mobile-security) — Curated GitHub repository of mobile security tools, research, and guidelines.
6. [Your First Android App – Hextree](https://app.hextree.io/courses/first-android-app) — Foundations of Android architecture and reverse engineering.
7. [Android Application Security & Penetration Testing – Mahara-Tech](https://maharatech.gov.eg/course/view.php?id=2384) — Structured mobile AppSec training course.
8. [OWASP Top 10 Mobile Risks – Mahara-Tech](https://maharatech.gov.eg/course/view.php?id=2255) — Practical overview of critical mobile risks.
9. [Mobile Application (APK) Analysis Training – Hackviser](https://hackviser.com/trainings/mobile-application-apk-analysis) — Practical APK reverse engineering walkthrough.
10. [Android AppSec Notes – Sallam GitBook](https://sallam.gitbook.io/sec-88/android-appsec) — Field guide to Android assessment methodologies.
11. [Android Pentesting Field Guide – A0xTrojan Notion](https://www.notion.so/Android-Pentesting-A0xTrojan-17b90050c67180d8a453fb4dfb6cfd2c) — Practical cheatsheet, bypass techniques, and command notes.

### Hands-On Practical Labs & Workshops
1. [Mobile Hacking Labs – MobileHackingLab](https://academy.mobilehackinglab.com/free-mobile-hacking-labs) — Real-world hands-on vulnerable mobile lab scenarios.
2. [Android & iOS Security Challenges – 8kSec Battle](https://www.8ksec.io/battle/) — Interactive vulnerability discovery challenges for mobile platforms.
3. [OWASP MASTG Testing Guide & Checklist](https://mas.owasp.org/MASTG/) — Authoritative manual and automated testing procedures for Android and iOS.
4. [Free Practical Workshop – 7ASecurity](https://7asecurity.com/free-workshop-mobile-practical) — Hands-on mobile application exploitation and vulnerability workshop.
5. [TryHackMe | Mobile Malware Analysis](https://tryhackme.com/room/mma) — Practice analyzing mobile threats; covers Cabir PoC worm history and static analysis.
6. [TryHackMe | Malware Introductory](https://tryhackme.com/room/malmalintroductory) — Foundational malware triage and reversing concepts.
7. [TryHackMe | iOS Forensics](https://tryhackme.com/room/iosforensics) — Extracting and inspecting artifacts on iOS devices.
8. [TryHackMe | Android Malware Analysis](https://tryhackme.com/room/androidmalwareanalysis) — Decompilation, manifest inspection, and suspicious behavior analysis.
9. [TryHackMe | Android Hacking 101](https://tryhackme.com/room/androidhacking101) — Hands-on exploitation of vulnerable Android components.

### Vulnerable Practice Applications (Intentionally Vulnerable Apps & Crackmes)

#### Android Vulnerable Applications
1. [AndroGoat](https://github.com/satishpatnayak/AndroGoat) — Intentionally vulnerable Android app demonstrating OWASP Mobile Top 10 risks in Kotlin.
2. [DIVA (Damn Insecure and Vulnerable App)](https://github.com/payatu/diva-android) — Classic training app for insecure storage, access control, and IPC flaws.
3. [Insecure Bank v2](https://github.com/dineshshetty/Android-InsecureBankv2) — Client-server vulnerable banking app simulating real-world financial app vulnerabilities.
4. [Damn Vulnerable Bank](https://github.com/rewanthtammana/Damn-Vulnerable-Bank) — Modern vulnerable banking application designed for intermediate Android pentesting.
5. [Insecure Shop](https://github.com/hax0rgb/InsecureShop) — E-commerce vulnerable app written in Kotlin focusing on modern Android architecture flaws.
6. [OWASP MASTG Hacking Playground](https://github.com/OWASP/MASTG-Hacking-Playground) — Official collection of iOS and Android apps demonstrating specific vulnerabilities and verification techniques.
7. [OWASP Uncrackable Apps (Android)](https://mas.owasp.org/crackmes/) — Reverse engineering, anti-tampering, and root detection bypass challenges (Levels 1–4).
8. [OWASP Mobile Reference Applications](https://mas.owasp.org/MASTG/apps/) — Sample reference applications used across the OWASP MASTG guide.
9. [PwnShop Mobile](https://github.com/ctfsec/pwnshop-mobile) — Vulnerable mobile app for practicing mobile penetration testing and CTF techniques.
10. [Injured Android](https://github.com/B3nac/InjuredAndroid) — Flag-based vulnerable Android application covering modern exploitation primitives (activities, flags, broadcasts, deep links).
11. [DVAA / DVAC (Damn Vulnerable Android Components)](https://github.com/zinja-coder/Damn-Vulnerable-Android-Components) — Focused practice targets for insecure Activities, Services, Broadcast Receivers, and Content Providers.

#### iOS Vulnerable Applications
1. [DVIA v2 (Damn Vulnerable iOS App)](https://github.com/prateek147/DVIA-v2) — Modern Swift-based vulnerable application covering OWASP Mobile Top 10 for iOS.
2. [iGoat Swift](https://github.com/OWASP/iGoat-Swift) — OWASP's flagship vulnerable training app for iOS developers and security testers.
3. [OWASP iOS Uncrackable Apps](https://mas.owasp.org/crackmes/) — Binary protection, anti-debugging, and jailbreak detection bypass challenges (iOS Levels 1–2).
4. [Oversecured Vulnerable iOS App](https://github.com/oversecured/OversecuredVulnerableiOSApp) — Vulnerable iOS application containing real-world vulnerabilities reported in major iOS programs.

### Video Series & Masterclasses
1. [Android Pentesting Series – Byte Theories](https://www.youtube.com/playlist?list=PL1f72Oxv5SylOECx9M34pLZlNa7YkJJ14) — Step-by-step practical Android security walkthroughs.
2. [Android Bug Bounty Masterclass – B1scuit Security](https://www.youtube.com/watch?v=9STDmGIAJu4) — Deep-dive masterclass on methodology and finding high-impact mobile bugs.
3. [Android Development for Beginners - Full Course Part 1](https://www.youtube.com/watch?v=fis26HvvDII) — Essential Android fundamentals and UI lifecycle.
4. [Android Development for Beginners - Full Course Part 2](https://www.youtube.com/watch?v=RcSHAkpwXAQ) — Android services, intents, and background architecture.
5. [Android App Pentesting Playlist](https://youtube.com/playlist?list=PLNwotgTQ6zKEcBp3EOmDqw-DKRdOEHl_F) — Comprehensive video playlist on mobile pentesting workflow.
6. [Mobile Security Setup & Inspection Walkthrough](https://youtu.be/QwwLSyRzNwo) — Practical toolchain setup video guide.
7. [Android Application Pentesting Video Series](https://www.youtube.com/watch?v=hf5mOFtdsz0&list=PL4S940IsHJYWhhYOpBk6Y-U9nTQq2omae) — Exploitation tutorials and lab walkthroughs.

### Standards, Frameworks & Tooling
- [OWASP Mobile Application Security (MAS)](https://mas.owasp.org/) — Authoritative standard for mobile app security (MASVS & MASTG).
- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/) — The canonical 10 most critical security risks for mobile apps.
- [Mobile Security Framework (MobSF)](https://github.com/MobSF/Mobile-Security-Framework-MobSF) — Automated static and dynamic analysis framework.
- [Android Studio & App Tools](https://developer.android.com/studio) — Official IDE, SDK manager, and emulator platform.
- [Genymotion Desktop](https://www.genymotion.com/product-desktop/download/) — Fast, flexible Android emulation for security testing.
- [Android Platform Architecture Guide](https://developer.android.com/guide/platform) — Google's authoritative architectural overview.
- [MITRE ATT&CK Mobile Matrix (Android)](https://attack.mitre.org/matrices/mobile/android/) — Adversary tactics, techniques, and procedures targeting Android.
- [MITRE ATT&CK Mobile Matrix (iOS)](https://attack.mitre.org/matrices/mobile/ios/) — Adversary tactics, techniques, and procedures targeting iOS.

---

## Related Notes
- Hacker Methodology
- Web Application Penetration Testing Checklist
- PTES Framework
- Tools MOC

## Resources
> [!EXAMPLE] References
> - Primary Source: [Android Developer Tools](https://developer.android.com/tools/adb)
> - Complete reference links and resources are cataloged in this note's YAML frontmatter.
