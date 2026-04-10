## Arch Linux Bluetooth Setup & Troubleshooting Guide

This guide explains the complete process of fixing Bluetooth issues on Arch Linux — from "service not found" to fully working device connection and UI setup.

---

## 📌 Problem Overview

Common issues:

* `bluetooth.service could not be found`
* Bluetooth not detecting devices
* No Bluetooth icon in system tray

---

## ✅ Step 1: Install Required Packages

Bluetooth is not installed by default in minimal Arch setups.

```bash
sudo pacman -S bluez bluez-utils
```

Optional GUI tool:

```bash
sudo pacman -S blueman
```

---

## ✅ Step 2: Enable & Start Bluetooth Service

```bash
sudo systemctl enable bluetooth
sudo systemctl start bluetooth
```

Check status:

```bash
systemctl status bluetooth
```

Expected:

```
Active: active (running)
```

---

## ✅ Step 3: Verify Bluetooth Adapter

Run:

```bash
bluetoothctl
```

Then:

```bash
list
```

Expected:

```
Controller XX:XX:XX:XX:XX:XX
```

---

## ✅ Step 4: Scan & Connect Devices

Inside `bluetoothctl`:

```bash
power on
agent on
default-agent
scan on
```

Find your device, then:

```bash
pair XX:XX:XX:XX:XX:XX
trust XX:XX:XX:XX:XX:XX
connect XX:XX:XX:XX:XX:XX
```

Stop scanning:

```bash
scan off
```

---

## ⚠️ Step 5: Fix Blocked Bluetooth

Check:

```bash
rfkill list
```

If blocked:

```bash
rfkill unblock bluetooth
```

---

## ⚠️ Step 6: Hardware Detection

Check device:

```bash
lsusb
```

or

```bash
lspci
```

If no Bluetooth device appears → hardware/driver issue.

---

## 🎧 Step 7: Fix Audio (if connected but no sound)

Install PipeWire:

```bash
sudo pacman -S pipewire pipewire-pulse wireplumber
```

Reboot system.

---

## 🖥️ Step 8: Fix Missing Bluetooth Icon

### 🔍 Check session type:

```bash
echo $XDG_SESSION_TYPE
```

---

### 🧩 If using Wayland (common issue)

Install tray support:

```bash
sudo pacman -S gnome-shell-extension-appindicator
```

Enable:

```bash
gnome-extensions enable appindicatorsupport@rgcjonas.gmail.com
```

Logout/Login.

---

### 🧩 Alternative GUI tools

```bash
sudo pacman -S blueman
```

Run:

```bash
blueman-applet
```

---

### 🧩 If using X11

Login with:

* GNOME on Xorg
* KDE Plasma (X11)

Then:

```bash
blueman-applet
```

---

## 🧠 Root Cause Summary

| Issue             | Cause                   | Fix                  |
| ----------------- | ----------------------- | -------------------- |
| Service not found | Packages missing        | Install `bluez`      |
| No devices        | Adapter off / blocked   | `rfkill unblock`     |
| No icon           | Wayland tray limitation | Install appindicator |
| No sound          | Audio backend missing   | Install PipeWire     |

---

## 🚀 Quick Fix (All-in-One)

```bash
sudo pacman -S bluez bluez-utils blueman pipewire pipewire-pulse wireplumber
sudo systemctl enable bluetooth
sudo systemctl start bluetooth
rfkill unblock bluetooth
```

---

## ✅ Final Status Checklist

* [x] Bluetooth service running
* [x] Adapter detected (`hci0`)
* [x] Devices visible via scan
* [x] Successfully paired & connected
* [x] Audio working
* [x] Tray icon visible

---

## 📎 Notes

* Minimal Window Managers (i3, Hyprland) require manual tray setup
* Wayland may not support all tray icons by default
* Bluetooth works even without GUI tools via CLI

---

## 🎉 Done!

Your Arch Linux Bluetooth should now be fully functional.

If you want, I can also convert this into a cleaner GitHub-style project (with badges, screenshots, etc.).
