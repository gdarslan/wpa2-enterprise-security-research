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
