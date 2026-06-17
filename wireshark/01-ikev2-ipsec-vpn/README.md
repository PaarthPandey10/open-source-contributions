# IKEv2 IPsec VPN Handshake Capture

> Bare-metal network engineering lab to capture and contribute a pristine IKEv2 IPsec VPN handshake to the Wireshark Foundation.

---

## Overview

This project documents the engineering, deployment, and troubleshooting of an enterprise-grade network security lab. The objective was to capture the cryptographic negotiation of an IKEv2 Site-to-Site IPsec VPN and merge the `.pcapng` file into the official Wireshark Foundation upstream repository. The lab was built using a bare-metal EVE-NG instance on Windows Hyper-V, running Cisco ASAv firewall nodes bridged to a physical local network.

---

## Key Highlights

- **Infrastructure:** Deployed Cisco ASAv QCOW2 images in EVE-NG, writing native CLI configurations (`crypto ikev2 policy`, `crypto map`) to enforce modern AES-256-GCM authenticated encryption.
- **Pipeline Debugging:** Diagnosed a silent failure in the EVE-NG `wireshark_wrapper.bat` script where `plink.exe` hung in `-batch` mode. Bypassed by manually caching the RSA SSH key via CMD.
- **State Machine Manipulation:** Cleared active IPsec security associations (`clear crypto ikev2 sa`) prior to triggering traffic to successfully capture `IKE_SA_INIT` and `IKE_AUTH` packets instead of missing them to an already-established tunnel.
- **Upstream Integration:** Bypassed a GitLab GUI sync delay using native markdown shortcuts to successfully publish the capture to the master `SampleCaptures` and `IKEv2` protocol pages.

---

## Links

Here are the links to check out the contribution:
* [Wireshark SampleCaptures Wiki Page](https://wiki.wireshark.org/samplecaptures#example-3-site-to-site-ikev2-vpn-with-aes-256-gcm): The original wiki page with my contribution under "IPSec/Example 3: Site-to-Site IKEv2 VPN with AES-256-GCM" section. (Note: You might have to scroll down to the section to see the work)
* [Wireshark IPSec Wiki Page](https://wiki.wireshark.org/ipsec): A related protocol (IPSec) where the .pcapng file is linked under "Example Capture Files" with hypertext "IKEv2 Site-to-Site IPsec VPN". 
* [Wireshark ESP Wiki Page](https://wiki.wireshark.org/esp): A related protocol (ESP) where the .pcapng file is linked under "Example Capture Files" with hypertext "IKEv2 Site-to-Site IPsec VPN". 



---

## Contact

For any questions or feedback, reach out:  
**Paarth Pandey**  
[LinkedIn](https://www.linkedin.com/in/paarth-pandey-13779529b/) | [GitHub](https://github.com/paarthpandey10) | paarthdxb@gmail.com

---

> Author: [Paarth Pandey](https://github.com/paarthpandey10)
>  
> Wireshark Foundation Contribution
