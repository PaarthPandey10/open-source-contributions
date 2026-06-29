# Open-Source Contributions & Security Research

> A consolidated repository of my upstream open-source contributions, network engineering labs, and security research.

---

## Table of Contents

- [About](#about)  
- [Project Structure](#project-structure)  
- [Usage / How to Use](#usage--how-to-use)  
- [Features / Highlights](#features--highlights)  
- [Technologies Used](#technologies-used)  
- [Contributing](#contributing)  
- [License](#license)  
- [Contact](#contact)

---

## About

This repository serves as a centralized portfolio of my open-source security engineering and research. It documents my technical process, infrastructure deployments, and the specific hurdles overcome to contribute to upstream security projects. My focus is on network security, cryptography analysis, and bridging the gap between rigorous technical execution and compliance frameworks.

---

## Project Structure
```
open-source-contributions/
├── screenshots/
├── owasp/
│   ├── README.md
│   └── 01-api-security-testing/
│       └── README.md
├── wireshark/
│   ├── README.md
│   ├── 01-ikev2-ipsec-vpn/
│   │   ├── README.md
│   │   ├── 01-ikev2-ipsec-vpn-build-guide.md
│   │   └── ikev2-site-to-site-handshake.pcapng
│   └── 02-isis-p2p-adjacency/
│       ├── README.md
│       ├── 02-isis-p2p-adjacency-build-guide.md
│       └── isis_p2p_adjacency_sync.pcapng
├── LICENSE
└── README.md
```

## Usage / How to Use
Contributions are categorized by the upstream organization or foundation (e.g., Wireshark, OpenSSF). Navigate to the organization folder, then into the specific project directory to review the objective, architecture, challenges, and the final artifacts (e.g., PCAP files, scripts, or configuration files).

## Features / Highlights
* Wireshark Foundation Upstream Contribution: Engineered a bare-metal network lab to capture and publish a pristine IKEv2 IPsec VPN handshake to the official Wireshark Wiki.
* Advanced Infrastructure Bypasses: Diagnosed and bypassed headless Windows pipeline crashes (plink.exe) and native GitLab UI sync delays during deployment and publishing.
* Cryptographic State Manipulation: Manually manipulated Cisco ASA state machines to capture targeted cryptographic negotiation phases (Phase 1 & 2) over standard ESP payloads.

## Technologies Used
* Infrastructure: Hyper-V, Bare-Metal EVE-NG
* Networking: Cisco ASAv, IPsec, IKEv2, AES-256-GCM
* Tools: Wireshark, CMD/PowerShell, VPCS
* Platforms: GitLab, GitHub, Markdown

## Contributing
This is a personal portfolio repository showcasing my individual contributions to other upstream projects. It is currently not open for external contributions.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Contact
Paarth Pandey
[LinkedIn](https://www.linkedin.com/in/paarthpandey/) | [GitHub](https://github.com/PaarthPandey10) | paarthdxb@gmail.com


> Author: Paarth Pandey
>
> Open-Source Contributions Portfolio
