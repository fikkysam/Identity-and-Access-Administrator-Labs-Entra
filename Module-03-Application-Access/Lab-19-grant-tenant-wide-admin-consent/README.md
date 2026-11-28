# Lab 19 – Grant Tenant-Wide Admin Consent to an Application

**Module:** 03 – Application Access  
**Status:** Completed  
**Application:** Demo app  
**Role used:** Global Administrator  
**Estimated source duration:** 15 minutes

## Objective

Grant tenant-wide admin consent to an application registered directly in the Microsoft Entra tenant. The exercise demonstrates how administrators can pre-approve permissions on behalf of all users.

## Exercise 1 – Admin Consent

### Task 1 – Grant admin consent in App registrations

- Signed in to the Microsoft Entra admin center using the Global Administrator account.
- Navigated to **Entra ID → App registrations → All applications → Demo app**.
- Opened **API permissions**.
- Reviewed the configured permissions. The screenshot provided during the lab showed **Microsoft Graph – User.Read**, with permission type **Delegated** and the description **Sign in and read user profile**.
- Initiated **Grant admin consent** and reviewed the confirmation dialog.
- Completed the consent flow. The user confirmed that Task 1 was completed.

### Task 2 – Grant admin consent in Enterprise apps

- Opened **Entra ID → Enterprise apps → Demo app**.
- Navigated to **Security → Permissions**.
- Completed the **Grant admin consent** flow using the Global Administrator account.
- Reviewed the **Permissions requested** dialog for Demo app, which displayed the delegated permission **Sign in and read user profile**.
- Accepted the consent prompt. The user confirmed that Task 2 was completed.

## Validation and evidence

| Requirement | Result |
|---|---|
| Demo app opened from App registrations | Completed |
| API permissions reviewed | Completed |
| Admin consent flow completed from App registrations | Completed (user-confirmed) |
| Demo app opened from Enterprise apps | Completed (user-confirmed) |
| Admin consent flow completed from Enterprise apps | Verified in the Permissions page (`User.Read`, Admin consent, granted by an administrator) |
| Permissions requested dialog reviewed and accepted | Completed (user-confirmed) |

The screenshots shared during the session show the Demo app API permissions page and admin-consent confirmation dialog, the Microsoft permissions-request screen for delegated **User.Read**, and the final Enterprise applications Permissions page showing **Admin consent** granted by an administrator. The user confirmed that both consent tasks were completed.

## Security considerations

- Tenant-wide admin consent authorizes the application to access the resources covered by the approved permissions on behalf of users in the organization.
- Review the requested permissions and publisher before granting consent.
- The Microsoft exercise warns that granting tenant-wide admin consent through App registrations can revoke previously granted tenant-wide permissions. User-granted permissions on behalf of individual users are not affected.
- Do not approve permissions that are not required or understood.

## Completion checklist

- [x] Sign in as a Global Administrator.
- [x] Open Demo app under App registrations.
- [x] Review API permissions.
- [x] Complete tenant-wide admin consent through App registrations.
- [x] Open Demo app under Enterprise apps.
- [x] Open Security → Permissions.
- [x] Complete tenant-wide admin consent through Enterprise apps.
- [x] Review and accept the permissions request.

## Exercise summary

Granted tenant-wide admin consent to Demo app through both App registrations and Enterprise apps. This exercise demonstrates how administrators can pre-approve application permissions on behalf of all users.
