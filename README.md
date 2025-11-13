# Android Security Lab
## 📌 Reverse-Engineering Android Apps — Playlist

A set of practical videos on Android reverse engineering: smali patching, root detection bypass, Frida scripts, traffic interception, emulator workflows, and system internals.

---

### 1. **[How to Bypass Android Root Checks via Smali Patching (No Frida). Part 2](https://youtu.be/WC_FdEfaFug?si=1wsm0p8-GSzoCrvd)**
Static root detection bypass using smali modifications and APKTool.

---

### 2. **[Android Root Detection Bypass — Reverse Engineering. Part 1](https://www.youtube.com/watch?v=ymE1U5iC6F0)**
Finding and patching root checks with Jadx + APKTool. Entry-level RE workflow.

---

### 3. **[Frida on Fire | Dynamic Analysis for Android & iOS](https://youtu.be/xGKLkzQCyGU?si=Ak1xBe83QvDjYr2e)**
Dynamic instrumentation basics with Frida: hooking, tracing, and inspecting runtime behavior.

---

### 4. **[Android Under the Hood | Where Do Apps Live?](https://youtu.be/sJF0aVaV4YM?si=qBjrxpyd1bNtJLgt)**
Overview of Android’s filesystem layout and where applications store their data.

---

### 5. **[Working with Android Emulator | Terminal, ADB Commands](https://youtu.be/IMz_oW0k4oQ?si=_-4945juN5L4ugH9)**
Using ADB, shell commands, emulator configs, and CLI workflows for analysis.

---

### 6. **[HACKING Android Applications | Real Examples](https://youtu.be/Ai1agob7q_k?si=HcPXUDzr4w5w_jsN)**
Hands-on examples of Android application manipulation and vulnerability exploration.

---

### 7. **[Reverse Engineering Android Apps for Beginners | APKTool, Jadx](https://youtu.be/OwVO3Hk5y9s?si=fCuYFiAq34YGSIvg)**
Beginner-friendly introduction to static analysis, decompilation, and smali patching.

---

### 8. **[Intercepting Android App Traffic | Charles Proxy + Frida Tutorial](https://youtu.be/HCKXLWbrF8k?si=i-4jXYVCiwdDpygr)**
Combining traffic interception with dynamic hooks for deeper analysis.

---

### 9. **[Interception of Traffic on Android | Setting up an Emulator](https://youtu.be/yWsBhp-Fg3k?si=INFFphetSuWUygu4)**
Configuring Android emulator networking for MITM, HTTPS interception, and analysis.

## 🔧 Full Android Reverse Engineering Workflow

A compact end-to-end workflow for unpacking, patching, rebuilding, installing, and analyzing Android apps using APKTool + Frida on a rooted emulator.

---

### 📦 1. Unpack & Rebuild APK (APKTool)
apktool d app.apk -o unpacked
apktool b unpacked -o app_patched.apk

---

### 🔐 2. Start Rooted Emulator (optional)
adb root

---

### 🧩 3. Push & Run Frida Server
adb push frida-server /data/local/tmp/
adb shell chmod +x /data/local/tmp/frida-server
adb shell /data/local/tmp/frida-server &
---

### 📲 4. Install Target APK on the Emulator
adb install fdroid.apk
---

### 🧰 5. Install Frida Tools (Host Side)
python -m venv new_venv
source new_venv/bin/activate
pip3 install frida-tools
---

### 🔍 6. Find the Target Process on the Emulator
adb shell
adb top
---

### 🎯 7. Run Frida Script (example: SSL pinning bypass)

frida -U -p <process_id> -l ssl-pin.js
frida -U -n com.example.app -c codeshare/(script name from codeshare)

