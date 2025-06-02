# Kali SSH Brute-Force + Wireshark Traffic Analysis

## 🎯 Objective
Simulate a brute-force SSH attack using Hydra on Kali Linux, capture the network traffic using Wireshark, and analyze it for intrusion detection patterns.

## 🛠 Tools Used
- Kali Linux (on UTM)
- Hydra (for SSH brute-force)
- Wireshark (for packet capture and analysis)
- OpenSSH on target VM (or metasploitable)

## ⚙️ Setup
- Target machine running SSH service (e.g. Metasploitable2 or Ubuntu with SSH enabled)
- Kali Linux VM with Hydra and Wireshark installed
- Both VMs running in VirtualBox or UTM, bridged or NAT network

## 🧪 Steps
1. Identified target IP with `nmap -p 22 <target-ip>`
2. Launched Hydra attack:  
   `hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://<target-ip>`
3. Simultaneously opened Wireshark and captured interface traffic
4. Filtered traffic with:  
   `tcp.port == 22` or `ssh`
5. Analyzed packet bursts, TCP stream, and login attempts
6. Noted the attack pattern: multiple failed login attempts within seconds

## 🔍 Key Findings
- Repetitive login failures visible via TCP stream
- SSH handshake visible pre-login
- Traffic pattern easily detectable via packet timing

## 🧠 What I Learned
- Basics of brute-force attack mechanics using Hydra
- How Wireshark visualizes malicious traffic
- How intrusion detection systems can flag brute-force behavior

## 🖼️ Screenshots
See `/screenshots/` folder for:
- Hydra CLI in action
- Wireshark filtered traffic
- Example TCP stream analysis

## 🔗 Resources
- [Hydra Documentation](https://tools.kali.org/password-attacks/hydra)
- [Wireshark Display Filters](https://wiki.wireshark.org/DisplayFilters)
