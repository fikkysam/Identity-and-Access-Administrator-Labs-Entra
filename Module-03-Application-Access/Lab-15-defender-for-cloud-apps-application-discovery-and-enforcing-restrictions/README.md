# Lab 15 – Defender for Cloud Apps Application Discovery and Enforcing Restrictions

**Module:** Application Access  
**Status:** Configuration exercise completed; endpoint enforcement validation not verified

## Objective

Use Microsoft Defender for Cloud Apps to review cloud app discovery information, inspect Dropbox in the Cloud App Catalog, and demonstrate sanctioning and unsanctioning an application.

## Official instructions

[Open the Microsoft lab instructions](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_17_DefenderForCloudAppsDiscoveryAndRestrictions.html)

## Implementation

. Opened the Microsoft Defender portal and navigated to **SaaS apps > SaaS app catalog**.

. Filtered the Cloud App Catalog by **Category: Cloud storage**.

. Selected **Dropbox** and reviewed its details under the **General** tab.

. Recorded the displayed Dropbox cloud app risk score of **10**.

. Opened Dropbox in a separate browser tab as required by the exercise, then returned to the Defender portal.

. Selected **Sanction** for Dropbox and confirmed that Defender displayed **Sanctioned app**.

. Selected **Unsanction** and confirmed that Defender displayed **Unsanctioned app**.

## Cloud discovery observations

. Reviewed the Cloud Discovery overview and the discovered-apps list for the selected user.

. The overview showed **3 apps**, **0 risky apps**, **1,256 transactions (2)**, and **39 MB** of traffic at the time captured.

. The discovered-apps view listed three detected services. Microsoft SharePoint was displayed as a protected app and tagged as sanctioned.

. These discovery figures are a point-in-time view from the lab environment, not a complete inventory of organizational cloud usage.

## Validation and results

| Test | Observed result |
|---|---|
| Cloud storage category filter | Dropbox appeared in the filtered app catalog |
| Dropbox app details | General tab displayed risk score **10** and category **Cloud storage** |
| Sanction action | Defender displayed **Sanctioned app** |
| Unsanction action | Defender displayed **Unsanctioned app** |
| Endpoint access blocking | Not independently verified on a device onboarded to Microsoft Defender for Endpoint and integrated with Defender for Cloud Apps |

**Important distinction:** Changing Dropbox to **Unsanctioned** in the catalog demonstrates the app-governance configuration. The exercise states that blocking browser access, InPrivate/Incognito access, and app downloads depends on supported devices being onboarded to Microsoft Defender for Endpoint and integrated with Defender for Cloud Apps. This endpoint enforcement was not demonstrated in the captured evidence, so it is not claimed as validated.

## Evidence

The `screenshots/` folder contains the evidence index. The five selected screenshots are packaged in the accompanying ZIP file for upload:

- `01-cloud-discovery-overview.png`
- `02-cloud-discovery-discovered-apps.png`
- `03-dropbox-cloud-storage-risk-score.png`
- `04-dropbox-sanctioned.png`
- `05-dropbox-unsanctioned.png`

See [screenshots/README.md](screenshots/README.md) for the evidence index.

## Troubleshooting and lessons learned

. In the current Defender navigation, the relevant location was **SaaS apps > SaaS app catalog**; it was not labelled **Cloud Apps** in the visible menu.

. The Cloud App Catalog and Cloud Discovery are related but different views: the catalog provides app risk and governance actions, while Cloud Discovery displays observed app usage.

. Sanctioning and unsanctioning are separate governance states. The final captured state for Dropbox was **Unsanctioned app**.

. An unsanctioned catalog status alone does not prove endpoint traffic is blocked; the Defender for Endpoint onboarding and integration prerequisites must also be met.

## Completion checklist

- [x] Reviewed Cloud Discovery overview and discovered apps
- [x] Filtered the Cloud App Catalog to Cloud storage
- [x] Reviewed Dropbox risk score and app details
- [x] Demonstrated sanctioning Dropbox
- [x] Demonstrated unsanctioning Dropbox
- [x] Captured and packaged selected screenshots
- [ ] Verify endpoint blocking on a supported, onboarded device
- [x] Documented findings and limitations
