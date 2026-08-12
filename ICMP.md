# ICMP — Internet Control Message Protocol

> **Learning Track:** Networking Essentials
> **Focus:** [ICMP, network diagnostics, and security implications](https://tryhackme.com/room/networkingessentials?taskNo=4&sharerId=68025329c716e4bfe75b004f)

## What is ICMP?

**ICMP (Internet Control Message Protocol)** is a network-layer protocol used by network devices to communicate information about network conditions.

Unlike TCP and UDP, ICMP is **not used to transport application data**.

Instead, it is primarily used for **error reporting, diagnostics, and network control information**.

A common example is the `ping` command.

---

## ICMP and Ping

When I use:

```bash
ping 8.8.8.8
```

my computer sends an **ICMP Echo Request** to the destination.

If the destination responds, it sends an **ICMP Echo Reply**.

Simplified:

```text
Host
  │
  │ ICMP Echo Request
  ▼
Destination
  │
  │ ICMP Echo Reply
  ▼
Host
```

This allows me to determine whether a host is reachable and can also provide information about round-trip time.

---

## Common ICMP Message Types

Some important ICMP messages include:

| Message                 | Purpose                                        |
| ----------------------- | ---------------------------------------------- |
| Echo Request            | Used to test connectivity                      |
| Echo Reply              | Response to an Echo Request                    |
| Destination Unreachable | Indicates that a destination cannot be reached |
| Time Exceeded           | Indicates that a packet's TTL expired          |

---

## Why ICMP Matters in Cybersecurity

ICMP is useful for legitimate network troubleshooting, but attackers can also abuse it.

For example:

* ICMP can be used during **network reconnaissance**
* Attackers can use ICMP to identify potentially reachable hosts
* ICMP can be abused for certain denial-of-service attacks
* ICMP traffic can sometimes be used as a covert communication channel

This doesn't mean ICMP traffic is inherently malicious.

The important skill is being able to distinguish **expected behaviour from suspicious behaviour**.

---

## Key Takeaway

Before learning this, I mostly associated ICMP with `ping`.

Now I understand that ICMP is part of how network devices communicate information about connectivity and network conditions.

For cybersecurity, that makes understanding normal ICMP traffic important when analysing network activity.
