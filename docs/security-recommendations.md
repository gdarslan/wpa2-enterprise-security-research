# Security recommendations

| Priority | Recommendation | Rationale |
| --- | --- | --- |
| High | Enforce approved CA and expected authentication-server identity through managed client profiles | Reduce rogue-server trust risk |
| High | Prefer mutual certificate-based EAP authentication (EAP-TLS) where practical | Reduce dependence on password-based inner authentication |
| High | Review outer-identity privacy and supported anonymous identity configuration | Reduce exposure of real usernames where supported |
| Medium | Review protected management frame settings and client compatibility | Improve resilience against spoofed management-frame disruption |
| Medium | Maintain certificate issuing, renewal and revocation processes | Avoid expired certificates and insecure workarounds |
| Medium | Monitor RADIUS and wireless infrastructure logs | Identify unusual failures and association patterns |
| Medium | Train users not to accept unexpected certificate prompts | Reduce reliance on ad hoc trust decisions |
| Medium | Periodically revalidate the configuration in an authorized lab | Detect configuration drift |

## Limitations

Only one client type (iPhone 12 Pro) was assessed. It had already connected to the legitimate network. No first-use enrollment scenario, Windows/Android comparison, EAP-TLS implementation or comprehensive management-frame protection comparison was documented. These are recommendations or future research, not completed experiments.

The results do not establish that password material can never be compromised in an enterprise wireless network. They establish that it was not captured under the recorded conditions. A username was observed and service availability was interrupted.

## Next steps

Version-control sanitized deployment configurations, extend the client compatibility matrix, compare managed certificate-validation profiles, and repeat resilience checks against a documented baseline.

## Translating findings into enterprise controls

- **Client provisioning:** configure expected server trust centrally before employees connect. Document onboarding and certificate renewal so users are not asked to make unplanned trust decisions.
- **Authentication policy:** assess EAP-TLS feasibility, certificate provisioning, endpoint compatibility and revocation requirements. The research used PEAP/MSCHAPv2; EAP-TLS is a recommendation rather than a deployed feature.
- **Identity privacy:** test whether anonymous outer identities are supported by the relevant clients and authentication infrastructure. Preserve the ability to apply authorization and audit policy after protected authentication.
- **Availability:** separately test management-frame protection and wireless resilience. The observed disassociation should not be confused with radio-frequency jamming; management-frame defenses do not remove every availability risk.
- **Monitoring:** correlate authentication failures, certificate-related errors and wireless events where telemetry permits. A nearby rogue AP may not send requests to the legitimate RADIUS server, so server logs alone cannot establish full visibility.
- **Change management:** record known-good configuration, certificate ownership, client profiles, controlled regression tests and rollback procedures.

## Proposed follow-up validation matrix (not executed)

| Candidate test | Expected security outcome | Evidence to collect |
| --- | --- | --- |
| Managed client with approved server identity | Legitimate authentication succeeds | Client state and RADIUS result |
| Managed client encountering unapproved server identity | Inner authentication is not released | Certificate error and absence of inner exchange |
| New client onboarding | Approved trust established without accepting unexpected prompts | Enrollment workflow and validation result |
| Alternative client platforms | Behavior documented per platform/configuration | Comparative test records |
| Anonymous outer identity | Real identity not exposed at outer layer where supported | Sanitized protocol observation |
| Management-frame protection | Resistance evaluated for supported devices | Association and disconnection records |

These tests are proposed to broaden the evidence, not claims of completed implementation.
