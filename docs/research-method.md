# Research scope and methodology

## Background and research question

Enterprise wireless networks rely on centralized authentication rather than a shared Wi-Fi password. Their security depends in part on correct trust and certificate configuration. A rogue access point may impersonate a network, but a matching network name does not by itself establish trust in its authentication server.

The main research question was whether password material could be obtained from an 802.1X network in an isolated, controlled environment.

Supporting questions:

- How does enterprise authentication differ from a shared-password network?
- How does server certificate validation affect rogue access point resistance?
- How can the behavior of the authentication flow be observed safely?
- What practical measures reduce the identified risks?

## Method

The project combined literature research, laboratory implementation, observation and testing. The original plan was revised as equipment and the research scope evolved. The final setup used a virtualized Linux FreeRADIUS server, TP-Link C39 access point, Kali Linux and an iPhone 12 Pro rather than assuming the proposed Wi-Fi Pineapple, Raspberry Pi or additional client platforms had been deployed.

The baseline was verified before security scenarios were evaluated. RADIUS logs, connection behavior and documentation were used to compare the legitimate authentication flow with the controlled test outcomes.

## Rules of engagement

The original report describes tests limited to personally owned laboratory equipment, low-power wireless testing and no collection of third-party data. Production systems, credential reuse, social engineering against real users and cryptographic cracking were outside the final test scope.

## Provenance

This public summary is derived from the original project plan revisions, final PRP report, research presentation and architecture drawing. The final report takes precedence where the initial plan differs from implemented equipment or results.

## Research design and evaluation criteria

| Research activity | Evaluation question | Evidence |
| --- | --- | --- |
| Literature study | What distinguishes personal and enterprise wireless authentication? | Protocol and architecture discussion in final report |
| Prototype | Can a functional enterprise Wi-Fi environment be built with available hardware? | Lab topology, configuration notes and baseline authentication |
| Controlled test | Can availability be disrupted without compromising credentials? | Client disconnection and reconnection |
| Controlled test | Does the client accept an impersonating authentication server? | Certificate rejection and observed authentication exchange |
| Analysis | What residual risks are present? | Distinction between outer identity, inner credentials and service availability |
| Reflection | What would improve the next experiment? | Cross-platform testing and reproducible configuration |

The project used an iterative applied-research approach: investigate the technology, build a working environment, observe its behavior, test specific security questions and reflect on what the evidence supports. This explains why the final hardware and method differed from the earlier plan. It avoids presenting the planned tests as completed work.

## Threat model

The assessed asset was the enterprise network's authentication boundary and the test user's identity/password material. The scenario assumed a nearby wireless adversary capable of impersonating the network and disrupting client association. The legitimate RADIUS server, access point and previously configured client were the reference system. The test did not assume compromise of the legitimate server, possession of its private key, or physical access to the client.

The principal security questions covered identity confidentiality and network availability. User acceptance of misleading trust prompts, new-device onboarding and compromised PKI were recognized as additional scenarios but were not independently evaluated.

## Validity

The established baseline makes the comparison more meaningful: the client could authenticate before the rogue-server test. Nevertheless, the study is qualitative and explores one environment. It does not supply a sample size sufficient to estimate a general attack success probability, and no statistical comparison across client operating systems was conducted.
