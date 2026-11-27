# Lab 07 – Add Hybrid Identity with Microsoft Entra Connect

**Module:** Identity Management  
**Status:** Completed (user-confirmed hands-on implementation)

## Objective

Implement a hybrid identity environment by integrating on-premises Active Directory Domain Services (AD DS) with Microsoft Entra ID using Microsoft Entra Connect. The goal is to understand how on-premises identities are represented and managed in the cloud.

## Implementation summary

The user has confirmed that the hybrid identity environment and this lab's hands-on implementation have already been completed in their existing home lab. The environment was not rebuilt for this documentation update.

The documented scope of this lab covers:

- On-premises Active Directory Domain Services (AD DS) as the on-premises identity directory.
- Microsoft Entra Connect as the synchronization component between AD DS and Microsoft Entra ID.
- Hybrid identity synchronization and the relationship between on-premises and cloud directory objects.
- Understanding source of authority in a hybrid identity configuration.
- Reviewing synchronization health and troubleshooting considerations.

## Validation and proof of completion

The following evidence is appropriate to demonstrate the completed implementation. Capture only the items that are available from the environment; do not recreate the lab solely to obtain screenshots.

- [ ] Active Directory Users and Computers showing the lab domain and test users (redact personal or sensitive details).
- [ ] Microsoft Entra Connect configuration or installation summary showing the configured directory connection and selected sign-in/synchronization method.
- [ ] Synchronization status or Synchronization Service Manager showing a successful synchronization cycle.
- [ ] Microsoft Entra admin center showing one or more synchronized users and their on-premises synchronization/source attributes.
- [ ] A validation screenshot showing that a test identity is present in both directories and that the expected attributes are synchronized.

**Evidence handling:** Redact tenant identifiers, email addresses where unnecessary, domain details that should remain private, credentials, tokens, and other sensitive values before publishing screenshots. Do not publish secrets or recovery codes.

## Key concepts demonstrated

- Hybrid identity connects an on-premises directory with Microsoft Entra ID.
- Microsoft Entra Connect synchronizes directory objects and selected attributes between the environments.
- Source of authority determines where particular identity attributes are mastered and managed.
- Synchronization health and error review are important operational checks in a hybrid identity deployment.

## Troubleshooting and lessons learned

The lab is recorded as completed based on the user's confirmation of the existing hands-on implementation. Environment-specific errors, resolutions, synchronization results, and screenshots should be added only when the corresponding details or evidence are available; no test output has been fabricated in this record.

## Completion checklist

- [x] Prerequisites and existing lab environment prepared
- [x] Hybrid identity implementation performed (user-confirmed)
- [x] Lab work completed in the existing environment (user-confirmed)
- [ ] Redacted evidence screenshots added to the `screenshots/` folder
- [x] Completion documented
- [x] Progress tracker updated

## Official instructions

[Open the Microsoft lab instructions](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_07_AddHybridIdentityWithAzureADConnect.html)
