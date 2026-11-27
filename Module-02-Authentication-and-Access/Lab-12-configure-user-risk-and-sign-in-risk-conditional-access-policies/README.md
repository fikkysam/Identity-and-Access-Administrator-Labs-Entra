# Lab 12 – Configure User Risk and Sign-in Risk Conditional Access Policies

**Module:** 02 – Authentication and Access  
**Status:** In Progress — policies configured; validation against a genuine high-risk event is pending  
**Environment:** Non-production Microsoft Entra tenant

## Objective

Configure Conditional Access policies that respond to user risk and sign-in risk, understand how Entra evaluates risk signals, and validate the behaviour using sign-in logs. A separate Canada location-based block policy was also configured to demonstrate geographic Conditional Access independently of risk detection.

## Official instructions

[Microsoft SC-300 lab – Enable sign-in risk policy](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_14_EnableSignRiskPolicy.html)

## Concepts learned

### User risk

**User risk** estimates the likelihood that an identity's account has been compromised. It is an account-level risk assessment, based on signals associated with the user identity. It can remain relevant across sign-ins until the risk is remediated or dismissed.

Examples of signals that can contribute to user risk include leaked credentials and suspicious activity associated with the account.

### Sign-in risk

**Sign-in risk** estimates the likelihood that a particular authentication attempt is not legitimate. It is specific to a sign-in event and is based on real-time detections associated with that session.

A user can have no user risk while a particular sign-in is risky, or a user can have elevated user risk even when an individual sign-in is not classified as risky.

### The distinction

| Signal | What it assesses | Scope |
|---|---|---|
| User risk | Likelihood that the account/identity is compromised | User account |
| Sign-in risk | Likelihood that this particular sign-in is compromised | Individual sign-in event |

A normal sign-in from Canada does **not** automatically become high-risk. Location and risk are separate signals. If a policy requires both Canada and High sign-in risk, both conditions must match for that policy to apply.

## Implementation

### 1. User-risk policy

Created a Conditional Access policy named **user high risk**.

- User scope: all users, with the administrator account excluded.
- Target resources: all resources.
- Risk condition: High user risk.
- Grant control selected: Require multifactor authentication.
- Policy was configured for evaluation in the tenant.

The portal displayed a constraint when attempting to use **Require risk remediation**: it is only available when the policy targets **All resources**, requires MFA or an authentication strength, and requires the Session control **Sign-in frequency – Every time**. Because that control combination did not fit the alternative configuration being used, the implementation proceeded with the MFA grant control instead.

### 2. Sign-in-risk policy

Created **Sign-in Risk – High Risk**.

- User scope: all users, with the administrator account excluded.
- Target resources: all resources.
- Sign-in risk condition: High.
- Grant control: Require multifactor authentication.
- Policy mode: Report-only during initial evaluation.

The risk condition is evaluated for each sign-in. A sign-in with risk level **None** does not satisfy a High sign-in-risk condition.

### 3. Canada named location and combined risk policy

Created the named location **block-canada-lab** using the country/region configuration:

- Country lookup method: Determine location by IP address (IPv4 and IPv6).
- Country selected: Canada.

Created **sign in high risk-canada**:

- Lab account included; administrator account excluded.
- All resources targeted.
- Canada named location included.
- High sign-in risk selected.
- Grant control: Block access.
- Policy state: On.

This policy is an AND-condition demonstration: the account/resource assignment, Canada location, and High sign-in risk condition must all match.

### 4. Separate Canada-only block policy

To validate geographic blocking independently from risk detection, created **block sign in -canada**:

- Lab account included; administrator account excluded.
- All resources targeted.
- **block-canada-lab** selected under Network.
- Grant: Block access.
- Policy state: On.

This separate policy does not depend on a High risk signal. It demonstrates that a sign-in from a configured Canadian location can be blocked regardless of whether Entra detects sign-in risk.

## Validation and observed results

### Sign-in log evaluation for Lami

A sign-in to Microsoft Graph was inspected in **Sign-in logs → Conditional Access Policy details**.

| Evaluation item | Observed result |
|---|---|
| User | Matched |
| Resource (Microsoft Graph) | Matched |
| Network/location | Matched – Saskatoon, Canada |
| Sign-in risk | None – Not matched |

**Interpretation:** The Canadian location matched. The High sign-in-risk condition did not, because Entra recorded the sign-in risk as **None**. Therefore, the combined **sign in high risk-canada** policy did not apply to that event. This is expected policy evaluation, not evidence that the named location is broken.

### Canada-only block test

A sign-in attempt by the lab account from the Canadian test environment displayed Microsoft's **“You cannot access this right now”** page. The page stated that authentication succeeded but the account did not meet the access requirements for the resource.

This is consistent with the Canada-only block policy. For a complete audit trail, the corresponding failed sign-in event should also be opened and its Conditional Access tab checked to confirm the exact policy name and Block result.

### High-risk validation limitation

No genuine High sign-in-risk event was generated during this exercise. The logs showed **Sign-in risk: None**. Consequently, the High-risk policies were configured and their evaluation logic was inspected, but enforcement against an actual High-risk event was **not** demonstrated.

Do not create artificial risky activity against the everyday administrator account just to force a test result. Use a dedicated test identity and an approved test scenario if a genuine risk event becomes available.

## Troubleshooting and problems encountered

1. **The risk policies initially seemed absent from sign-in logs.**  
   After opening the Conditional Access details for the relevant sign-in, the policies appeared with a result such as **Not applied**. A policy can be listed even when its conditions do not match; the result is an evaluation outcome, not a missing policy.

2. **Sign-in frequency – Every time appeared selected and could not be changed.**  
   This occurred while attempting to use the **Require risk remediation** grant control. The portal warning explained that risk remediation has specific prerequisites, including the Session control **Sign-in frequency – Every time**. The implementation used the MFA grant-control alternative instead.

3. **Canada was initially treated as though it needed a manually entered IP address.**  
   The correct configuration for this exercise was a **Countries location** using IP-based country lookup (IPv4 and IPv6), with Canada selected. No single personal IP address was needed.

4. **The combined Canada + High sign-in-risk policy did not apply to an ordinary sign-in.**  
   The sign-in log showed the network matched Canada but sign-in risk was None. Since the policy requires both conditions, it correctly did not apply. A separate Canada-only block policy was created to demonstrate location enforcement without depending on risk detection.

5. **A test sign-in was denied.**  
   The lab account received Microsoft's access-denied page after the Canada-only policy was enabled. The matching sign-in log's Conditional Access details should be retained as the definitive policy-attribution evidence.

## Key takeaways

- User risk and sign-in risk are related but not interchangeable: one assesses the account, the other assesses a particular sign-in.
- Conditional Access combines configured conditions. When multiple conditions are configured, each must match for the policy to apply.
- A sign-in from Canada is not automatically high-risk.
- **Not applied** is a meaningful evaluation result. Inspect the individual condition results to find out why.
- Country-based named locations use Entra's IP geolocation; they are not configured by entering one Canadian IP address.
- Report-only mode is useful for observing policy impact before enforcement.
- Excluding the administrator account from test policies reduces the risk of accidental administrative lockout.

## Evidence

The curated evidence package contains 10 screenshots covering policy configuration, risk and location evaluation, the Canada named location, and the lab-account access-denied result.

- [Screenshots evidence index](./screenshots/README.md)
- Downloadable archive: `Lab-12-Risk-Based-Conditional-Access-Evidence.zip` (provided separately with this update).

Screenshots should be redacted before any public upload. Do not publish passwords, tokens, recovery codes, or unnecessary personal/tenant identifiers.

## Completion checklist

- [x] User-risk policy configured
- [x] High sign-in-risk policy configured
- [x] Administrator account excluded from the test policies
- [x] Canada named location configured using IP-based country lookup
- [x] Separate Canada-only block policy configured and test sign-in denied
- [x] Sign-in log conditions inspected and interpreted
- [x] Troubleshooting and lessons learned documented
- [x] Curated screenshot evidence package prepared
