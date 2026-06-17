# Infrastructure Build Guide: Bare-Metal IKEv2 IPsec VPN

> A visual guide documenting the engineering, deployment, and validation of a bare-metal IKEv2 IPsec VPN handshake.

---

## Overview

This guide provides a comprehensive visual narrative of the IKEv2 IPsec VPN deployment process. It follows the end-to-end engineering workflow, starting from provisioning the bare-metal EVE-NG infrastructure and configuring layer 3 routing, to applying modern cryptographic policies and validating the raw packet sequence using a custom Wireshark pipeline.

---

## Workflow Steps

### 1. Architecture and Topology
The lab environment was constructed on a bare-metal EVE-NG instance hosted within Windows Hyper-V to ensure high performance and isolation. The core network topology consists of two Cisco ASAv firewalls acting as the primary IPsec gateways (designated as FW-London and FW-Dubai). These gateways are separated by a central WAN switch to simulate internet transit, while Virtual PC Simulator (VPCS) nodes sit on the internal trusted subnets to generate the necessary payload traffic.

![](../../screenshots/Screenshot%202026-06-17%20102000.png)

### 2. Node Provisioning and Interface Configuration
The initial configuration phase involved establishing the foundational layer 3 boundaries across the network. We configured the outside, untrusted interfaces connecting to the WAN switch, and the internal, trusted interfaces acting as default gateways for the LANs on both ASAv nodes.

**FW-London Outside Interface Setup:**
![](../../screenshots/Screenshot%202026-06-17%20102500.png)

**FW-Dubai Outside Interface Setup:**
![](../../screenshots/Screenshot%202026-06-17%20103115.png)

Following the firewall setup, the internal VPCS endpoints were provisioned to simulate corporate workstations on both ends of the site-to-site tunnel. Static IP addresses and default gateways were assigned to enable internal routing before the tunnel creation.

**PC-London IP Assignment (192.168.1.0/24):**
![](../../screenshots/Screenshot%202026-06-17%20103322.png)

**PC-Dubai IP Assignment (192.168.2.0/24):**
![](../../screenshots/Screenshot%202026-06-17%20103414.png)

### 3. Routing and Base Connectivity
Before applying any complex cryptographic maps, standard layer 3 reachability across the simulated WAN had to be strictly verified. We configured static default routes pointing to the WAN interfaces and executed a targeted ping sweep from FW-London to FW-Dubai to confirm end-to-end gateway visibility.

**Routing Verification and Interface Stats:**
![](../../screenshots/Screenshot%202026-06-17%20102846.png)

**Gateway-to-Gateway ICMP Success:**
![](../../screenshots/Screenshot%202026-06-17%20103544.png)

### 4. Cryptographic Engineering (IKEv2 and AES-256-GCM)
This phase focused on enforcing modern, enterprise-grade security standards. We deployed comprehensive IKEv2 policies utilizing AES-256-GCM authenticated encryption and SHA-256 for pseudo-random functions. Legacy ESP integrity hashes were explicitly disabled and ignored by the ASAv configurations, as the GCM cipher suite inherently provides built-in authenticated encryption without redundant overhead.

**FW-London Crypto Map and Tunnel Group:**
![](../../screenshots/Screenshot%202026-06-17%20110902.png)

**FW-Dubai Crypto Map and Tunnel Group:**
![](../../screenshots/Screenshot%202026-06-17%20111353.png)

### 5. The Packet Capture Pipeline
With the cryptographic maps securely applied to the outside transit interfaces, we initiated the native EVE-NG Wireshark integration hook to monitor the wire. We applied the specific display filter `isakmp || esp || icmp` to strip out background ARP and CDP noise, perfectly isolating the negotiation phases.

**Listening on the Wire:**
![](../../screenshots/Screenshot%202026-06-17%20111454.png)

To force the tunnel state to transition from down to up, we generated "interesting traffic" by pinging the PC-Dubai endpoint from PC-London. The first ICMP echo request predictably drops (shows as timeout) while the ASAv buffers the packet to initiate the initial IKEv2 handshake. Once the security associations (SAs) are successfully negotiated, the subsequent ICMP packets flow securely through the encrypted ESP tunnel.

**Triggering the Tunnel:**
![](../../screenshots/Screenshot%202026-06-17%20111616.png)

### 6. The Upstream Artifact: Pristine IKEv2 Handshake
The final result of the lab is visual proof of the capture. It demonstrates a flawless, zero-noise packet capture of the `IKE_SA_INIT` and `IKE_AUTH` cryptographic negotiations, immediately followed by the secure ICMP payload stream completely encapsulated in ESP. This is the exact raw `.pcapng` sequence that was verified and committed upstream to the official Wireshark Foundation repository.

![](../../screenshots/Screenshot%202026-06-17%20113815.png)

---

## Contact

![](../../screenshots/Pasted%20image%2020260617155839.png)

For any questions or feedback, reach out:  
**Paarth Pandey** [LinkedIn](https://www.linkedin.com/in/paarth-pandey-13779529b/) | [GitHub](https://github.com/paarthpandey10) | paarthdxb@gmail.com

---

> Author: [Paarth Pandey](https://github.com/paarthpandey10)
>  
> Wireshark Foundation Contribution