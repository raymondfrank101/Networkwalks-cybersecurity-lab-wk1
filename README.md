# Networkwalks-cybersecurity-lab-wk1
This is my first cyber security lab project on github.
# 🖥️ Cybersecurity Lab Setup

![VirtualBox](https://img.shields.io/badge/Hypervisor-VirtualBox-183A61?logo=virtualbox&logoColor=white)
![Kali](https://img.shields.io/badge/OS-Kali%20Linux-557C94?logo=kalilinux&logoColor=white)
![Network](https://img.shields.io/badge/Network-NAT%20Network-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Use](https://img.shields.io/badge/Use-Educational%20Only-red)

> An isolated virtual lab for practising ethical hacking, scanning and security research, without risking my real computer or home network.

---

## 📑 Table of Contents
1. [Overview](#-overview)
2. [Objectives](#-objectives)
3. [Lab Configuration](#-lab-configuration)
4. [Setup Steps](#-setup-steps)
5. [Verification](#-verification)
6. [Problems & Solutions](#-problems--solutions)
7. [What I Learned](#-what-i-learned)
8. [Next Steps](#-next-steps)
9. [Ethical Use](#-ethical-use)
10. [Tools Used](#-tools-used)
11. [Author](#-author)

---

## 📌 Overview

I built a self-contained practice environment on my own laptop using **Kali Linux inside Oracle VirtualBox**. Everything I run stays inside the virtual machine and never touches my host system or home network.

The VM sits on a private network (`[NatNetwork]`, `[10.0.0.0/24]`) with a fixed IP of `[10.0.0.2]`. A known address makes the lab easier to document, test and reuse, and more machines can join later as practice targets.

**Result:** a working Kali VM with internet access, file sharing with the host, and a clean snapshot to restore at any time.

---

## 🎯 Objectives

- [x] Install and configure VirtualBox
- [x] Set up Kali Linux as a virtual machine
- [x] Create a private NAT Network
- [x] Assign Kali a static IP address
- [x] Confirm internet and DNS access
- [x] Take a snapshot as a recovery point


## ⚙️ Lab Configuration

| 🧩 Component | ⚙️ Setting |
|---|---|
| 🖥️ Host OS | [Windows 10/11] |
| 🧠 Host RAM | [e.g. 8 GB] |
| ⚡ Processor | [e.g. Intel Core i5] |
| 🧰 Hypervisor | VirtualBox [version] |
| 🐉 Guest OS | Kali Linux [version] |
| 🧠 Kali RAM | [e.g. 2048 MB] |
| 🌐 Network | [NatNetwork] |
| 📡 Network range | [10.0.0.0/24] |
| 📍 Kali IP | [10.0.0.2/24] |
| 🚪 Gateway | [10.0.0.1] |
| 🌍 DNS | [8.8.8.8] |

---

## 🪜 Setup Steps

### Step 1: Install 7-Zip
Installed 7-Zip to extract the Kali VM package, which downloads as a `.7z` archive.

### Step 2: Install VirtualBox
Installed Oracle VirtualBox as the hypervisor that runs the virtual machines.

### Step 3: Create the NAT Network
Created a NAT Network named `[NatNetwork]` with the range `[10.0.0.0/24]`.

<img width="960" height="540" alt="capture 1" src="https://github.com/user-attachments/assets/6ae9ed7f-e326-4986-913c-592a640971aa" />


### Step 4: Import Kali Linux
Imported the official Kali VM and attached its network adapter to `[NatNetwork]`.
<img width="960" height="540" alt="capture 3" src="https://github.com/user-attachments/assets/bd540a05-6332-4993-95fa-3e97da15c82d" />


<img width="960" height="540" alt="capture 2" src="https://github.com/user-attachments/assets/e8922a82-d0e2-4114-aa7e-a52a19639b75" />


### Step 5: Configure the Static IP
Set the static address `[10.0.0.2/24]` on Kali (details in [Problems & Solutions](#-problems--solutions)).

<img width="960" height="540" alt="capture 4" src="https://github.com/user-attachments/assets/2a5e1ecf-f935-4130-8d9e-9af6b7eabbed" />


### Step 6: Test Connectivity
Ran `ping -c 4 8.8.8.8` and `ping -c 4 google.com` to confirm internet access and DNS.

<img width="960" height="540" alt="capture 5" src="https://github.com/user-attachments/assets/606dced7-e8d5-47ea-8f66-8ddd0d4098ca" />


### Step 7: Take a Snapshot
Took a snapshot named `[My fresh kali linux]` as a clean baseline to restore if anything breaks.

<img width="960" height="540" alt="capture 6" src="https://github.com/user-attachments/assets/3824ea91-9331-4fb2-9543-e414d99ab896" />


---

## 🔎 Verification

| ✅ Test | 💻 Command | 🎯 Result |
|---|---|---|
| Check IP address | `ip a` | [10.0.0.2/24 shown] |
| Test gateway | `ping -c 4 [gateway]` | Replies received |
| Test internet | `ping -c 4 8.8.8.8` | Replies received |
| Test DNS | `ping -c 4 google.com` | Name resolved |
| Check Kali version | `cat /etc/os-release` | [version shown] |
| Check Nmap | `nmap --version` | Version displayed |
| Confirm snapshot | VirtualBox Snapshots tab | [snapshot name] listed |

---

## 🐞 Problems & Solutions

### Problem 1: Setting a static IP on Kali
Kali was getting its address automatically from DHCP, but the lab needed a fixed one.

**Solution:**
```bash
nm-connection-editor &
```
1. Select the wired connection and click the gear icon.
2. Open the **IPv4 Settings** tab and set the method to **Manual**.
3. Enter address `[10.0.0.2]`, netmask `24`, gateway `[10.0.0.1]`, DNS `[8.8.8.8]`.
4. Save, then disconnect and reconnect.
5. Verify with `ip a` and `ping -c 4 8.8.8.8`.
---

## 💡 What I Learned

- 🌐 How a NAT Network lets VMs talk to each other and the internet
- 📍 How to set and verify a static IP
- 📸 Why a clean snapshot matters before risky experiments
- 📝 Why documenting every step is part of professional security work

---

## 🚀 Next Steps

- [ ] Add a vulnerable target VM (e.g. Metasploitable or DVWA)
- [ ] Run a first Nmap scan from Kali against the target
- [ ] Capture and analyse traffic with Wireshark
- [ ] Document each exercise in its own folder

---

## 🔐 Ethical Use

This lab is for **learning only**. I only test systems I own or have explicit permission to test.

---

## 🧰 Tools Used

| 🛠️ Tool | 📝 Purpose | 🔗 Website |
|---|---|---|
| 7-Zip | Extract the Kali VM package | [7-zip.org](https://7-zip.org) |
| Oracle VirtualBox | Run the virtual machines | [virtualbox.org](https://virtualbox.org) |
| Kali Linux | Security-focused operating system | [kali.org](https://kali.org) |
| GitHub | Host and document the project | [github.com](https://github.com) |
| Shields.io | README badges | [shields.io](https://shields.io) |

---

## 👤 Author

**Raymond Frank-Nnokwe**
Cybersecurity intern. Batch B084
🔗 LinkedIn: [https://www.linkedin.com/in/raymond-frank-nnokwe-792669383/]
