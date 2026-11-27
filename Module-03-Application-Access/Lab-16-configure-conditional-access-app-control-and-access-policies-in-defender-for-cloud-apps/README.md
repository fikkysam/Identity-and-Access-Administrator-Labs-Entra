# Lab 16 – Configure Conditional Access App Control and Access Policies in Defender for Cloud Apps

**Module:** Application Access  
**Status:** Configuration and activity-log validation completed

## Objective

Configure Microsoft Entra Conditional Access App Control for Microsoft Forms, route the selected user's browser session through Microsoft Defender for Cloud Apps in **Monitor only** mode, and create a Defender for Cloud Apps access policy that monitors Microsoft Forms activity and generates alerts.

## Implementation

. Used the tenant account **Lami** in place of the Microsoft lab's sample account **Pradeep Gupta**.

. Confirmed that Lami could access Microsoft Forms before applying the monitoring configuration.

. Created the Microsoft Entra Conditional Access policy **Monitor Lami using Forms**.

. Scoped the policy to the Lami user account and the **Microsoft Forms** cloud application.

. Configured **Use Conditional Access App Control** with the mode set to **Monitor only**, and enabled the policy.

. Signed in to Microsoft Forms in an Incognito/InPrivate browser session and confirmed the Defender for Cloud Apps monitoring notice: **Access to Microsoft Forms is monitored**.

. Created the Defender for Cloud Apps access policy **Monitor Microsoft Forms access** under **Policies > Policy management**.

. Set the policy category to **Access control**, selected the Microsoft Forms app condition, and retained the **Test** action so matching activity would be monitored rather than blocked.

. Enabled alert creation and email notifications, using the tenant address **lami@fikayo.onmicrosoft.com** as the alert recipient.

. Confirmed that **Monitor Microsoft Forms access** appeared in the Defender access-policy list with **Active** status.

## Validation and results

| Validation | Observed result |
|---|---|
| Baseline Forms access | Lami could access Microsoft Forms |
| Entra Conditional Access policy | Created for Lami and Microsoft Forms; enabled |
| App Control mode | Monitor only |
| Monitored-session notice | Displayed when accessing Microsoft Forms |
| Defender access policy | Created and listed as Active |
| Activity log | Recorded Lami's Microsoft Forms SSO logon |
| Matched Conditional Access policy | **Monitor Lami using Forms** appeared in the matched-policy details |

The activity-log record and matched-policy details provide evidence that the Forms sign-in was evaluated against the Entra Conditional Access App Control policy.

## Important distinctions and limitations

. **Monitor only** routes and monitors the browser session; it does not block the user from accessing Microsoft Forms.

. The Defender for Cloud Apps access policy used the **Test** action. It was configured to monitor matching activity, not to block it.

. The access policy was configured to create alerts and send email notifications. The evidence confirms the alert settings and policy creation; it does not independently confirm delivery of an alert email.

. The matched-policy evidence identifies the Entra Conditional Access policy **Monitor Lami using Forms**. It should not be confused with the separate Defender access policy **Monitor Microsoft Forms access**.

## Evidence

The `screenshots/` folder is reserved for the 12 selected evidence images. The accompanying ZIP package contains the same images, ready for upload.

See [screenshots/README.md](screenshots/README.md) for the evidence index.

## Completion checklist

- [x] Confirmed baseline Microsoft Forms access for Lami
- [x] Created and enabled the Entra Conditional Access policy
- [x] Scoped the policy to Microsoft Forms
- [x] Configured Conditional Access App Control in Monitor only mode
- [x] Verified the monitored-access notice
- [x] Created the Defender for Cloud Apps access policy
- [x] Configured Test action and email alert settings
- [x] Confirmed the Defender access policy is Active
- [x] Verified the Forms sign-in in the Defender activity log
- [x] Verified the Entra policy in matched-policy details
- [x] Compiled the selected screenshot evidence
