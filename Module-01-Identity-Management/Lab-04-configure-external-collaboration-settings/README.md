# Project – Microsoft Entra External Collaboration and Guest Access Configuration

**Project area:** Microsoft Entra ID identity and access management  
**Implementation status:** Implemented and configuration state verified; redacted screenshot archive prepared locally; repository image upload pending  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Objective

Configure organization-wide external collaboration controls for guest identities. The implementation establishes a restrictive guest directory-visibility boundary while allowing approved internal users and designated administrators to invite external collaborators.

This record describes the configuration actually applied and observed in the tenant. It is not a reproduction of the Microsoft sample exercise.

## Configuration summary

| Control | Implemented setting | Security purpose |
|---|---|---|
| Guest user access | **Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)** | Limits guest directory visibility to the guest's own directory object and prevents browsing other users, groups, and group memberships. |
| Guest invitation permissions | **Member users and users assigned to specific admin roles can invite guest users, including guests with member permissions** | Allows ordinary member users and designated administrative roles to invite guests while preventing unrestricted guest-invitation capability across the organization. |
| Guest self-service sign-up via user flows | **Yes** | Enables the tenant-level guest self-service sign-up capability for applicable user flows. This toggle alone does not demonstrate that a particular user flow has been created or published. |
| Email one-time passcode for guests | **Yes** | Allows guests without an existing Microsoft Entra or Microsoft account to authenticate using a passcode delivered to their email address. |
| Collaboration restrictions | **Allow invitations to be sent to any domain (most inclusive)** | Preserves the default domain policy specified for this exercise. No domain allowlist or denylist was configured. |

## Implementation

### 1. Guest self-service sign-up

Enabled **Enable guest self-service sign-up via user flows** in the external collaboration settings.

**Observed state:** The control displayed **Yes**.

### 2. Guest directory access

Selected the most restrictive guest access option:

> Guest user access is restricted to properties and memberships of their own directory objects (most restrictive).

**Observed state:** The third guest-access option was selected. This limits guest visibility into the directory; it does not by itself define permissions to every application or resource. Resource access still depends on the permissions and policies assigned to those resources.

### 3. Guest invitation permissions

Selected:

> Member users and users assigned to specific admin roles can invite guest users including guests with member permissions.

**Observed state:** The second guest-invitation option was selected. This is more restrictive than allowing anyone in the organization to invite guests, while not limiting invitations exclusively to administrators.

### 4. Email one-time passcode

Opened **External Identities → All identity providers → Email one-time passcode** and verified the guest email one-time passcode control.

**Observed state:** **Yes** was selected and the provider list showed **Configured**.

### 5. Collaboration restrictions

Reviewed the domain restriction options and retained the default:

> Allow invitations to be sent to any domain (most inclusive).

**Observed state:** The allow-any-domain option was selected. This is the configured outcome for this exercise, not a recommendation that every production organization should use an unrestricted domain policy.

## Validation results

| Validation | Expected state | Observed result |
|---|---|---|
| Guest access restriction | Most restrictive option selected | **Pass** – third guest-access option selected |
| Guest invitation permissions | Member users and designated admin roles can invite | **Pass** – second invitation option selected |
| Guest self-service sign-up | Enabled | **Pass** – Yes |
| Email one-time passcode | Enabled for guests | **Pass** – Yes; provider displayed Configured |
| Collaboration domain restriction | Default allow-any-domain option retained | **Pass** – allow invitations to any domain selected |
| Pending changes | No unsaved configuration changes remain | **Pass** – Save control was disabled when reviewed |

**Validation boundary:** These checks verify the tenant configuration shown in the Entra admin center. A live external invitation, guest redemption, user-flow execution, and guest sign-in were not performed as part of this implementation record. No end-to-end authentication outcome is claimed.

## Evidence

The redacted evidence package contains four screenshots:

1. Guest directory access, invitation permissions, and self-service sign-up.
2. Built-in identity provider overview showing Email one-time passcode as Configured.
3. Email one-time passcode explicitly set to Yes.
4. Collaboration restrictions showing the default allow-any-domain option.

The signed-in administrator identity and tenant/directory breadcrumb were obscured in the screenshots prepared for publication.

**Local evidence archive:** `Lab-04-Redacted-Screenshot-Evidence.zip`  
**Repository status:** Screenshot descriptions are documented in [screenshots/README.md](./screenshots/README.md). The PNG files are prepared in the local archive but have not yet been committed to this repository.

## Security considerations

- The most restrictive guest directory-access option reduces directory reconnaissance and limits exposure of other users' and groups' directory information.
- Restricting who can invite guests reduces the number of identities that can initiate external collaboration.
- Email one-time passcode provides an authentication method for eligible external users who do not have an existing Microsoft Entra or Microsoft account. It should not be treated as a substitute for evaluating the assurance requirements of sensitive applications.
- Guest self-service sign-up should be paired with appropriately designed and scoped user flows, application assignment, and access governance. Enabling the tenant toggle does not itself prove those controls exist.
- The allow-any-domain setting permits invitations to any email domain. A production organization may instead use an approved-domain allowlist based on business requirements, while also considering cross-tenant access settings and the separate SharePoint/OneDrive external-sharing controls.
- Guest directory visibility settings do not automatically grant or revoke access to individual enterprise applications, SharePoint sites, Teams, or other resources.

## Technical observations

- The Entra admin center indicates that the Email one-time passcode configuration has moved from the External Collaboration Settings page to **All identity providers**.
- The guest-access, invitation, and self-service controls were visible together in External Collaboration Settings.
- The Save button was disabled after the final review, indicating no pending unsaved changes on that page.
- The identity provider showed **Configured**, and the detailed provider pane showed **Yes**.

## Implementation checklist

- [x] Guest self-service sign-up enabled
- [x] Most restrictive guest directory access selected
- [x] Guest invitation permissions configured for members and designated admin roles
- [x] Email one-time passcode enabled and verified
- [x] Default collaboration domain restriction reviewed and retained
- [x] Configuration state reviewed in the Entra admin center
- [x] Screenshot evidence captured and redacted
- [x] Implementation details, validation boundaries, and security implications documented
- [ ] Redacted PNG evidence uploaded into the repository screenshots folder
- [ ] Final repository evidence review completed

## Official reference

[Microsoft SC-300 – Configure External Collaboration Settings](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_04_ConfigureExternalCollaborationSettings.html)
