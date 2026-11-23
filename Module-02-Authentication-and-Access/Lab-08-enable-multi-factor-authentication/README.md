# Lab 08 – Enable Multi-Factor Authentication (MFA)

**Module:** Authentication and Access  
**Status:** Completed (adapted implementation)  
**Test identity:** Lami — `lami@fikayo.onmicrosoft.com`  
**Authentication method observed:** Microsoft Authenticator push notification with number matching  
**Application validated:** Outlook on the web

## Objective
Review Microsoft Entra MFA configuration, inspect existing Conditional Access and per-user MFA enforcement, and validate an MFA-protected Microsoft 365 sign-in.

[Official Microsoft SC-300 Lab 08 instructions](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_08_EnableAzureADMultiFactorAuthentication.html)

## Implementation and observations

### 1. Legacy MFA service settings
Reviewed the per-user MFA **Service settings** page.

Observed:
- App passwords were allowed.
- The federated-intranet MFA bypass checkbox was not selected.
- No trusted IP subnet was entered.
- The page indicated that legacy verification options had migrated to Authentication methods.

No service settings were changed.

### 2. Existing Conditional Access policy
Inspected the pre-existing policy named **MFA for all users**.

Observed:
- State: On.
- Users: All users, with one excluded identity.
- Target resources: All resources.
- Grant requirement: Require multifactor authentication.
- Network: Not configured.

This policy pre-existed the exercise. It was inspected, not newly created. The separate policy in the original Microsoft exercise (`MFA_for_Delia`) was not created because the tenant already had a broader MFA policy and the exercise was adapted to avoid duplicating or changing live security controls.

### 3. Per-user MFA
Inspected the legacy per-user MFA Users page. The selected test identity, Lami, showed **Enforced** before sign-in testing. The status was not changed.

### 4. Authentication validation
Signed in as Lami and observed:
1. Microsoft sign-in displayed an **Approve sign in request** prompt.
2. The prompt instructed the user to open Microsoft Authenticator and enter the displayed number if requested.
3. The sign-in was approved in Authenticator.
4. Outlook on the web loaded for Lami.

**Result:** Successful MFA-protected sign-in and Outlook access.

The test demonstrates that an MFA challenge occurred and that access followed successful approval. Because both per-user MFA and Conditional Access MFA were present, this test does not isolate which enforcement mechanism independently caused the prompt.

## Key IAM findings
- Per-user MFA and Conditional Access are distinct enforcement mechanisms.
- Disabling per-user MFA does not disable an applicable Conditional Access requirement.
- Excluding a user from one Conditional Access policy does not exclude them from other applicable policies or security controls.
- Number matching adds a user-verification step to Authenticator push approval.
- Existing tenant security controls should be inspected before creating duplicate policies or changing enforcement.

## Adaptations and limitations
- Used Lami instead of the sample identities Delia Dennis and Adele Vance.
- Reviewed the existing organization-wide Conditional Access policy instead of creating `MFA_for_Delia`.
- Inspected Lami's existing per-user MFA status instead of changing it.
- The sign-in test was performed in the existing tenant configuration; it did not independently attribute the prompt to one of the overlapping MFA mechanisms.

## Evidence
See the [screenshots](screenshots/README.md) folder for the redacted evidence set.

## Completion checklist
- [x] Reviewed legacy MFA service settings
- [x] Inspected existing Conditional Access MFA policy
- [x] Inspected test user's per-user MFA status
- [x] Triggered and completed Authenticator number-matching challenge
- [x] Verified successful Outlook access
- [x] Documented adaptations, observations, and limitations
- [x] Captured and redacted screenshots
