# Lab 05 – Add Guest Users to the Directory

**Module:** Identity Management  
**Status:** Completed — implementation, guest redemption, troubleshooting, and selected redacted evidence published  
**Environment:** Non-production Microsoft Entra ID tenant

## Objective

Add external users to the directory as guests using the Microsoft Entra admin center, a CSV bulk invitation, and Microsoft Graph PowerShell. Verify invitation processing and guest redemption.

## Official instructions

[Microsoft SC-300 Lab 05 – Add Guest Users to the Directory](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_05_AddGuestUsersToTheDirectory.html)

## Prerequisites and tools

- Access to the Microsoft Entra admin center with permission to invite guest users.
- PowerShell 7.2 or later.
- Microsoft Graph PowerShell SDK.
- Delegated Microsoft Graph permission: `User.ReadWrite.All`.
- External email accounts for invitation and redemption testing.

Observed environment:
- PowerShell **7.6.10**
- Microsoft.Graph PowerShell module **2.40.0**
- Microsoft Graph connection using delegated authentication.

## Implementation

### Exercise 1 — Invite an individual guest

1. Opened **Entra ID → Users → All users → New user → Invite external user**.
2. Entered the external email address and display name **fikayooo**.
3. Kept **User type** set to **Guest**.
4. Used the invitation message to explain the collaboration invitation and retained the My Applications redirect destination.
5. Submitted the invitation.

**Observed result:** The Entra admin center displayed **Successfully invited user** for **fikayooo**. A corresponding **Invite external user** success event was visible in the directory audit log.

### Exercise 2, Task 1 — Bulk invite guests using CSV

1. Downloaded the Entra bulk-invitation CSV template.
2. Retained the template's column headings and populated two guest entries with external email addresses and display names **Emmanuel** and **Samuel**.
3. Used the same redirect URL for both entries: `https://myapplications.microsoft.com/`.
4. Set the invitation-message option to `TRUE` and supplied a customized invitation message.
5. Uploaded the CSV and submitted the bulk operation.

**Observed result:** The directory audit log showed successful **Invite external user** events for **Emmanuel** and **Samuel**. The two guest invitations were processed successfully.

### Exercise 2, Task 2 — Invite a guest with Microsoft Graph PowerShell

1. Confirmed PowerShell version **7.6.10**.
2. Installed and verified Microsoft.Graph PowerShell module **2.40.0**.
3. Connected using:

~~~powershell
Connect-MgGraph -Scopes "User.ReadWrite.All"
~~~

4. Verified the delegated context with `Get-MgContext` and confirmed `User.ReadWrite.All` was present in the granted scopes.
5. Imported the invitation cmdlets:

~~~powershell
Import-Module Microsoft.Graph.Identity.SignIns
~~~

6. Prepared the invitation parameters using the external identity and the My Applications redirect URL:

~~~powershell
$params = @{
    invitedUserEmailAddress = "oyedokun6416@saskpolytech.ca"
    inviteRedirectUrl = "https://myapplications.microsoft.com/"
}
~~~

7. Submitted the invitation:

~~~powershell
New-MgInvitation -BodyParameter $params
~~~

**Observed result:** Microsoft Graph returned an invitation ID and an invitation redemption URL. The invitation email was received at the external mailbox.

## Validation results

| Test | Expected result | Observed result |
|---|---|---|
| Individual invitation | Guest invitation is created | **Pass** — Entra displayed successful invitation for fikayooo |
| Individual invitation audit | Invitation operation recorded | **Pass** — audit log showed Invite external user success |
| Bulk CSV invitation | Multiple guest invitations are submitted | **Pass** — audit log showed successful invitations for Emmanuel and Samuel |
| Graph PowerShell installation | Microsoft.Graph module is available | **Pass** — version 2.40.0 verified |
| Graph authentication | Delegated connection established | **Pass** — Get-MgContext returned the signed-in tenant account |
| Graph permission | User.ReadWrite.All is granted | **Pass** — scope confirmed in context |
| Graph invitation | Invitation created through New-MgInvitation | **Pass** — invitation ID and redemption URL returned |
| Invitation email delivery | External mailbox receives invitation | **Pass** — invitation email received |
| Guest redemption | External user accepts invitation | **Pass** — invitation state shown as Accepted |
| Guest directory object | Account is represented as a guest | **Pass** — account overview showed User type Guest and Creation type Invitation |

## Guest redemption verification

The PowerShell-created guest opened the invitation email and accepted the invitation. The Entra user overview subsequently showed:

- **User type:** Guest
- **Creation type:** Invitation
- **Invitation state:** Accepted
- **Account enabled:** Yes
- **External identity:** Federated sign-in identifier shown in the account's sign-in identifiers.

This validates the invitation and redemption lifecycle for the PowerShell-created guest. The other two invitation methods were validated through successful invitation events; redemption of those two bulk invitations is not claimed.

## Security and evidence handling

- Invitation redemption URLs are sensitive and must not be published.
- Do not commit access tokens, passwords, full personal email addresses, or unnecessary tenant identifiers.
- Redact email addresses, tenant identifiers, browser profile information, and other personal or tenant-sensitive details in screenshots before publication.
- The invitation email screenshot demonstrates delivery; the user overview screenshot demonstrates guest type and accepted invitation state.

## Troubleshooting and lessons learned

- The PowerShell session was running version 7.6.10, satisfying the lab's 7.2 minimum.
- Microsoft.Graph module installation was verified before authentication.
- The first typed verification command used incorrect casing/spacing (`get -Mgcontext`) and failed because PowerShell interpreted `get` as a separate command. The corrected command, `Get-MgContext`, worked.
- The Graph context already included `User.ReadWrite.All`, so a new connection was not required.
- Defining `$params` does not submit an invitation. The invitation is created only when `New-MgInvitation -BodyParameter $params` is executed.
- Invitation creation, email delivery, and redemption are separate validation stages and are documented separately.

## Completion checklist

- [x] Prerequisites and PowerShell version checked
- [x] Individual guest invitation submitted
- [x] Bulk CSV invitations submitted
- [x] Microsoft Graph PowerShell module installed and verified
- [x] Microsoft Graph delegated authentication verified
- [x] User.ReadWrite.All scope confirmed
- [x] Graph invitation submitted successfully
- [x] Invitation email delivery verified
- [x] Guest redemption verified
- [x] Guest user type and accepted invitation state verified
- [x] Implementation and validation documented
- [x] Selected redacted screenshots organized and published in the repository
- [x] Final repository evidence review completed

## Evidence

Created a `screenshots/` folder and published redacted evidence for:
1. Successful individual guest invitation notification.
2. Audit log entries for the individual and bulk guest invitations.
3. CSV template populated with redacted email addresses.
4. Bulk operation success result.
5. PowerShell version and Microsoft.Graph module version.
6. Microsoft Graph connection context and granted `User.ReadWrite.All` scope, with account and tenant identifiers redacted.
7. New-MgInvitation result with the redemption URL fully removed or obscured.
8. Invitation email with personal email addresses and actionable links redacted.
9. Guest account overview showing User type Guest and Invitation state Accepted.

The lab is **Completed**. The repository contains the implementation record, validation results, troubleshooting notes, and selected redacted screenshot evidence.
