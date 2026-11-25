# Lab 12 – Screenshot Evidence Index

This folder documents the curated 10-image evidence package prepared for Lab 12. The downloadable ZIP was supplied separately with the lab update; the archive is not yet committed as a binary file in this repository.

| # | Screenshot | What it demonstrates |
|---:|---|---|
| 01 | `01-sign-in-risk-policy-grant-controls.png` | Sign-in risk policy grant-control configuration using MFA |
| 02 | `02-risk-policy-mfa-control-selection.png` | MFA grant control selected in the risk policy |
| 03 | `03-canada-location-block-policy-grant.png` | Canada-only policy configured to block access |
| 04 | `04-risk-policy-user-scope-and-exclusion.png` | Specific test-user scope and administrator exclusion |
| 05 | `05-sign-in-evaluation-canada-matched-risk-not-matched.png` | Sign-in evaluation showing Canada matched while risk did not match |
| 06 | `06-canada-named-location-country-configuration.png` | Country-based named-location configuration |
| 07 | `07-canada-country-location-method.png` | IP-based country lookup (IPv4 and IPv6) |
| 08 | `08-sign-in-risk-evaluation-none.png` | Sign-in-risk evaluation showing no detected risk |
| 09 | `09-lab-account-access-denied.png` | Lab account received Microsoft's access-denied page |
| 10 | `10-canada-block-policy-enabled.png` | Canada block policy enabled |

## Evidence interpretation

The sign-in log showed the test user's network location as Saskatoon, Canada and marked the network condition **Matched**. The same event showed sign-in risk **None**, so the High sign-in-risk condition was **Not matched**. This explains why the combined Canada + High-risk policy did not apply to that ordinary sign-in.

The separate Canada-only policy was tested and the lab account received an access-denied page. For audit-quality evidence, retain the corresponding sign-in event's Conditional Access details showing the exact Canada-only policy and its Block result.

## Redaction and publication

Before committing image files to this public repository, review them for personal identifiers, tenant IDs, email addresses, IP addresses, and other information that should not be public. Do not publish passwords, tokens, recovery codes, or secrets.
