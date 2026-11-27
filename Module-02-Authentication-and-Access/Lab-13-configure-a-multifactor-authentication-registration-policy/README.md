# Lab 13 – Configure a Multifactor Authentication Registration Policy

**Module:** Authentication and Access  
**Status:** In Progress — configuration completed; sign-in log verification pending

## Objective

Configure the Microsoft Entra multifactor authentication (MFA) registration policy, test MFA authentication, and document the configuration and observed results.

## Official instructions

[Open the Microsoft lab instructions](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_15_ConfigureAAD_MultiFactorAuthRegPolicy.html)

## Implementation

### Multifactor authentication registration policy

Configured the **Multifactor authentication registration policy** under **ID Protection** with the following settings:

| Setting | Observed configuration |
|---|---|
| Policy | Multifactor authentication registration policy |
| Included users | All users |
| Excluded users | None shown in the captured configuration |
| Control | Require Microsoft Entra ID multifactor authentication registration |
| Policy enforcement | Enabled |

The policy configuration screenshot shows the registration requirement enabled for all users. This documents the policy scope and enforcement setting; it does not establish that every user has completed registration.

### Conditional Access MFA policy

Also configured a separate Conditional Access policy named **mfa policy**:

| Setting | Observed configuration |
|---|---|
| Users | All users, with specific users excluded |
| Target resources | All resources (formerly all cloud apps) |
| Network | Not configured |
| Conditions | None selected |
| Grant control | Grant access — require multifactor authentication |
| Policy state | Captured first as Report-only, then On |

This is an MFA enforcement policy and is distinct from the MFA registration policy. The captured enabled state is broad in scope. Keep an emergency access account excluded and verify administrative access before enforcing tenant-wide policies.

## Validation performed

### Microsoft Authenticator challenge

Tested sign-in using the account `lami@fikayo.onmicrosoft.com`. The sign-in flow displayed **Approve sign in request** and instructed the user to approve the request in Microsoft Authenticator and enter the displayed number if prompted.

This is evidence that the account was challenged for MFA using Microsoft Authenticator with number matching. The screenshot contains a transient number-matching code; do not publish that code.

### Successful application access

After completing the authentication step, the test account reached its Outlook mailbox. This demonstrates successful access after the authentication flow.

The Outlook landing-page screenshot alone does not prove which control caused the MFA challenge. The Authenticator challenge screenshot is the direct evidence of the MFA step.

### Sign-in log verification

**Pending.** Review the corresponding Entra sign-in event and its **Conditional Access** details to confirm the policy evaluation and result. Add the observed result here after the event is available; do not infer the sign-in log outcome from the Outlook landing page.

## Evidence

Capture and store redacted screenshots in the `screenshots/` subfolder:

- MFA registration policy showing all users included, registration required, and enforcement enabled.
- Conditional Access policy showing the MFA grant control and final policy state.
- Microsoft Authenticator approval challenge (redact transient number-matching codes).
- Successful Outlook access after authentication.
- Entra sign-in event showing the Conditional Access evaluation and result (**pending**).

Do not publish passwords, tokens, recovery codes, transient number-matching codes, or unnecessary personal or tenant identifiers.

## Troubleshooting and lessons learned

- MFA registration and MFA enforcement are separate controls. The registration policy requires users in scope to register; Conditional Access can require MFA during access.
- A user reaching the Authenticator approval screen demonstrates an MFA challenge, while successful Outlook access demonstrates completion of the sign-in flow.
- The sign-in event's Conditional Access details are still required to attribute the MFA requirement to the intended Conditional Access policy.

## Completion checklist

- [x] MFA registration policy configured and enabled for all users
- [x] Conditional Access MFA policy configured
- [x] Microsoft Authenticator MFA challenge observed
- [x] Successful Outlook access after authentication observed
- [ ] Corresponding sign-in log reviewed and Conditional Access result recorded
- [ ] Evidence screenshots uploaded to the repository and redacted
- [ ] Findings documented and final review completed
- [ ] Progress tracker updated
