# Lab 12 – Manage Microsoft Entra Smart Lockout Values

**Module:** Authentication and Access  
**Status:** Implemented – configuration and temporary lockout observed; sign-in log review and repository evidence publication pending

## Objective

Configure Microsoft Entra Smart Lockout and observe how it temporarily blocks sign-in after repeated unsuccessful authentication attempts. Understand the tenant-wide scope of the setting and the operational response to an urgent, legitimate lockout.

## Official instructions

[Open the Microsoft lab instructions](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_12_ManageAzureADSmartLockoutValues.html)

## Environment

- Microsoft Entra tenant: personal lab tenant
- Administrative access: Global Administrator
- Test identity: Lami (cloud-only test account)
- Portal: Microsoft Entra admin center

## Implementation

Navigated to **Entra ID → Authentication methods → Password protection** and reviewed the existing configuration.

The observed configuration was:

| Setting | Value |
|---|---:|
| Lockout threshold | 5 |
| Lockout duration | 120 seconds |
| Mode | Enforced |

The portal also showed **Enforce custom list = Yes** and **Password protection on Windows Server Active Directory = Yes**. These were observed settings; this lab did not change or validate their operation.

Saved the Smart Lockout configuration using the portal's **Save** action.

## Validation

| Test | Expected result | Observed result |
|---|---|---|
| Review tenant Smart Lockout settings | Threshold 5, duration 120 seconds, Enforced mode | Values were visible in the Password protection page |
| Attempt sign-in with repeated incorrect passwords using Lami | Temporary lockout message appears | Microsoft sign-in page displayed: “Your account is temporarily locked to prevent unauthorized use. Try again later.” |
| Access the tenant after the temporary lockout | Access becomes available after the lockout period | A subsequent Azure Portal interactive sign-in for Lami shows Success at 2026-11-24 06:08:07 UTC, after the failed sign-ins shown below |
| Review interactive sign-in events | Failed attempts are followed by a successful sign-in after access is restored | The screenshot shows five visible failed Azure Portal interactive sign-ins between 06:04:54 and 06:05:05 UTC, followed by a Success at 06:08:07 UTC. The event details were not opened, so the exact failure reason and causal link to Smart Lockout are not confirmed |
| Confirm exact trigger count and duration | Logs or controlled timing confirm the precise threshold and timer | Not independently measured; the lockout message and event sequence support the test, but do not prove that exactly five attempts caused the lockout or that the timer lasted precisely 120 seconds |

**Validation limitation:** Smart Lockout uses detection logic, so the observed lockout message alone does not prove that exactly five attempts caused the lockout or that the timer lasted precisely 120 seconds. Do not deliberately repeat failed attempts against administrator or production accounts.

## Troubleshooting and lessons learned

- Smart Lockout is configured at the tenant level; users do not need to be added individually or assigned to a Smart Lockout group.
- The configured threshold and duration are not a guarantee that every account will lock at an identical attempt count. Microsoft applies detection logic to sign-in activity.
- Smart Lockout is distinct from on-premises Active Directory account lockout. Do not assume there is a simple per-user **Unlock account** control that clears the cloud Smart Lockout timer.
- For an urgent legitimate lockout, verify the user's identity through the approved process, inspect Entra sign-in logs, and determine whether activity is suspicious before initiating recovery.
- Do not reduce the tenant-wide lockout duration as an ad hoc response for one user. That changes protection for the tenant and may weaken resistance to password-guessing attacks.
- A password reset is not a guaranteed way to bypass an active Smart Lockout timer. Follow the organization's recovery and incident-response procedures.
- Consider an alternative authorized user or business-continuity process for urgent work while the lockout is investigated.

## Security and operational considerations

- Test with a dedicated non-privileged lab identity.
- Never publish passwords, recovery codes, tokens, or secrets.
- Do not intentionally generate repeated failures against production or privileged accounts.
- Review sign-in logs and escalate suspicious activity according to incident-response procedures.

## Evidence

Capture and upload redacted screenshots showing:
1. Password protection settings with threshold, duration, and mode.
2. The temporary lockout message for the test identity.
3. Subsequent access after the temporary lockout.
4. Entra sign-in events showing the failed attempts and subsequent successful sign-in (reviewed; retain a redacted screenshot in the repository evidence folder).

**Repository evidence status:** Screenshots were shared during the working session, but PNG files have not yet been confirmed in this lab's GitHub `screenshots/` folder. Upload the redacted image files before marking the lab fully completed.

## Completion checklist

- [x] Prerequisites and administrative access checked
- [x] Smart Lockout settings reviewed/configured
- [x] Temporary lockout behaviour observed
- [x] Operational response and security implications documented
- [ ] Redacted screenshot evidence uploaded to GitHub
- [x] Interactive sign-in events reviewed; failed attempts and a subsequent successful sign-in observed
- [ ] Evidence links verified
- [ ] Progress tracker updated to Completed after evidence publication and validation
