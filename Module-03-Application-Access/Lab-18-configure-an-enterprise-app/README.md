# Lab 18 – Configure an Enterprise App

**Module:** 03 – Application Access  
**Status:** Completed  
**Application:** GitHub Enterprise Cloud – Enterprise Account  
**Platform:** Microsoft Entra admin center  
**Estimated source duration:** 5 minutes

## Objective

Your organization requires that only specific users or groups have access to enterprise applications. This lab assigns users to a specific application in Microsoft Entra ID.

## Exercise 1 – Configure an Enterprise App

### Task 1 – Add an app to the Microsoft Entra tenant

- Opened the Microsoft Entra admin center at [https://entra.microsoft.com](https://entra.microsoft.com) using an administrator account.
- Navigated to **Entra ID → Enterprise apps**.
- Opened **+ New application** and searched the Microsoft Entra gallery for **GitHub**.
- Selected **GitHub Enterprise Cloud – Enterprise Account** and created the enterprise application.
- Verified the application opened on its **Overview** page.

### Task 2 – Assign users to an app

- Opened the enterprise application's **Users and groups** page.
- Selected **+ Add user/group** and assigned:
  - **Debbie O**
  - **Oluwafikayo Oyedokun** (the administrator's own account)
- Verified both users appeared in the application's assignment list.

**Adaptation:** The Microsoft instructions use **Adele Vance** and a **MOD administrator** sample account. This tenant used Debbie O as the test user and the actual administrator account instead. The assignment objective and access-control configuration were completed.

## Validation

| Requirement | Result |
|---|---|
| GitHub Enterprise Cloud – Enterprise Account created in Entra | Verified |
| Enterprise application's Overview page opened | Verified |
| Debbie O assigned to the application | Verified |
| Administrator account assigned to the application | Verified |
| Both assignments visible under Users and groups | Verified |

The supplied exercise is about enterprise application creation and user assignment. SAML single sign-on configuration is not required for this exercise; it was performed separately as an additional activity and is documented in the Lab 17 SAML exercise.

## Completion checklist

- [x] Open Microsoft Entra Enterprise applications.
- [x] Select **+ New application**.
- [x] Search the gallery for **GitHub**.
- [x] Create **GitHub Enterprise Cloud – Enterprise Account**.
- [x] Open **Users and groups**.
- [x] Assign Debbie O.
- [x] Assign the administrator account.
- [x] Verify both users are listed as assigned.

## Evidence

See [screenshots/README.md](./screenshots/README.md) for the evidence index.

## Exercise summary

Configured user assignment and access controls for an enterprise application. This exercise demonstrates how to govern which users can access a federated application.
