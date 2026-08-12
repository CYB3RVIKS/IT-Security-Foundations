# NAT — Network Address Translation

> **Learning Track:** Networking Essentials
> **Focus:** [NAT, private/public IP addresses, and network communication](https://tryhackme.com/room/networkingessentials?taskNo=6&sharerId=68025329c716e4bfe75b004f)

## What is NAT?

**NAT (Network Address Translation)** is a technique used to translate IP addresses as traffic moves between networks.

One common use of NAT is allowing multiple devices on a private network to access the Internet using a **public IP address**.

For example:

```text
Private Network

192.168.1.10 ─┐
192.168.1.11 ─┼──► Router/NAT ───► Internet
192.168.1.12 ─┘
                    │
                    ▼
              Public IP
```

Instead of every device needing its own public IPv4 address, the router can translate private addresses to a public address.

---

## Private vs Public IP Addresses

Private IP addresses are used within private networks.

Common private IPv4 ranges include:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

These addresses are not directly routable across the public Internet.

A public IP address, on the other hand, can be used to communicate across the Internet.

---

## How NAT Works

Suppose my computer has:

```text
Private IP: 192.168.1.10
```

It wants to access a website on the Internet.

The router can translate the source address:

```text
192.168.1.10
      ↓
NAT
      ↓
Public IP address
```

The router keeps track of the connection so that returning traffic can be translated back and delivered to the correct internal device.

---

## NAT and Port Translation

NAT is often used together with **PAT (Port Address Translation)**.

PAT allows multiple internal devices to share a single public IP address by using different source ports to keep connections separate.

This is commonly called:

**NAT overload.**

---

## Why NAT Matters in Cybersecurity

NAT is important when analysing network traffic because the IP address visible externally may not represent the actual internal device that initiated the connection.

Understanding NAT can therefore help when:

* Investigating network traffic
* Analysing logs
* Understanding firewall rules
* Troubleshooting connectivity
* Understanding network architecture
* Investigating incidents involving internal hosts

NAT can also provide a degree of network separation, but it should **not be treated as a replacement for a firewall or a complete security control**.

---

## Key Takeaway

NAT helped me understand another layer of what happens when a device inside a private network communicates with the wider Internet.

What looks like:

```text
My computer → Website
```

can actually involve:

```text
My computer
     ↓
Private network
     ↓
Router
     ↓
NAT/PAT
     ↓
Public network
     ↓
Internet
```

Understanding these layers makes network traffic much less mysterious—and gives me a better foundation for analysing it from a security perspective.
