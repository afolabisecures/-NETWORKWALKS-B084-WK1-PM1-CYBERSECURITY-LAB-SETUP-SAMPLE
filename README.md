# NetworkWalks | Cybersecurity Lab Setup

**Week 1 — Practical Module 1**  
**Project:** Setting up an isolated virtual lab for penetration testing and ethical hacking

---

## Table of Contents

- [Introduction](#introduction)
- [Project Objectives](#project-objectives)
- [What the Lab Is Used For](#what-the-lab-is-used-for)
- [Lab Architecture](#lab-architecture)
- [Lab Configuration](#lab-configuration)
- [Setup Process](#setup-process)
- [Key Lessons](#key-lessons)
- [Tools and Resources](#tools-and-resources)

## Introduction

For this project, I set up a virtual cybersecurity lab using **Oracle VirtualBox** and **Kali Linux**.

The aim was to build a safe, controlled space where I can practise cybersecurity tasks such as network discovery, port scanning, reconnaissance, and vulnerability testing.

The lab runs on a private virtual network. This makes it possible to add more virtual machines in the future and use them as practice targets.

## Project Objectives

The goals of this exercise were to:

- Install and set up VirtualBox.
- Import Kali Linux as a virtual machine.
- Create a private NAT Network for the lab.
- Connect Kali Linux to the virtual network.
- Configure a consistent IP address for the Kali VM.
- Test network access and DNS resolution.
- Create a snapshot that can be used to restore the VM.
- Record the setup and prepare the lab for future exercises.

## What the Lab Is Used For

This environment is intended for safe cybersecurity practice and authorised testing.

Some of the activities it can support include:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet inspection and analysis
- Web application security testing
- Exploitation practice
- Testing and learning security tools

## Lab Architecture

The diagram below shows the general layout of the virtual lab.

![Cybersecurity lab architecture](https://github.com/user-attachments/assets/403726b2-f6e0-46f3-9fbd-4a5b59d37551)

## Lab Configuration

| Component | Configuration |
|---|---|
| Host operating system | Windows 10 |
| Host memory | 12 GB RAM |
| Processor | Intel Core i5 |
| Virtualisation software | VirtualBox 7.2 |
| Guest operating system | Kali Linux 2026.2 |
| Kali Linux memory (summary) | 6,161 MB |
| Virtual network type | NAT Network |
| Network address | `10.0.0.0/24` |
| Kali Linux IP address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS server | `8.8.8.8` |
| Planned address range for future VMs | `10.0.0.3–10.0.0.99` |

## Setup Process

### Step 1: Install 7-Zip

I installed **7-Zip** to extract the Kali Linux virtual machine files. These files may be provided in `.7z` archive format.

**Tool:** [7-Zip](https://7-zip.org/download.html)

### Step 2: Install VirtualBox

I installed **VirtualBox** to create and manage the virtual machines used in the lab.

**Download:** [VirtualBox](https://virtualbox.org/wiki/Downloads)

### Step 3: Create a NAT Network

I created a separate NAT Network in VirtualBox for the lab.

The network settings were:

| Setting | Value |
|---|---|
| Network name | `NatNetwork` |
| IPv4 prefix | `10.0.0.0/24` |
| DHCP | Enabled |
| IPv6 | Disabled |

![VirtualBox NAT Network configuration](https://github.com/user-attachments/assets/6a2cfeee-1fc4-4167-a634-57d552b05839)

I chose a NAT Network because virtual machines connected to the same NAT Network can communicate with each other while still having outbound network access.

This setup will also make it possible for future attacker and target machines to communicate inside the lab.

### Step 4: Import Kali Linux

I downloaded Kali Linux from its official website and imported the virtual machine into VirtualBox.

I configured its first network adapter with these settings:

| Adapter setting | Value |
|---|---|
| Adapter | Adapter 1 |
| Connection type | NAT Network |
| Network name | `NatNetwork` |
| Adapter type | Intel PRO/1000 MT Desktop (82540EM) |

**Memory recorded during import:** 6,161 MB

![Kali Linux shared-folder configuration](https://github.com/user-attachments/assets/1e5719f8-a876-47c6-bad8-78f88e5e9c53)

I also set up a shared folder so that files could be transferred between Windows and the Kali Linux virtual machine.

### Step 5: Configure the Kali Linux Network

I checked the network settings in Kali Linux and configured the VM to use a consistent IPv4 address.

The recorded network details are:

| Setting | Value |
|---|---|
| IP address | `10.0.0.2` |
| Subnet mask | `255.255.255.0` |
| Default gateway | `10.0.0.1` |
| DNS server | `8.8.8.8` |

Keeping a consistent IP address makes it easier to identify the Kali VM and use it in later lab exercises.

![Kali Linux IP configuration](https://github.com/user-attachments/assets/095a99d9-738e-4143-8a08-34bedab57480)

## Key Lessons

This exercise helped me understand how to build a virtual environment for cybersecurity practice. The main things I learned were:

### 1. NAT and NAT Network

I learned that VirtualBox's NAT and NAT Network modes are not the same.

A NAT Network allows connected virtual machines to communicate with one another. It also provides network address translation for outbound connectivity. This makes it useful when building a lab with more than one virtual machine.

### 2. Virtual Machine Networking

I learned how virtual network adapters connect VMs to a network and how their settings affect communication between machines.

### 3. Static IP Addressing

I practised working with IPv4 addresses, subnet masks, gateways, and DNS settings in Kali Linux. A consistent IP address also makes it easier to manage and document the lab.

### 4. Virtual Machine Snapshots

I learned why it is useful to create a clean snapshot before carrying out experiments that may affect a VM.

A snapshot provides a restore point, allowing the machine to return to a known working state if a later exercise causes problems.

### 5. Technical Documentation

I learned the importance of keeping clear records of commands, settings, screenshots, issues, and solutions. Good documentation makes technical work easier to review, repeat, and troubleshoot.

## Tools and Resources

- [7-Zip](https://7-zip.org/download.html) — Extracting archived files
- [Oracle VirtualBox](https://virtualbox.org/wiki/Downloads) — Running and managing virtual machines
- [Kali Linux](https://kali.org/get-kali) — Security-focused Linux distribution

## Profile

[Connect with me on LinkedIn](https://www.linkedin.com/in/emmanuel-afolabi-59a9b9289/)

---

> **Security reminder:** Use this lab only to practise on systems you own or have clear permission to test. Do not use its tools against unauthorised systems.


