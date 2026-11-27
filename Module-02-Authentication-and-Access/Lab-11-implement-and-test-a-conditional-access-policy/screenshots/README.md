# Lab 11 — Screenshot Evidence

Six screenshots are retained to document the three exercises and the sign-in-log verification.

| Screenshot | Evidence |
|---|---|
| **01-sway-baseline.png** | Exercise 1 — Confirms that Sway was accessible before the Conditional Access restriction was applied. |
| **02-block-access-configuration.png** | Exercise 1 — Shows the Conditional Access policy configured with the **Block access** grant control for Sway. |
| **03-what-if-inputs.png** | Exercise 2 — Records the user and resource inputs used for the What If evaluation. |
| **04-what-if-block-policy-applies.png** | Exercise 2 — Shows the What If evaluation result identifying the Sway block policy as applicable. |
| **05-sign-in-frequency-policy.png** | Exercise 3 — Shows the saved sign-in frequency policy with a **30-day** session control and **Report-only** mode. |
| **06-sign-in-activity.png** | Supporting verification — Shows the sign-in log's **Conditional access** tab listing the sign-in frequency policy and its result as **Disabled**. |

## Interpretation and limitations

The **Disabled** result in the sign-in log is consistent with the policy being in **Report-only** mode: the policy is evaluated for reporting, but its session control is not enforced. The screenshot confirms that the policy is visible in the sign-in record; it does not demonstrate that a 30-day reauthentication event was enforced.

## Excluded captures

- **06-sign-in-frequency-settings.png** — Excluded because it shows an unfinished policy-creation screen rather than the saved policy. The saved policy and its 30-day session control are demonstrated in screenshot 05.
- **08-sign-in-activity-details.png** — Excluded because it is a broad policy listing and does not add distinct evidence beyond the focused Conditional access view in screenshot 07.

The original screenshots are preserved separately. This folder's evidence set contains only the six selected screenshots listed above.
