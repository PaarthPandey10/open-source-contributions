# IS-IS Level-2 Point-to-Point Adjacency Capture

> Bare-metal network engineering lab to capture and contribute a pristine IS-IS protocol database synchronization sequence to the Wireshark Foundation.

---

## Overview

This project documents the engineering, deployment, and execution of a localized routing protocol lab. The objective was to capture a completely noise-free IS-IS Level-2 routing adjacency—specifically stripping out broadcast LAN Multi-Access noise—and merge the `.pcapng` file into the official Wireshark Foundation upstream repository. The lab was built using a bare-metal EVE-NG hypervisor running Cisco IOL (IOS on Linux) routing nodes.

---

## Key Highlights

- **Infrastructure:** Deployed lightweight Cisco IOL routing images within EVE-NG, mapping virtual serial and ethernet interfaces to simulate a direct wide-area link.
- **License Emulation:** Bypassed Cisco IOL binary restrictions by executing a Python keygen script within the EVE-NG CLI to generate a host-mapped `iourc` license file.
- **Broadcast Suppression:** Explicitly engineered the links with `isis network point-to-point` to suppress Designated Intermediate System (DIS) elections, isolating the pure `P2P HELLO` (IIH) and database exchange sequence.
- **State Machine Manipulation:** Executed a dynamic protocol reset (`clear isis *`) with Wireshark pre-listening on the wire to perfectly trap the complete Link State PDU (LSP) and Sequence Number PDU (CSNP/PSNP) synchronization.
- **Upstream Integration:** Formatted and published the final `.pcapng` capture to the master `SampleCaptures` (Routing Protocols) and native `IS-IS` protocol pages on the Wireshark Wiki.

---

## Links

Here are the links to check out the contribution:
* [Wireshark SampleCaptures Wiki Page](https://wiki.wireshark.org/SampleCaptures#routing-protocols): The original wiki page with my contribution under the "Routing Protocols" section.
* [Wireshark IS-IS Protocol Page](https://wiki.wireshark.org/IS-IS): A related protocol page where the .pcapng file is linked under "Example traffic" as an isolated IS-IS Level-2 Point-to-Point adjacency synchronization.

---

## Contact

For any questions or feedback, reach out:  
**Paarth Pandey**  
[LinkedIn](https://www.linkedin.com/in/paarth-pandey-13779529b/) | [GitHub](https://github.com/paarthpandey10) | paarthdxb@gmail.com

---

> Author: [Paarth Pandey](https://github.com/paarthpandey10)
>  
> Wireshark Foundation Contribution
