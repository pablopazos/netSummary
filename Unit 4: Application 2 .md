

# Topic 4: Application Layer Protocols II

This section covers the Domain Name System (DNS) and Peer-to-Peer (P2P) models.

---

## 1. DNS (Domain Name System)

### Introduction
**Purpose**: Translates human-readable machine names (e.g., `www.google.com`) into IP addresses (e.g., `209.85.227.104`).
**Protocol**: Implemented over **UDP (port 53)**, though it can also use TCP.
**Model**: Client-server architecture.
**History**: Replaced the old `hosts` file system, which was non-scalable and prone to inconsistencies.

### DNS Components
**DNS Client (Resolver)**: Each machine has a resolver that sends queries to a local DNS server and provides the answer to applications.
**DNS Server**: Each organization (ISP, University, etc.) has its own server that resolves queries by communicating with a distributed hierarchical database.

### DNS Namespace
**Hierarchical Structure**: Organized as an inverted tree.
    **Root**: Top of the hierarchy.
    **Top-Level Domains (TLDs)**: Includes ccTLDs (.es, .uk) and gTLDs (.com, .org, .edu).
    **FQDN (Fully Qualified Domain Name)**: A complete domain name ending in a dot (e.g., `www.fic.udc.es.`).

### Server Hierarchy
1.  **Root Servers**: 13 critical servers (A-M) that know all TLDs.
2.  **TLD Servers**: Responsible for top-level domains like `.com` or `.es`.
3.  **Authoritative Servers**: Known for hosting the actual IP mappings for a specific domain.

### Operation Types
* **Recursive Query**: The DNS server takes full responsibility for finding the answer, performing all necessary transactions.
* **Iterative Query**: The server returns the best information it has (e.g., a reference to another server) but doesn't perform further queries.
* **DNS Caching**: Servers and clients store resolved mappings for a period (TTL) to reduce network traffic.

### Common DNS Query Types
* **A**: Name to IP mapping.
* **CNAME**: Alias for a name.
* **PTR (Reverse)**: IP to name mapping using the `.arpa` TLD.
* **MX (Mail Exchanger)**: Identifies the SMTP mail server for a domain.

---

## 2. Peer-to-Peer (P2P) Model

### Overview
Unlike the client-server model, P2P consists of **peers** that act as both clients (consuming services) and servers (providing services).

### Key Characteristics
**User-based**: Uses resources (CPU, disk, bandwidth) from user-owned devices rather than central providers.
**Intermittent connectivity**: Peers connect and disconnect frequently.
**Advantages**: Highly fault-tolerant and resource sharing grows as more users join.
**Disadvantages**: Higher security risks and heavy bandwidth usage.

### Examples & Types
**File Distribution**: BitTorrent, Napster.
**VoIP**: Skype.
**CPU Lending**: SETI@Home, BOINC.
**Blockchain**: Bitcoin.

### Classification
* **By Structure**:
  *Structured*: Organized topographies like DHT (Distributed Hash Table).
  *Unstructured*: Peers connect randomly.
* **By Organization**:
    * [cite_start]*Centralized*: Uses a central node for management[cite: 71].
    * [cite_start]*Decentralized*: No central control mechanism[cite: 72].
