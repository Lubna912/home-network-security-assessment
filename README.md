# Home Network Security Assessment

A hands-on network security operations exercise performed on a real home
network — covering router configuration review, SSH connectivity testing,
and live traffic analysis with Wireshark.

**Course:** CYB 444 – Computer Network Operations Security

## Overview

This project applies network security operations concepts to a real,
live environment (a home network) rather than a simulated lab. Sensitive
identifying details (network name, public IP address, device MAC
addresses) have been blurred in the screenshots for privacy.

## Task 1: Home Router Configuration Analysis

Reviewed the router's admin panel to assess its security posture:

- **Wireless settings** – WPA2-PSK authentication with AES encryption on
  both 2.4GHz and 5GHz bands; WEP and WPS disabled (both are weaker/legacy
  protocols).
- **DHCP configuration** – Reviewed the IP range handed out to connected
  devices.
- **Firewall / DoS protection** – Confirmed protections enabled: ICMP
  Echo Protection, Ping Sweep Protection, Smurf Protection, SYN Flood
  Cookie Protection, and WinNuke Protection.
- **Connected devices** – Reviewed the DHCP lease table to identify
  active devices on the network.

## Task 2: SSH Connectivity Exploration

Attempted to connect to the router via SSH from PowerShell:

```
ssh admin@<router-ip>
```

- The first attempt failed because the router only offered a legacy
  `ssh-rsa` host key type that the client rejected by default.
- Retried with explicit algorithm flags to allow `ssh-rsa`, after which
  the connection reached the router and prompted for a password —
  confirming the SSH service was reachable on port 22.
- Authentication ultimately failed (`Permission denied`), showing the
  connection succeeded at the network level but credentials were not
  accepted.

## Task 3: Network Monitoring with Wireshark

Captured live traffic on the Wi-Fi interface to observe real network
communication:

- Observed TCP, TLS, and HTTP packets in real time.
- Reviewed source/destination addresses, protocols, and packet details.
- Demonstrated how packet capture tools can be used to monitor and
  understand network activity.

## Files

- `fig1_router_status.png` – Router status overview
- `fig2_wireless_basic.png` – Wireless 2.4GHz basic settings
- `fig3_security_2ghz.png` – Wireless 2.4GHz security settings
- `fig4_security_5ghz.png` – Wireless 5GHz security settings
- `fig5_dhcp_settings.png` – DHCP configuration
- `fig7_dhcp_leases.png` – Connected devices / DHCP leases
- `fig8_ssh_attempt.png` – SSH connection attempt via PowerShell
- `fig9_wireshark.png` – Wireshark packet capture

## Author

Lubna Alamri

