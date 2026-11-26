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
