# Implementation and test evidence

## Authentication architecture

| Component | Implemented role |
| --- | --- |
| Windows host | Virtualization workstation |
| Oracle VirtualBox | Linux FreeRADIUS VM |
| TP-Link C39 | WPA2-Enterprise authenticator |
| iPhone 12 Pro | PEAP supplicant |
| VMware Workstation / Kali Linux | Controlled wireless test system |
| Netgear USB Wi-Fi adapters | Wireless test interfaces |

FreeRADIUS was configured with a laboratory CA, server certificate and test identities. The access point forwarded authentication exchanges to the RADIUS server. The client established a TLS tunnel with the legitimate server before completing inner MSCHAPv2 authentication.

## Baseline validation

The report records Access-Request and Access-Challenge messages followed by a successful Access-Accept. The iPhone established the TLS tunnel and obtained an IP address. This established that the legitimate environment worked before adversarial testing.

## Security assessment

| Test | Evidence recorded in the final report | Interpretation |
| --- | --- | --- |
| Legitimate authentication | Successful RADIUS log and client connectivity | Authentication baseline functional |
| Deauthentication | Client disconnected and reconnected after the test stopped | Availability disruption observed; not a confidentiality breach |
| Rogue AP / certificate mismatch | Connection attempt terminated when the unexpected certificate was presented | Server trust checks protected inner authentication in this configuration |
| Outer identity observation | Test username was visible | Identity privacy remains an issue |
| Inner credential observation | No password or MSCHAPv2 response was captured | No demonstrated password compromise |

The report attributes rejection to the client's previously established trust relationship. The experiment did not independently verify every internal iOS trust mechanism, so the observation is reported without asserting universal certificate pinning or platform behavior.

The original project used FreeRADIUS debugging, hostapd-wpe and Aircrack-ng tools; specific attack parameters, credentials and capture files are not published.

## Troubleshooting and professional reflection

- Rebuilt FreeRADIUS after conflicting configuration changes made the environment difficult to maintain.
- Investigated access-point reachability, shared-secret configuration and addressing issues.
- Restored management connectivity after an accidental lockout.
- Used authentication logs to distinguish connectivity, certificate and authentication failures.

The project demonstrated the value of maintaining a reproducible configuration, validating dependencies individually and documenting both positive and negative results.
