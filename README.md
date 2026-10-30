# NetworkWalks — Cybersecurity Lab Setup

**Week 1 · Practical Module 1**  
**Project:** Building an isolated virtual lab for penetration testing and ethical hacking

---

## Table of Contents

- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Purpose of the Lab](#purpose-of-the-lab)
- [Lab Architecture](#lab-architecture)
- [Lab Configuration](#lab-configuration)
- [Lab Setup Procedure](#lab-setup-procedure)
- [Lab Verification](#lab-verification)
- [Security and Usage Notice](#security-and-usage-notice)

## Project Overview

This project documents the setup of a virtual cybersecurity and penetration-testing laboratory using **VirtualBox** and **Kali Linux**.

The goal is to create a controlled environment in which cybersecurity tools and techniques—including network scanning, reconnaissance, vulnerability assessment, and other security-testing activities—can be practised safely and repeatedly.

The lab uses a private virtual network. Additional virtual machines can be connected later and used as targets for authorised security testing.

## Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install or import Kali Linux as a virtual machine.
- Create a private NAT Network for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali Linux VM.
- Verify network connectivity and DNS resolution.
- Create a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

## Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorised security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

## Lab Architecture

The diagram below illustrates the laboratory architecture.

![Cybersecurity lab architecture](https://github.com/user-attachments/assets/403726b2-f6e0-46f3-9fbd-4a5b59d37551)

## Lab Configuration

| Component | Configuration |
|---|---|
| Host operating system | Windows 10 |
| Host RAM | 8 GB |
| Processor | Intel Core i7 |
| Hypervisor | VirtualBox 7.2 |
| Security operating system | Kali Linux 2026.2 |
| Kali Linux RAM (configuration summary) | 2,048 MB |
| Virtual network | NAT Network |
| Network address | `10.0.0.0/24` |
| Kali Linux IP address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS server | `8.8.8.8` |
| Future VM address range | `10.0.0.3–10.0.0.99` |

## Lab Setup Procedure

### Step 1: Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

### Step 2: Install VirtualBox

VirtualBox was installed to serve as the hypervisor for running the virtual machines.

### Step 3: Create the NAT Network

A dedicated NAT Network was created in VirtualBox with the following settings:

| Setting | Value |
|---|---|
| Network name | `NatNetwork` |
| IPv4 prefix | `10.0.0.0/24` |
| DHCP | Enabled |
| IPv6 | Disabled |

![VirtualBox NAT Network setup](https://github.com/user-attachments/assets/6a2cfeee-1fc4-4167-a634-57d552b05839)

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This configuration will allow future attacker and target VMs to communicate within the lab.

### Step 4: Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM's network adapter was configured as follows:

| Adapter setting | Value |
|---|---|
| Adapter | Adapter 1 |
| Attached to | NAT Network |
| Network | `NatNetwork` |
| Adapter type | Intel PRO/1000 MT Desktop (82540EM) |

**Memory allocated during import:** 6,161 MB

![Kali Linux shared-folder configuration](https://github.com/user-attachments/assets/1e5719f8-a876-47c6-bad8-78f88e5e9c53)

A shared folder was also configured to transfer required files between the host operating system and the Kali Linux VM.

### Step 5: Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

The example configuration is:

| Network setting | Value |
|---|---|
| IP address | `10.0.0.2` |
| Subnet mask | `255.255.255.0` |
| Gateway | `10.0.0.1` |
| DNS | `8.8.8.8` |

Using a consistent IP address makes it easier to document the lab and refer to the Kali Linux machine in future exercises.

![Kali Linux IP configuration](https://github.com/user-attachments/assets/095a99d9-738e-4143-8a08-34bedab57480)

### Step 6: Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

The snapshot represents the clean baseline of the laboratory. If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

## Lab Verification

The following checks were used to verify the laboratory setup:

| Test | Command | Expected result |
|---|---|---|
| Check IP address | `ip a` | Correct Kali Linux IP address is displayed. |
| Test gateway connectivity | `ping 10.0.0.1` | Successful replies are received. |
| Test internet connectivity | `ping 8.8.8.8` | Successful replies are received. |
| Test DNS resolution | `nslookup networkwalks.com` | The domain resolves successfully. |
| Verify Nmap installation | `nmap --version` | The installed Nmap version is displayed. |
| Verify snapshot | Restore the snapshot, then run `ip a` | The baseline configuration is restored. |

## Security and Usage Notice

> **Important:** Use this laboratory only to test systems that you own or for which you have explicit permission to perform security testing. Do not use the lab or its tools to attack unauthorised systems.

---

## Items to Confirm

Before treating this README as the final record of the setup, verify these configuration details against the actual VirtualBox settings:

1. **Kali Linux RAM:** The configuration summary lists **2,048 MB**, while the import procedure records **6,161 MB**. Confirm the actual VM memory allocation and make both entries consistent.
2. **DHCP and static addressing:** The NAT Network has DHCP enabled, while Kali Linux is documented with the fixed address `10.0.0.2`. Confirm that the address is reserved or configured in a way that avoids IP conflicts.
