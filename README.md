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

- Used **Lami** to validate baseline permissions, Application Administrator assignment, elevated application-creation access, role removal, and restoration of the original restriction.
- Completed bulk CSV user provisioning after correcting a UPN-domain issue; verified user-add events in Microsoft Entra audit logs.
- Installed and authenticated Microsoft Graph PowerShell, queried users, created **Samuel Adeyemi**, and updated and verified profile attributes.
- Investigated the source-of-authority restriction on directory-synchronized user attributes; no synchronized accounts were modified.
- Deleted and restored Lami, confirming the account returned to All users.
- Reviewed the Windows Enterprise E3 licence-selection workflow. A completed licence assignment is not claimed.

See the [project implementation record](./Module-01-Identity-Management/Lab-01-Manage-User-Roles/README.md) and [project evidence guide](./Module-01-Identity-Management/Lab-01-Manage-User-Roles/screenshots/README.md).

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
- Published all 12 redacted screenshots with an evidence index in the lab's screenshots folder.

See the [completed Lab 03 implementation record](./Module-01-Identity-Management/Lab-03-assigning-licenses-using-group-membership/README.md) and [12-screenshot evidence index](./Module-01-Identity-Management/Lab-03-assigning-licenses-using-group-membership/screenshots/README.md). The evidence documents Entra configuration and membership results; separate Office web-app sign-in testing is not claimed.

## Project — External Collaboration and Guest Access Configuration

Configured Microsoft Entra external collaboration controls in the non-production tenant.

- Restricted guest directory visibility to each guest's own directory object properties and memberships.
- Allowed member users and users assigned to designated administrator roles to invite guests.
- Enabled guest self-service sign-up via user flows.
- Enabled Email one-time passcode for guests and verified the provider's detailed setting.
- Reviewed collaboration restrictions and retained the exercise's default allow-any-domain setting.

The configuration state was verified in the Entra admin center, and four redacted screenshots have been published in the Lab 04 screenshots folder. Validation covers the tenant configuration shown in the portal; a live external invitation, guest redemption, user-flow execution, and guest sign-in were not performed.

See the [Lab 04 implementation record](./Module-01-Identity-Management/Lab-04-configure-external-collaboration-settings/README.md) and [screenshot evidence index](./Module-01-Identity-Management/Lab-04-configure-external-collaboration-settings/screenshots/README.md).

## Project — Add Guest Users to the Directory

Implemented guest onboarding through three Microsoft Entra invitation methods:

- Invited an individual guest through the Entra admin center and confirmed the successful invitation notification.
- Submitted two guest invitations using the bulk CSV workflow and verified successful invitation events in the directory audit log.
- Installed Microsoft.Graph PowerShell **2.40.0**, authenticated with delegated permissions, confirmed `User.ReadWrite.All`, and created another invitation using `New-MgInvitation`.
- Verified delivery of the PowerShell invitation email and accepted the invitation from the external account.
- Confirmed the resulting directory object had **User type: Guest**, **Creation type: Invitation**, **Invitation state: Accepted**, and **Account enabled: Yes**.

See the [Lab 05 implementation record](./Module-01-Identity-Management/Lab-05-add-guest-users-to-the-directory/README.md). The implementation and guest redemption are validated; redacted screenshot evidence still needs to be published before the lab is counted as completed.

## Documentation
- [Architecture](./ARCHITECTURE.md)
- [Progress tracker](./PROGRESS.md)

## Project documentation standard
Each project records its objective, environment, implementation decisions, validation results, evidence, security considerations, and technical findings.

## Status policy
All labs begin as **Planned**. A lab is marked **Completed** only after implementation, validation, documentation, and evidence publication. Creating a folder or reading instructions does not count as completion.

## Security
Use a dedicated non-production environment wherever possible. Never commit passwords, access tokens, client secrets, recovery codes, personal data, or unredacted sensitive tenant information. Redact screenshots before publishing.

Project folders document the actual tenant configuration, implementation decisions, validation evidence, and any limitations.
