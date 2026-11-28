# Lab 18 – Register an Application

**Source exercise:** Microsoft SC-300 – “Lab 19: Register an application”  
**Personal roadmap number:** Lab 18  
**Platform:** Microsoft Entra admin center  
**Estimated source duration:** 30 minutes

## Objective

Register an application in Microsoft Entra ID, configure its web platform settings and credentials, expose delegated API scopes, and create a least-privilege custom directory role for credential management.

## Implementation record

### Exercise 1 – Register an application

- Registered the single-tenant application **Demo app** in Microsoft Entra ID.
- Configured the **Web** platform redirect URI as `https://localhost`.
- Created a client secret with a **90-day** lifetime.
- Created the secret with the description `lab secret`; the source instructions specify `SC300 lab secret`. This is a documented naming deviation and does not change the credential configuration.
- Exposed the API and configured two enabled delegated scopes:
  - **Employees.Read.All** — consent allowed for admins and users.
  - **Employees.Write.All** — admin consent only; user-consent display name and description left blank.

### Application ID URI deviation

The source exercise requests `api://DemoAppAPI`. Microsoft Entra rejected that identifier URI under the tenant's identifier URI policy. The application retained the generated default URI:

`api://b4bb1a98-6316-4b69-adeb-40f270727a2f`

The scopes were created under that accepted URI. This is an environment-policy adaptation, not an omitted task.

### Exercise 2 – Manage app registration with a custom role

Created the custom directory role **My custom app role** with the two credential-management permissions specified in the source exercise:

- `microsoft.directory/servicePrincipals/managePasswordSingleSignOnCredentials`
- `microsoft.directory/servicePrincipals/synchronizationCredentials/manage`

The role was verified in **Entra ID → Roles & admins**. No role assignment was required by the supplied exercise steps.

## Validation and evidence

The application registration, redirect URI, client secret configuration, both API scopes, and custom role permissions were reviewed in the Microsoft Entra portal.

The screenshot evidence package contains nine screenshots. The client-secret value is fully redacted in the evidence copy. Never publish the secret value, access tokens, passwords, or recovery codes.

See [screenshots](./screenshots/README.md) for the evidence index.

## Completion checklist

- [x] Register **Demo app**
- [x] Configure Web redirect URI `https://localhost`
- [x] Create a 90-day client secret
- [x] Expose the API and create **Employees.Read.All**
- [x] Create **Employees.Write.All** with admin-only consent
- [x] Create **My custom app role**
- [x] Verify both required custom-role permissions
- [x] Document the tenant identifier-URI policy deviation
- [x] Prepare redacted screenshot evidence

## Learning outcomes

- Understand the application registration trust relationship with the Microsoft identity platform.
- Configure a platform-specific redirect URI.
- Distinguish client secrets from certificates and understand why certificates are recommended for production confidential clients.
- Expose delegated API permissions and configure user versus administrator consent.
- Apply least privilege through a custom Microsoft Entra directory role.

## Source

Microsoft SC-300 Identity and Access Administrator learning lab, “Lab 19 – Register an application” (personal roadmap: Lab 18).
