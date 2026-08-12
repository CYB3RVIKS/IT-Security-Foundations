# Routing & Routing Protocols

> **Focus:** [Routing, routers, routing tables, and routing protocols](https://tryhackme.com/room/networkingessentials?taskNo=5&sharerId=68025329c716e4bfe75b004f)

## What is Routing?

**Routing** is the process of determining how packets move from a source network to a destination network.

When a device wants to communicate with a destination outside its local network, the packet is typically forwarded to a **router**, which determines where the packet should go next.

A simplified example:

```text
Source
  │
  ▼
Router A
  │
  ▼
Router B
  │
  ▼
Destination
```

The packet may pass through several routers before reaching its destination.

---

## Routing Tables

Routers use **routing tables** to determine where packets should be forwarded.

A routing table can contain information such as:

* Destination network
* Next hop
* Interface
* Route metric

A simplified routing decision looks like:

```text
Destination IP
      ↓
Check routing table
      ↓
Find best matching route
      ↓
Forward packet
```

The router doesn't necessarily know the entire journey of the packet.

It mainly needs to determine the **next appropriate hop**.

---

# Routing Protocols

Routers can learn routes through different methods.

### Static Routing

A network administrator manually configures the route.

**Advantages:**

* Predictable
* Simple for small networks
* No routing protocol overhead

**Disadvantages:**

* Doesn't automatically adapt to network changes
* Becomes difficult to maintain in large networks

---

### Dynamic Routing

Routers use routing protocols to automatically learn and update routes.

Some routing protocols include:

* **RIP**
* **OSPF**
* **EIGRP**
* **BGP**

These protocols use different methods to determine and exchange routing information.

---

## OSPF

**OSPF (Open Shortest Path First)** is a dynamic routing protocol commonly used within an organization's network.

It is a **link-state routing protocol** and uses the **Shortest Path First (SPF)** algorithm to calculate paths.

---

## BGP

**BGP (Border Gateway Protocol)** is used to exchange routing information between different autonomous systems on the Internet.

It plays a major role in determining how traffic can travel between large networks across the Internet.

---

## EIGRP

**EIGRP (Enhanced Interior Gateway Routing Protocol)** A Cisco proprietary routing protocol that combines aspects of different routing algorithms together.

Allows different networks (like Internet Service Protocols) to exchange routing information and establish paths for data to travel between these networks.

---

## RIP

**RIP (Routing Information Protocol)** Routers running RIP share information about the networks they can reach and the number of hops (routers) required to get there.

---

## Why Routing Matters in Cybersecurity

Routing determines where network traffic goes.

That makes routing knowledge relevant to:

* Network monitoring
* Traffic analysis
* Network segmentation
* Incident response
* Firewall configuration
* Detecting unusual traffic paths
* Understanding network attacks

If I don't understand how traffic normally moves through a network, it becomes much harder to recognise when something unusual is happening.

---
