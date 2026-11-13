# Local Network Discovery Using Zenmap

## Project overview
This project documents a beginner-level local network discovery exercise using Zenmap (the graphical interface for Nmap). The goal was to identify hosts responding on an authorized local LAN.

## Objective
- Identify the local IPv4 address and subnet.
- Run a Zenmap Ping Scan against the local subnet.
- Record responding hosts and the MAC/vendor information reported by Nmap.
- Summarize the results and limitations.

## Tools
- Windows Command Prompt (`ipconfig`)
- Zenmap
- Nmap 7.993

## Local network details
| Field | Value |
|---|---|
| Local IPv4 address | `192.168.1.8` |
| Subnet mask | `255.255.255.0` |
| Default gateway | `192.168.1.1` |
| Scan target | `192.168.1.0/24` |
| Scan type | Ping Scan (`-sn`) |
| Scan date/time | 2026-11-13, 11:51 (+0500) |
| Scan duration | 14.88 seconds |
| Addresses scanned | 256 |
| Hosts reported up | 6 |

## Discovered hosts

> Privacy note: MAC addresses are device identifiers. Before making this repository public, consider replacing full MAC addresses with redacted values, or keep the repository private if your internship requires the full values.

| IP address | MAC address reported | Vendor / note |
|---|---|---|
| `192.168.1.1` | `privacy` | ZTE; hostname `gpon.net` |
| `192.168.1.2` | `privacy` | Unknown |
| `192.168.1.3` | `privacy` | Unknown |
| `192.168.1.6` | `privacy` | Unknown |
| `192.168.1.7` | `privacy` | Samsung Electronics |
| `192.168.1.8` | Not shown in scan output | Local PC IPv4 address |

## Methodology
1. Open Command Prompt and run `ipconfig`.
2. Read the active adapter's IPv4 address and subnet mask.
3. With address `192.168.1.8` and mask `255.255.255.0`, determine the subnet as `192.168.1.0/24`.
4. Open Zenmap, enter `192.168.1.0/24` as the target, and select **Ping scan**.
5. Run the scan and record the hosts and MAC/vendor details shown in the output.

## Nmap command equivalent
```bash
nmap -sn 192.168.1.0/24
```

## Findings and limitations
- Nmap reported six hosts responding to host-discovery probes.
- The gateway's MAC vendor was identified as ZTE.
- One host's MAC vendor was identified as Samsung Electronics.
- Three hosts had unknown vendor labels.
- The local PC (`192.168.1.8`) appeared in the output without a MAC address.
- A Ping Scan is host discovery, not a vulnerability assessment. A host marked **up** responded to discovery probes; it does not mean the host is secure, compromised, or fully characterized.
- MAC vendor identification is not definitive device identification. Unknown devices should be verified with the network owner.

## Conclusion
The Zenmap Ping Scan successfully discovered six responsive hosts on the authorized local `/24` network. This exercise provided hands-on practice with IPv4 addressing, subnetting, host discovery, MAC addresses, and basic Nmap output interpretation.

## Evidence
Add your own screenshots to the `evidence/` folder:
- `ipconfig.png` — show the active adapter's IPv4 address and subnet mask. Hide unrelated private information.
- `zenmap-scan.png` — show the Zenmap target, Ping Scan profile, and results.

## Authorization and safety
Only scan networks you own or have explicit permission to assess. This report describes a local network discovery exercise and does not claim that unknown hosts are malicious.
