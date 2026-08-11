# DHCP & ARP

> **Learning Track:** Networking Essentials 
> **Focus:** DHCP, ARP, MAC addresses, and network security implications
> [DHCP](https://tryhackme.com/room/networkingessentials?taskNo=2&sharerId=68025329c716e4bfe75b004f)
> [ARP](https://tryhackme.com/room/networkingessentials?taskNo=3&sharerId=68025329c716e4bfe75b004f)

## Overview

Today, I learnt about **DHCP (Dynamic Host Configuration Protocol)** and **ARP (Address Resolution Protocol)**.

At first glance, both protocols seem like basic networking concepts. But understanding them helped me see something important:

> **Cybersecurity becomes much easier to understand when you understand how the underlying network works.**

DHCP helps devices obtain the network configuration they need, while ARP helps devices discover the MAC address associated with an IPv4 address on a local network.

---

## 1. DHCP — Dynamic Host Configuration Protocol

### What problem does DHCP solve?

Devices on a network need configuration information such as an IP address before they can communicate effectively.

Instead of manually configuring every device, **DHCP automatically provides network configuration to clients**.

This can include:

* IP address
* Subnet mask
* Default gateway
* DNS server information
* Lease duration

### The DORA Process

The DHCP process can be remembered using **DORA**:

| Step  | Meaning        | What happens                                                                |
| ----- | -------------- | --------------------------------------------------------------------------- |
| **D** | Discover       | The client broadcasts a request to locate available DHCP servers.           |
| **O** | Offer          | A DHCP server offers an available IP address and configuration information. |
| **R** | Request        | The client requests the offered configuration.                              |
| **A** | Acknowledgment | The DHCP server confirms the assignment.                                    |

### Simplified flow

```text
Client
   │
   │ DHCP Discover
   ▼
DHCP Server
   │
   │ DHCP Offer
   ▼
Client
   │
   │ DHCP Request
   ▼
DHCP Server
   │
   │ DHCP ACK
   ▼
Client receives network configuration
```

### Why DHCP matters in cybersecurity

Understanding normal DHCP behaviour is useful when investigating network activity.

A malicious or unauthorized DHCP server could potentially provide clients with incorrect network configuration.

This means that something as ordinary as **"How did this device get its IP address?"** can become relevant during a security investigation.

---

# 2. ARP — Address Resolution Protocol

### What problem does ARP solve?

IPv4 communication on a local network requires devices to know the destination's **MAC address**.

But a device may only know the destination's IP address.

ARP helps resolve this:

```text
IPv4 Address
     ↓
    ARP
     ↓
MAC Address
```

For example, suppose my computer wants to communicate with:

```text
192.168.1.10
```

but doesn't know the MAC address associated with that IP.

It can send an ARP request asking:

> Who has 192.168.1.10?

The device using that IP can respond with its MAC address.

The mapping can then be stored in the device's **ARP cache** for future communication.

### Simplified ARP flow

```text
Host A
IP: 192.168.1.5
      │
      │ ARP Request:
      │ "Who has 192.168.1.10?"
      ▼
Local Network
      │
      ▼
Host B
IP: 192.168.1.10
MAC: XX:XX:XX:XX:XX:XX
      │
      │ ARP Reply
      ▼
Host A stores the mapping in its ARP cache
```

---

# 3. The Security Connection

This is where the topic became more interesting to me.

ARP does not have built-in authentication for its messages, which creates opportunities for abuse.

### ARP Spoofing / ARP Poisoning

An attacker can send forged ARP messages to manipulate the IP-to-MAC mappings stored by devices on a local network.

For example, an attacker may attempt to convince:

```text
Victim → "The attacker's MAC belongs to the gateway."
```

If successful, traffic intended for the gateway could potentially be redirected through the attacker.

This can be used as part of a **Man-in-the-Middle (MITM)** attack.

The important lesson for me wasn't just learning that ARP spoofing exists.

It was understanding **why it is possible in the first place**.

I needed to understand normal ARP behaviour before the security implication made sense.

---

# DHCP vs ARP

|                    | DHCP                                 | ARP                                      |
| ------------------ | ------------------------------------ | ---------------------------------------- |
| Full name          | Dynamic Host Configuration Protocol  | Address Resolution Protocol              |
| Main purpose       | Provides network configuration       | Resolves IPv4 addresses to MAC addresses |
| Works with         | Network configuration                | Local network address resolution         |
| Key concept        | IP assignment                        | IP → MAC mapping                         |
| Security relevance | Rogue DHCP / malicious configuration | ARP spoofing / poisoning                 |

---

# What I Learnt

Before this lesson, I could have given a simple definition of both protocols.

Now I have a better understanding of **what problem each protocol solves and how that behaviour connects to security**.

My biggest takeaway:

> **You can't properly secure what you don't understand.**

Networking isn't just a prerequisite I need to complete before getting into "real" cybersecurity.

It *is* part of cybersecurity.

Understanding how devices receive IP addresses, communicate locally, resolve addresses, and move traffic across a network gives me a better foundation for eventually understanding areas like **SOC analysis, network security, incident response, and cloud security**.

---

## Next Steps

For now, I'm moving from simply asking:

> **"What does this protocol do?"**

to asking:

> **"Why does it work this way, and how could this behaviour become a security problem?"**

That's the mindset I'm trying to build.

---

### Resources / Practice

* Personal notes and observations

