# 📱 Evolution Custom ROM Flashing Guide

🇻🇳 [Xem bằng Tiếng Việt](README.md)

> ⚠️ **Warning:** Flashing a custom ROM can erase all data and may brick your device if done incorrectly. Back up your data before starting.

---

## 🔧 Requirements Before You Start

- **ADB & Fastboot** installed on your computer
- **Bootloader unlocked**
- ROM file: `evo_rom.zip`
- Boot file: `boot.img`
- **USB Debugging** enabled on your phone
- Good quality USB cable

---

## 📋 Steps

### Step 1 — Flash Boot Image

Connect your phone via USB, boot into **Fastboot** mode, then run the command:

```bash
fastboot flash boot boot.img
```

> ✅ Wait for the terminal to show `OKAY` or `Finished`.

---

### Step 2 — Boot Into Recovery

After flashing the boot image, reboot into **Recovery** mode using the hardware key combo (usually `Volume Up + Power`) or the command:

```bash
fastboot reboot recovery
```

---

### Step 3 — Wipe Data

In the Recovery menu, perform a **Wipe Data / Factory Reset** to avoid conflicts with the old ROM.

```
Recovery Menu → Wipe → Wipe Data / Factory Reset → Confirm
```

> ⚠️ This will **erase all data** on your device. Make sure you have a backup.

---

### Step 4 — Enter ADB Sideload Mode

In Recovery, select the **ADB Sideload** option:

```
Recovery Menu → Apply Update → Apply from ADB
```

The screen will show a waiting state for connection from your computer.

---

### Step 5 — Flash ROM via ADB Sideload

On your computer, run the following command to start installing the Evolution ROM:

```bash
adb sideload evo_rom.zip
```

> ⏳ This may take a few minutes. Do not unplug the USB cable while flashing.  
> ✅ When complete, the Recovery screen will show a success message.

---

## 🚀 Done

After sideloading, go back to the Recovery menu and select **Reboot System Now** to boot into Evolution.

```
Recovery Menu → Reboot → Reboot System
```

The first boot may take **5–10 minutes**. Be patient.

---

## ❓ Common Errors & Fixes

| Error | Cause | Fix |
|-------|-------|-----|
| `fastboot: command not found` | ADB/Fastboot not installed | Install Android Platform Tools |
| `no devices found` | USB device not recognized | Check driver & USB cable |
| Sideload stops mid-way | Poor USB cable | Try a different cable |
| Device bootloops | Data not wiped | Wipe data and re-flash |

---

*🎉 Good luck flashing!*