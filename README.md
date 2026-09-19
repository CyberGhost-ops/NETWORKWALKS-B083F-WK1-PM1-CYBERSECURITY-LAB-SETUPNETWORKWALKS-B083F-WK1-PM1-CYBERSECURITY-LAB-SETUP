 Cybersecurity Lab Environment Setup

Setting up a personal virtual lab for cybersecurity practice and hands-on learning

````markdown

![Skill](https://img.shields.io/badge/Skill-Cybersecurity-808080)
![Ver](https://img.shields.io/badge/Ver-Virtualbox%20v7.2-blue)
![Kali Linux](https://img.shields.io/badge/Kali%20Linux-v2026.1-orange)
![Skill](https://img.shields.io/badge/Skill-Linux-808080)
![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-4CAF50)
![Skill](https://img.shields.io/badge/Skill-Virtualization-808080)
![GitHub](https://img.shields.io/badge/-GitHub-181717?logo=github&logoColor=white)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-e74c3c)
![Author](https://img.shields.io/badge/Author-Sulaiman-e74c3c)

---

## 📌 Project Overview

This project documents my hands-on cybersecurity and networking lab environment built using **Oracle VirtualBox** and **Kali Linux**.

The purpose of the lab is to develop practical skills in:

- Cybersecurity
- Linux administration
- Network configuration
- Virtualization
- Network reconnaissance
- Network troubleshooting
- Security testing in an isolated environment

The lab uses the private network:

```text
10.0.0.0/24
````

All testing is performed within an authorized lab environment.

---

# 🎯 Objective

The main objectives of this project are to:

1. Build a virtual cybersecurity laboratory.
2. Configure Kali Linux inside VirtualBox.
3. Create and configure a private virtual network.
4. Understand IP addressing and subnetting.
5. Identify hosts on the lab network.
6. Test network connectivity.
7. Perform basic network reconnaissance.
8. Practice Linux networking commands.
9. Document findings and troubleshooting steps.
10. Develop practical cybersecurity skills through hands-on exercises.

---

# 🏗️ Network Topology

The lab uses a private `10.0.0.0/24` network.

### Network

```text
Network:       10.0.0.0/24
Subnet Mask:   255.255.255.0
Usable Hosts:  10.0.0.1 - 10.0.0.254
```

### Example topology

```text
                 ┌──────────────────────┐
                 │      Host Machine    │
                 │      Windows/Linux   │
                 └──────────┬───────────┘
                            │
                     VirtualBox Network
                            │
                 ┌──────────┴───────────┐
                 │                      │
          ┌──────▼──────┐       ┌──────▼──────┐
          │  Kali Linux │       │ Target VM   │
          │             │       │             │
          │ 10.0.0.X    │       │ 10.0.0.X    │
          └─────────────┘       └─────────────┘
```

> **Note:** Replace the example IP addresses with the actual addresses assigned to your machines.

---

# 💻 VirtualBox Setup

## Software Used

| Component        | Version           |
| ---------------- | ----------------- |
| Virtualization   | VirtualBox 7.2    |
| Operating System | Kali Linux 2026.1 |
| Network          | 10.0.0.0/24       |
| Platform         | Virtual Machine   |
| Host OS          | Windows/Linux     |

---

## VirtualBox Configuration

The Kali Linux virtual machine was configured with:

* Sufficient CPU resources
* Allocated RAM
* Virtual hard disk
* Network adapter
* Bootable Kali Linux ISO
* Private lab networking

### Network Adapter

The VM's network adapter was configured for the isolated cybersecurity lab network.

Example:

```text
Adapter 1
    Attached to: Host-only Adapter
    Network:     10.0.0.0/24
```

> If you used NAT, Bridged Adapter, or another VirtualBox networking mode, update this section accordingly.

---

# 🐉 Kali Linux

Kali Linux is the primary security-testing operating system used in this lab.

### System Information

```bash
uname -a
```

Check the Kali release:

```bash
cat /etc/os-release
```

Check the current user:

```bash
whoami
```

Check the hostname:

```bash
hostname
```

---

# 🌐 Network Configuration

To view the network interfaces:

```bash
ip addr
```

or:

```bash
ip a
```

To view routing information:

```bash
ip route
```

To view DNS configuration:

```bash
cat /etc/resolv.conf
```

---

# 🔎 Network Connectivity

Connectivity was tested using `ping`.

### Test localhost

```bash
ping -c 4 127.0.0.1
```

### Test another lab machine

```bash
ping -c 4 <TARGET-IP>
```

Example:

```bash
ping -c 4 10.0.0.20
```

Successful replies indicate that the machines can communicate across the configured network.

---

# 🛠️ Commands Used

## 1. Display IP Address

```bash
ip addr
```

Used to identify the IP address assigned to the Kali machine.

---

## 2. Display Routing Table

```bash
ip route
```

Used to identify the configured network route and gateway.

---

## 3. Test Connectivity

```bash
ping <IP>
```

Used to determine whether another authorized host is reachable.

---

## 4. Identify Open Ports

Within the authorized lab environment:

```bash
nmap <TARGET-IP>
```

Example:

```bash
nmap 10.0.0.20
```

For service detection:

```bash
nmap -sV <TARGET-IP>
```

> Only scan systems you own or have explicit permission to test.

---

## 5. Discover Hosts

To identify active systems within the lab network:

```bash
nmap -sn 10.0.0.0/24
```

This performs host discovery without performing a full port scan.

---

## 6. Check Listening Services

```bash
ss -tuln
```

This displays listening TCP/UDP sockets on the Kali machine.

---

## 7. Check ARP/Neighbor Information

```bash
ip neigh
```

This displays known neighboring devices on the local network.

---

# 📸 Screenshots

Screenshots are included to document the configuration and results of each stage.

## VirtualBox Configuration

![VirtualBox Configuration](screenshots/virtualbox-config.png)

Shows the VirtualBox configuration used for the Kali Linux VM.

---

## Kali Linux Desktop

![Kali Linux](screenshots/kali-desktop.png)

Shows the Kali Linux environment used throughout the lab.

---

## IP Configuration

![IP Configuration](screenshots/ip-config.png)

Example command:

```bash
ip addr
```

This screenshot demonstrates the IP address assigned to the Kali Linux machine.

---

## Network Connectivity

![Ping Test](screenshots/ping-test.png)

Example:

```bash
ping -c 4 <TARGET-IP>
```

This demonstrates connectivity between the lab machines.

---

## Network Discovery

![Nmap Scan](screenshots/nmap-scan.png)

Example:

```bash
nmap -sn 10.0.0.0/24
```

The scan was performed against the authorized lab network.

---

## Port Scanning

![Nmap Ports](screenshots/nmap-ports.png)

Example:

```bash
nmap -sV <TARGET-IP>
```

This was used to identify available services on the authorized target.

---

# 📊 Findings

During the lab, the following observations were made:

### Network Configuration

The lab successfully used the private:

```text
10.0.0.0/24
```

network.

### Connectivity

Network connectivity was tested between the virtual machines using `ping`.

### Host Discovery

Network discovery was performed to identify active hosts within the authorized lab environment.

### Service Discovery

Nmap was used to identify services and open ports on the authorized target machine.

### Linux Networking

The following Linux networking concepts were practiced:

* IP addressing
* Subnetting
* Routing
* Network interfaces
* ARP/neighbor discovery
* TCP/UDP ports
* Network services
* DNS configuration

---

# 🧠 Lessons Learned

This project helped reinforce several practical cybersecurity concepts.

## 1. Virtualization

VirtualBox makes it possible to build isolated environments for cybersecurity experimentation without directly exposing testing activities to production systems.

## 2. Network Configuration

Understanding IP addresses, subnet masks, gateways, and network interfaces is fundamental to cybersecurity.

## 3. Linux

Kali Linux provides a powerful environment for learning security and networking through the command line.

## 4. Network Reconnaissance

Tools such as Nmap can provide information about hosts, ports, and services within an authorized environment.

## 5. Troubleshooting

Basic commands such as:

```bash
ip addr
ip route
ping
ip neigh
ss
```

are useful when diagnosing network connectivity and configuration problems.

## 6. Security Awareness

A major lesson from this lab is the importance of understanding what is exposed on a network. Open ports and unnecessary services can increase an organization's attack surface.

---

# 🛡️ Security Considerations

All network scanning and security testing documented in this project was performed against systems within an authorized lab environment.

The techniques demonstrated here should only be used against:

* Systems you own
* Lab environments
* CTF platforms
* Systems where you have explicit authorization to test

Unauthorized scanning or exploitation of systems can be illegal.

---

# 🚀 Future Improvements

Future versions of this lab may include:

* [ ] Add a second Linux target
* [ ] Add a Windows target
* [ ] Configure a dedicated firewall
* [ ] Add Wireshark packet analysis
* [ ] Practice vulnerability assessment
* [ ] Configure SSH between lab machines
* [ ] Explore IDS/IPS concepts
* [ ] Document additional Nmap techniques
* [ ] Create network diagrams
* [ ] Add incident-response exercises

---

# 📚 Skills Demonstrated

```text
Cybersecurity
Linux
Networking
Virtualization
Network Reconnaissance
Nmap
IP Addressing
Subnetting
Troubleshooting
Security Testing
Technical Documentation
```

---

# 👨‍💻 Author

**Sulaiman**

Cybersecurity learner | Linux | Networking | Virtualization

---

## ⭐ Project

This project is part of my hands-on cybersecurity learning journey through **NetworkWalks**.

If you found this project useful, feel free to ⭐ the repository.

````

### Recommended GitHub folder structure

I'd organize the repository like this:

```text
NetworkWalks/
│
├── README.md
│
├── screenshots/
│   ├── virtualbox-config.png
│   ├── kali-desktop.png
│   ├── ip-config.png
│   ├── ping-test.png
│   ├── nmap-scan.png
│   └── nmap-ports.png
│
├── diagrams/
│   └── network-topology.png
│
└── notes/
    └── commands.md
````
