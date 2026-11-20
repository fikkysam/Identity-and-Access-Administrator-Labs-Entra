# Microsoft Entra ID – Identity and Access Administrator Labs

A practical portfolio of 28 Microsoft SC-300-aligned labs covering identity management, authentication and access management, application access, and identity governance.

> This repository is dedicated to the 28-lab collection and is independent of the separate Conditional Access policy portfolio.

## Learning objectives
- Administer Microsoft Entra identities, directory roles, tenant settings, guests, and hybrid identity.
- Configure authentication, MFA, SSPR, Conditional Access, risk-based access, and privileged access.
- Manage enterprise application access, app registrations, and consent.
- Implement identity governance, access reviews, lifecycle controls, monitoring, and security posture management.

## Lab modules

| Module | Focus | Labs |
|---|---|---:|
| [01 – Identity Management](./Module-01-Identity-Management/) | Roles, tenant properties, licensing, collaboration, guests, federation, hybrid identity | 01–07 |
| [02 – Authentication and Access](./Module-02-Authentication-and-Access/) | MFA, SSPR, VM authentication, PIM, smart lockout, Conditional Access, risk, managed identities | 08–16 |
| [03 – Application Access](./Module-03-Application-Access/) | Defender for Cloud Apps, app registration, application access and consent | 17–21 |
| [04 – Identity Governance](./Module-04-Identity-Governance/) | Entitlement management, Terms of Use, lifecycle, access reviews, PIM, Sentinel, Secure Score | 22–28 |

## Lab 01 progress — Manage User Roles

The first lab has been worked through using dedicated test identities in the non-production tenant.

| Exercise | Work completed | Evidence / notes |
|---|---|---|
| 1. Create a user and test baseline permissions | Created the Lami test identity, completed first sign-in, and verified standard-user restrictions on application creation. | Screenshots captured. |
| 2. Assign Application Administrator | Assigned the role and verified the application-creation option became available. | Screenshots captured. |
| 3. Remove the role | Removed the role and verified the restriction returned. | Screenshots captured. |
| 4. Bulk import and Microsoft Graph | Bulk-created users using CSV; verified successful creation in audit logs. Installed/verified Microsoft Graph PowerShell, connected with delegated permissions, created Samuel, and verified profile attribute updates. | Screenshots captured. A separate update attempt against directory-synchronised accounts failed as expected because those attributes are mastered on-premises; no changes were made to those accounts. |
| 5. Delete and restore a user | Deleted Lami and restored the account from Deleted users; verified it returned to All users. | Screenshots captured. |
| 6. Assign a Windows Enterprise licence | Tenant licence availability was inspected and licence-selection work was performed during the exercise. The sample user Raul Razo was not present in this tenant, so the lab's exact sample-user validation could not be reproduced. | Do not describe this as a verified Raul Razo assignment. |

**Progress note:** Exercises 1–5 have been validated with screenshots. Exercise 6 is documented as an environment-specific adaptation rather than claiming the original sample-user workflow was completed exactly.

**Security note:** Screenshots and CSV evidence must be reviewed and redacted before public publication. Do not upload source CSV files containing initial passwords, screenshots showing passwords, tokens, or other secrets.

## Documentation
- [Architecture](./ARCHITECTURE.md)
- [Progress tracker](./PROGRESS.md)

## Lab documentation standard
Each lab records its objective, prerequisites and licensing, implementation, configuration rationale, validation, evidence, troubleshooting, and lessons learned.

## Status policy
All labs begin as **Planned**. A lab is marked **Completed** only after implementation, validation, and documentation. Creating a folder or reading instructions does not count as completion.

## Security
Use a dedicated non-production environment wherever possible. Never commit passwords, access tokens, client secrets, recovery codes, personal data, or unredacted sensitive tenant information. Redact screenshots before publishing.

Each lab folder links to its corresponding Microsoft Learning instruction page.