# Lab 11 – Implement and Test a Conditional Access Policy

**Module:** Authentication and Access  
**Status:** Completed  
**Source exercise:** Microsoft SC-300, official exercise titled Lab 13. This repository numbers it Lab 11.

## Objective

Implement and validate a Conditional Access policy that blocks a selected user from Microsoft Sway, evaluate policy applicability with What If, and configure a 30-day sign-in frequency session control in Report-only mode.

## Official instructions

[Microsoft Learn – Implement and Test a Conditional Access Policy](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_13_ImplementAndTestAConditionalAccessPolicy.html)

## Environment and adaptation

- Microsoft Entra admin center in a non-production lab tenant.
- DebraB was used for the Sway access test and the Sway-blocking policy.
- **Lami** was used for the sign-in frequency policy because the Grady Archie test account was not available in this tenant. This is a documented account substitution; it does not change the 30-day session-control configuration.
- The sign-in frequency policy was left in **Report-only** mode, as required by the exercise.

## Exercise 1 – Block Sway for DebraB

### Implementation

1. Signed in to Office.com as DebraB and verified that Sway was accessible before applying the policy.
2. Created a Conditional Access policy targeting DebraB and the Sway cloud app.
3. Configured the Grant control to **Block access**.
4. Enabled the policy to test the access restriction.
5. After validation, turned the policy **Off** to avoid leaving the test account blocked.

### Validation

- Baseline Sway access was confirmed before the policy test.
- The policy configuration shows the Sway resource and **Block access** grant control.
- The policy was subsequently disabled after the test.

## Exercise 2 – Evaluate Conditional Access with What If

Configured What If with:
- **Identity type:** Users
- **User:** DebraB
- **Target resource type:** Cloud apps
- **Target resource:** Sway
- **Device platform:** Windows
- **Client app:** Browser

The evaluation listed the Sway blocking policy under **Policies that will apply**, with the **Block access** grant control. The test policy was later disabled, so a subsequent evaluation can correctly show it as not applying.

## Exercise 3 – Configure sign-in frequency

Created a separate Conditional Access policy with these settings:

| Setting | Configuration |
|---|---|
| Policy name | Sign in frequency |
| Included user | Lami |
| Target resource | Office 365 |
| Session control | Sign-in frequency |
| Frequency | 30 days |
| Policy state | Report-only |

**Account adaptation:** The Microsoft exercise names Grady Archie. That account was not present in the lab tenant, so Lami was selected instead. The configured user is visibly shown in the policy details.

### Validation and interpretation

- The policy configuration shows Lami as the included user, Office 365 as the target resource, and a 30-day sign-in frequency.
- The policy is set to **Report-only**. It evaluates sign-ins but does not enforce a reauthentication interval.
- Sign-in log details were reviewed. A report-only result is evaluated in the **Report-only** tab of the sign-in event details; the ordinary Conditional Access tab may show the policy as disabled/not applied for enforcement. Do not interpret that alone as proof that the Report-only evaluation failed.

## Evidence

See the [screenshots evidence index](./screenshots/README.md) for the required screenshots for all three exercises.

## Key findings

- Conditional Access policies evaluate the combined identity, target-resource, and sign-in context.
- What If is useful for checking whether a policy matches a simulated sign-in before relying on a live sign-in test.
- Report-only mode is suitable for observing the expected effect of a policy without enforcing it.
- The 30-day sign-in frequency is a session control, not a grant control.
- Test policies should be disabled after validation when they are not intended to remain active.

## Completion checklist

- [x] Baseline Sway access verified for DebraB
- [x] Sway blocking policy configured and tested
- [x] Sway policy disabled after testing
- [x] What If evaluation completed for DebraB, Sway, Windows, and Browser
- [x] 30-day sign-in frequency configured for Lami and Office 365
- [x] Sign-in frequency policy set to Report-only
- [x] Account substitution documented
- [x] Evidence index prepared

**Final status: Completed.**
