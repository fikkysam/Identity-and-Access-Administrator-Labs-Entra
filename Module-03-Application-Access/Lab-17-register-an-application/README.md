# Lab 17 – Register an Application and Manage App Registrations with a Custom Role

**Module:** Application Access  
**Status:** Implemented and portal-validated; redacted screenshot ZIP prepared; GitHub image upload pending

## Objective

Register a Microsoft Entra application, configure its web redirect URI and client secret, expose delegated API scopes, and create a focused custom directory role for application credential management.

## Environment and implementation notes

. Created the single-tenant app registration **Demo app** in the non-production Microsoft Entra tenant.

. Configured the **Web** platform redirect URI as `https://localhost`.

. Created a client secret with a **90-day** lifetime. The configured description in the portal was `lab secret`. The secret value is intentionally not recorded in this repository or in this document.

. The client-secret value was partially visible in a screenshot shared during the guided session. It was not copied into repository documentation. If there is any concern that the value was exposed, delete the secret and issue a replacement, then store the replacement securely.

## Expose an API

The lab requested the Application ID URI `api://DemoAppAPI`. Microsoft Entra rejected that value under the tenant's identifier URI formatting policy. The error required a tenant-verified domain, tenant ID, or application ID in the identifier URI.

. Retained the automatically generated Application ID URI: `api://b4bb1a98-6316-4b69-adeb-40f270727a2f`.

. Created the delegated scope **Employees.Read.All** with **Admins and users** consent and **Enabled** state.

. Set its admin consent display name to **Read-only access to employee records** and its user consent display name to **Read-only access to your employee records**.

. Created the delegated scope **Employees.Write.All** with **Admins only** consent and **Enabled** state.

. Set its admin consent display name to **Write access to employee records**. User consent display name and description were left blank, as required.

. Left the optional authorized client applications section empty.

## Custom directory role

Created the custom role **My custom app role** with these two permissions:

| Permission | Portal description |
|---|---|
| `microsoft.directory/servicePrincipals/managePasswordSingleSignOnCredentials` | Read password single sign-on credentials on service principals |
| `microsoft.directory/servicePrincipals/synchronizationCredentials/manage` | Manage application provisioning secrets and credentials |

The role appeared in **Roles and administrators → Microsoft Entra ID roles** with type **Custom**. The role had **0 assignments** at the time of validation; no role assignment was part of the supplied exercise instructions.

## Validation results

| Item | Result |
|---|---|
| Demo app registration | Created; single tenant |
| Web redirect URI | `https://localhost` configured |
| Client secret | Created; 90-day lifetime |
| Requested custom Application ID URI | Rejected by tenant identifier URI policy |
| Retained Application ID URI | Generated app-ID-based URI |
| Employees.Read.All | Enabled; Admins and users |
| Employees.Write.All | Enabled; Admins only |
| My custom app role | Created with both required permissions |
| Custom role assignment | Not performed; 0 assignments shown |

## Security and implementation considerations

. Client secret values, passwords, tokens, and other credentials must never be committed to GitHub.

. Client secrets are less secure than certificates for production application authentication. Use certificate-based credentials or an appropriate federated credential approach for production workloads where supported.

. The custom role contains credential-management permissions and should be assigned only to appropriately authorized administrators after reviewing the operational need.

. The API scopes are delegated permissions. The lab's **Expose an API** page explicitly distinguishes these from application-only permissions, which are configured through app roles.

## Evidence

Nine screenshots have been selected and packaged in **Lab-17-Application-Registration-Evidence-Redacted.zip**. The client-secret Value cell in screenshot 05 has been covered with an opaque redaction; the secret value is not included in the ZIP.

The archive contains these files:

. `01-demo-app-registration.png`
. `02-demo-app-overview.png`
. `03-web-redirect-uri-configured.png`
. `04-client-secret-creation-settings.png`
. `05-client-secret-created-REDACTED.png`
. `06-api-scopes-configured.png`
. `07-custom-role-permissions-selected.png`
. `08-custom-role-review.png`
. `09-custom-role-created.png`
. `README.md`

See [screenshots/README.md](screenshots/README.md) for the matching evidence index. The ZIP is prepared locally; the PNG files still need to be uploaded to GitHub.

## Completion checklist

- [x] Register the single-tenant Demo app
- [x] Configure the Web redirect URI
- [x] Create a 90-day client secret
- [x] Record the tenant policy exception for the requested Application ID URI
- [x] Create and enable Employees.Read.All
- [x] Create and enable Employees.Write.All
- [x] Create My custom app role
- [x] Verify both custom role permissions
- [x] Prepare the nine-image redacted screenshot evidence ZIP\n- [ ] Upload the redacted PNG files to the repository
