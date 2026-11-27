# Lab 11 — Verified Screenshot Evidence

Six screenshots are retained to document the three exercises and the sign-in-log check.

- **01-sway-baseline.png** — Exercise 1: confirms Sway was accessible before the restriction.
- **02-block-access-configuration.png** — Exercise 1: shows the Block access grant control in the Sway policy configuration.
- **03-what-if-inputs.png** — Exercise 2: records the What If evaluation inputs.
- **04-what-if-block-policy-applies.png** — Exercise 2: records the What If result showing the Sway block policy applies.
- **05-sign-in-frequency-policy.png** — Exercise 3: shows the 30-day sign-in frequency session control and Report-only mode.
- **07-sign-in-activity.png** — Supporting verification: shows the sign-in log's Conditional access tab listing the sign-in frequency policy and its result as Disabled.

**Interpretation:** The Disabled result is consistent with a Report-only policy: it is evaluated for reporting but does not enforce the session control. This screenshot demonstrates that the policy is visible in the sign-in record; it does not demonstrate an enforced 30-day reauthentication event.

The draft screenshot `06-sign-in-frequency-settings.png` was excluded because it shows an unfinished policy-creation screen and does not prove the saved 30-day configuration. `08-sign-in-activity-details.png` was excluded because it duplicates the policy listing without adding a clearer result than screenshot 07.
