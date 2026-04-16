<div align="center">

# 🔌 Teleport USB

**Virtual USB Network solution for sharing USB devices over the network**

[![Version](https://img.shields.io/badge/Version-1.3.0-blue?style=flat-square)](https://github.com/devguru-corp/TeleportUSB/releases)
[![OS](https://img.shields.io/badge/OS-Windows%2010%2064bit-0078D6?style=flat-square&logo=windows)](https://github.com/devguru-corp/TeleportUSB)
[![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)](https://github.com/devguru-corp/TeleportUSB)
[![Visitors](https://vbr.nathanchung.dev/badge?page_id=devguru-corp.TeleportUSB&color=55acb7&style=flat-square&logo=github)](https://github.com/devguru-corp/TeleportUSB)

<br>

[**한국어**](./README.md) | [**English**](./README_EN.md)

<br>

<img src="https://img.shields.io/badge/DEVGURU-Teleport%20USB-orange?style=for-the-badge&logo=usb&logoColor=white" alt="Teleport USB" />

<br><br>

```
┌──────────────┐                              ┌──────────────┐
│  Server PC   │        Network Share         │  Client PC   │
│              │  ◀━━━━━━━━━━━━━━━━━━━━━━━━▶  │              │
│  🔌 USB Port  │       TCP/IP Connection      │  💻 Remote Use │
└──────────────┘                              └──────────────┘
```

</div>

---

## 📑 Table of Contents

<details>
<summary><b>Click to expand</b></summary>

- [📦 Download](#-download)
- [⚙️ System Requirements](#️-system-requirements)
- [🖥️ Server Setup](#️-server-setup-pc-with-usb-device)
- [💻 Client Setup](#-client-setup-pc-to-use-usb-remotely)
- [✅ Verification](#-verification)
- [🔧 Troubleshooting](#-troubleshooting)
- [📌 Notes](#-notes)

</details>

---

## 📦 Download

| File | Target | Download |
|:----:|:------:|:-------:|
| **Server** Installer | PC with USB device attached | [⬇️ Download](./TeleportUSB_server_installer_64bit.msi) |
| **Client** Installer | PC to use USB device remotely | [⬇️ Download](./TeleportUSB_client_installer_64bit.msi) |

---

## ⚙️ System Requirements

> **Both** Server PC and Client PC must meet the requirements below.

| Item | Minimum Spec |
|:----:|:------------:|
| **OS** | Windows 10 64bit or later |
| **Processor** | Intel i3 Dual Core or better |
| **RAM** | 4GB or more |
| **Permissions** | Administrator (required for MSI install) |
| **Network** | Server ↔ Client on the same subnet |

### 🌐 How to find the Server PC's IP address

You will need the Server IP when setting up the Client. Check it on the **Server PC** beforehand.

<details>
<summary><b>📋 View IP lookup instructions</b></summary>

<br>

**Option 1 — Command Prompt (cmd)**

```cmd
ipconfig
```

Look for the **IPv4 Address** in the output:

```
Ethernet adapter:
   IPv4 Address . . . . . . . : 192.168.100.9    ← Note this value
   Subnet Mask  . . . . . . . : 255.255.255.0
   Default Gateway  . . . . . : 192.168.100.1
```

**Option 2 — PowerShell**

```powershell
(Get-NetIPAddress -AddressFamily IPv4 | Where-Object { $_.InterfaceAlias -notlike "*Loopback*" }).IPAddress
```

</details>

---

## 🖥️ Server Setup (PC with USB device)

> **📍 Perform these steps on the PC where the USB device is physically connected.**

### Step 1 — Run the installer

1. Double-click `TeleportUSB_server_installer_64bit.msi`
2. UAC prompt → click **`Yes`**
3. Check **`accept the terms in the License Agreement`**
4. Click **`Install`**

<div align="center">
<img src="images/server-install-wizard.png" width="500" alt="Server install wizard">
<br><em>Accept the license agreement and click Install</em>
</div>

<br>

5. When finished → click **`Finish`**

### Step 2 — Launch the program

1. Open **`Teleport USB Server`** from the desktop or Start menu
2. Confirm the Teleport USB icon appears in the system tray (bottom-right)

### Step 3 — Share a USB device

1. Plug the USB device into the Server PC
2. In the program window, click **`Share`** next to the device

<div align="center">
<img src="images/server-share-button.png" width="500" alt="Click Share button">
<br><em>Click the Share button next to the device</em>
</div>

<br>

3. ✅ **Sharing success indicators:**

<div align="center">
<img src="images/server-share-complete.png" width="500" alt="Share complete">
<br><em>Green border = sharing active</em>
</div>

| Checkpoint | Status |
|:----------:|:------:|
| USB icon border | 🟢 Green |
| Share button | Disabled (grayed out) |
| Device name | Displayed |

> 💡 **To stop sharing:** click the **`x`** button next to the device

---

## 💻 Client Setup (PC to use USB remotely)

> **📍 Perform these steps on the PC that will use the USB device remotely.**

### Step 1 — Run the installer

1. Double-click `TeleportUSB_client_installer_64bit.msi`
2. UAC prompt → click **`Yes`**
3. Check **`accept the terms in the License Agreement`**
4. Click **`Install`**

<div align="center">
<img src="images/client-install-wizard.png" width="500" alt="Client install wizard">
<br><em>Accept the license agreement and click Install</em>
</div>

<br>

5. When finished → click **`Finish`**

### Step 2 — Launch the program

1. Open **`Teleport USB Client`** from the desktop or Start menu

### Step 3 — Connect to the Server

1. Click **`Add Server`** at the top
2. Enter the **Server IP** (e.g., `192.168.100.9`) → click **`Add`**

<div align="center">
<img src="images/client-add-server-ip.png" width="500" alt="Enter Server IP">
<br><em>Enter the Server PC's IP address and click Add</em>
</div>

<br>

3. Shared devices are **auto-discovered** → click **`Connect`**

<div align="center">
<img src="images/client-device-found.png" width="500" alt="Device found">
<br><em>Click Connect on the discovered device</em>
</div>

<br>

4. ✅ **Connection success indicators:**

<div align="center">
<img src="images/client-connect-complete.png" width="500" alt="Connection complete">
<br><em>Green border = connected</em>
</div>

| Checkpoint | Status |
|:----------:|:------:|
| USB icon border | 🟢 Green |
| Connect button | Disabled (grayed out) |

> 💡 **To disconnect:** click the **`x`** button next to the device

---

## ✅ Verification

Once connected, the USB device works on the Client PC **exactly as if it were plugged in locally**.

<div align="center">
<img src="images/client-usb-drive-usage.png" width="600" alt="USB drive in File Explorer">
<br><em>The shared USB drive appears in File Explorer on the Client PC</em>
</div>

<br>

### ✔️ Checklist

| # | Item | Expected Result |
|:-:|:-----|:----------------|
| 1 | Green border on Server USB icon | ✅ Device shared |
| 2 | Device appears after `Add Server` on Client | ✅ Network OK |
| 3 | Green border on Client USB icon | ✅ Device connected |
| 4 | USB drive visible in File Explorer | ✅ Ready to use |
| 5 | Read / write / delete operations work | ✅ Fully operational |

---

## 🔧 Troubleshooting

<details>
<summary><b>❌ Device not found</b></summary>

<br>

| Cause | Solution |
|:------|:---------|
| Device not shared on Server | Verify `Share` was clicked in the Server program |
| Wrong IP address | Re-check with `ipconfig` on the Server PC |
| Different network | Ensure both PCs are on the same subnet |
| Firewall blocking | See **Firewall setup** below |

</details>

<details>
<summary><b>🔥 Firewall setup (Server PC)</b></summary>

<br>

1. Search for **`Windows Defender Firewall`** and open it
2. Click **`Allow an app or feature through Windows Defender Firewall`**
3. Click **`Change settings`** → **`Allow another app`**
4. Browse to the Teleport USB Server executable and add it
5. Check both **Private** and **Public** networks → click **`OK`**

Or via PowerShell (Admin):

```powershell
New-NetFirewallRule -DisplayName "Teleport USB Server" -Direction Inbound -Action Allow -Program "C:\Program Files\DEVGURU\TeleportUSB\TeleportUSB_Server.exe"
```

</details>

<details>
<summary><b>⚠️ Device connected but not working</b></summary>

<br>

| Cause | Solution |
|:------|:---------|
| Missing driver | Install the USB device driver on the Client PC |
| Device conflict | Close any programs using the device on the Server PC |
| Program not running | Ensure both Server and Client programs are running |
| Unstable network | Use wired LAN; if on Wi-Fi, check signal strength |

</details>

---

## 📌 Notes

| Item | Details |
|:----:|:--------|
| **Version** | Server and Client must be the same version (currently v1.3.0.0) |
| **Concurrency** | Only **one Client** can connect to a USB device at a time |
| **Connection** | Disconnects automatically if the Server shuts down or the USB is unplugged |
| **Uninstall** | `Settings` → `Apps` → search `Teleport USB` → `Uninstall` |

---

<div align="center">

**Made by [DEVGURU Corp.](https://github.com/devguru-corp)**

<sub>Copyright &copy; 2023 DEVGURU. All rights reserved.</sub>

</div>
