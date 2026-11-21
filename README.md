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

## Project — Privileged Role Assignment and User Lifecycle Management

Implemented and validated directory role administration, user lifecycle operations, bulk provisioning, and Microsoft Graph PowerShell workflows in the non-production tenant.

| Exercise | Work completed | Evidence / notes |
|---|---|---|
| 1. Create a user and test baseline permissions | Created the Lami test identity, completed first sign-in, and verified standard-user restrictions on application creation. | Screenshots captured. |
| 2. Assign Application Administrator | Assigned the role and verified the application-creation option became available. | Screenshots captured. |
| 3. Remove the role | Removed the role and verified the restriction returned. | Screenshots captured. |
| 4. Bulk import and Microsoft Graph | Bulk-created users using CSV; verified successful creation in audit logs. Installed/verified Microsoft Graph PowerShell, connected with delegated permissions, created Samuel, and verified profile attribute updates. | Screenshots captured. A separate update attempt against directory-synchronised accounts failed as expected because those attributes are mastered on-premises; no changes were made to those accounts. |
| 5. Delete and restore a user | Deleted Lami and restored the account from Deleted users; verified it returned to All users. | Screenshots captured. |
| 6. Assign a Windows Enterprise licence | Tenant licence availability was inspected and licence-selection work was performed during the exercise. The sample user Raul Razo was not present in this tenant, so the lab's exact sample-user validation could not be reproduced. | Do not describe this as a verified Raul Razo assignment. |

**Progress note:** Exercises 1–5 have been validated with screenshots. Exercise 6 is documented as an environment-specific adaptation rather than claiming the original sample-user workflow was completed exactly.

## Project — Microsoft Entra Tenant Configuration and Privacy Controls

Implemented tenant-level domain, organization profile, location metadata, and privacy-notice configuration in the non-production Microsoft 365 / Microsoft Entra tenant.

- Created the sales subdomain through Microsoft 365 admin center. DNS configuration was intentionally skipped, so the domain remains listed as **Incomplete setup**.
- Changed the tenant display name to **Contoso Marketing** and reviewed the technical contact.
- Reviewed the tenant country/region (**Canada**), the displayed primary-copy data location (**United States datacenters**), and located and recorded the Tenant ID.
- Configured the global privacy contact and added the Contoso sample privacy statement URL.
- Verified that the organizational privacy statement opened from **My Account → Data and Privacy → Organization's notice**.

See the [tenant configuration project record](./Module-01-Identity-Management/Lab-02-working-with-tenant-properties/README.md). The six-image redacted evidence package documents the configuration and validation results.

## Project — Group-Based Licensing and Dynamic Membership

Implemented and validated group-based licensing and dynamic membership in the non-production tenant using Microsoft 365 E5 and tenant test identities.

- Assigned Microsoft 365 E5 to security group **sec-001** and verified that Lami's licence assignment path was **Inherited (sec-001)**. Jones's existing E5 assignment was inspected as Direct and left unchanged.
- Created Microsoft 365 group **sec-002** with two assigned members.
- Created all-users dynamic group **dynamic-001**; after membership processing it contained 70 users.
- Tested guest-only and member-only dynamic rules. The guest group contained 2 users and the member group contained 68 users; the counts reconcile to 70.
- Used tenant-specific names: **Lami**, **Microsoft 365 E5**, **sec-001**, **sec-002**, **dynamic-001**, **dynamic guest-001**, and **dynamic member-001**. Licence inheritance was verified directly in Microsoft Entra ID.

See the [project implementation record](./Module-01-Identity-Management/Lab-03-assigning-licenses-using-group-membership/README.md). The 12-image redacted evidence ZIP has been prepared locally; upload and extraction into the project's screenshots folder remain pending, so the project evidence package is **Validated**; repository publication is pending.

## Documentation
- [Architecture](./ARCHITECTURE.md)
- [Progress tracker](./PROGRESS.md)

## Project documentation standard
Each project records its objective, environment, implementation decisions, validation results, evidence, security considerations, and technical findings.

## Status policy
All labs begin as **Planned**. A lab is marked **Completed** only after implementation, validation, and documentation. Creating a folder or reading instructions does not count as completion.

## Security
Use a dedicated non-production environment wherever possible. Never commit passwords, access tokens, client secrets, recovery codes, personal data, or unredacted sensitive tenant information. Redact screenshots before publishing.

Project folders document the actual tenant configuration, implementation decisions, validation evidence, and any limitations.
