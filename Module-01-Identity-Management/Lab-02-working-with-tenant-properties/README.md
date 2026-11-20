# Lab 02 – Working with Tenant Properties

**Module:** Identity Management  
**Status:** Completed  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Objective

Create a tenant subdomain, update tenant properties, identify tenant location and ID information, and configure and verify organizational privacy information.

## Official instructions

[Microsoft SC-300 – Lab 02: Working with Tenant Properties](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_02_WorkingWithTenantProperties.html)

## Implementation

### Exercise 1 – Create a custom subdomain

- Opened **Entra ID → Domain names** and initiated the custom-domain workflow.
- Used the Microsoft 365 admin center because management of `.onmicrosoft.com` domains is restricted in the Entra admin center.
- Added **`sales.fikayo.onmicrosoft.com`**.
- Stopped at the DNS-record stage and did not configure DNS

**Observed result:** The new subdomain appears in the Microsoft 365 Domains list with **Incomplete setup**. This is expected for this exercise because DNS configuration and verification were intentionally skipped. The tenant's default domain remained **Healthy**.

### Exercise 2 – Change and review tenant properties

- Changed the tenant display name to **Contoso Marketing**.
- Reviewed the technical contact and retained the administrator contact configured in the tenant.
- Reviewed **Tenant Country/Region: Canada**.
- Reviewed **Data location (Primary Copy): United States datacenters**, as displayed in the current Entra portal.
- Located the unique **Tenant ID** and recorded it for future lab use. The identifier is intentionally omitted from this public documentation.

### Exercise 3 – Configure privacy information

- Set the **Global privacy contact** to the existing tenant user Lami.
- Added the Microsoft Learning Contoso sample privacy statement URL.
- Opened **My Account → Data and Privacy → Organization's notice**.
- Selected the organizational privacy statement and confirmed that the Contoso Privacy Statement Sample PDF opened successfully.

## Validation results

| Test | Expected result | Observed result |
|---|---|---|
| Subdomain creation | Subdomain appears in Microsoft 365 Domains | **Pass** – listed as `sales.fikayo.onmicrosoft.com` |
| DNS configuration | DNS is not configured for this exercise | **Pass** – stopped before adding DNS records |
| Tenant display name | Tenant name field shows Contoso Marketing | **Pass** – configured |
| Country and data location | Values are visible in Tenant properties | **Pass** – Canada; United States datacenters (Primary Copy) |
| Tenant ID | Unique tenant identifier is available in Properties | **Pass** – located and recorded; value not published |
| Privacy contact | Global privacy contact field contains the selected tenant user | **Pass** – Lami configured |
| Privacy statement | Organizational privacy statement opens from My Account | **Pass** – sample PDF opened successfully |

## Evidence

The redacted evidence package contains six screenshots. Extract the ZIP contents into this lab's `screenshots/` folder before adding the image files to the repository.

| File | What the screenshot demonstrates |
|---|---|
| `01-Domain-Created.png` | Microsoft 365 Domains list showing the new sales subdomain and its expected Incomplete setup status. |
| `02-DNS-Setup-Skipped.png` | The Add DNS records stage, documenting that DNS configuration was intentionally skipped. |
| `03-Tenant-Properties-Redacted.png` | Tenant display name, country/region, primary-copy data location, and the Tenant ID field. Sensitive values are obscured. |
| `04-Privacy-Configuration-Redacted.png` | Technical contact, global privacy contact, and privacy statement configuration fields, with email addresses obscured. |
| `05-Organization-Privacy-Notice.png` | The Organization's notice section in Microsoft My Account. Personal profile details are obscured. |
| `06-Privacy-Statement-Verified.png` | The Contoso Privacy Statement Sample PDF opened successfully. |

## Troubleshooting and lessons learned

- **The custom-domain field rejected an email address:** A domain name is required, not an email address. The correct format is `sales.fikayo.onmicrosoft.com`.
- **Entra displayed a restriction message for the `.onmicrosoft.com` domain:** The workflow must be completed in the Microsoft 365 admin center.
- **The new subdomain showed Incomplete setup:** This was expected because the lab explicitly skips DNS configuration. It should not be described as DNS-verified or Healthy.
- **The privacy statement was not immediately visible:** In the current My Account experience, the relevant location is **Data and Privacy → Organization's notice**.

## Security and publication notes

- The Tenant ID and contact addresses are not reproduced in this README.
- Public evidence screenshots have been redacted to reduce exposure of tenant identifiers and personal contact details.
- The sample privacy statement is a training document, not a production legal privacy policy.
- The subdomain was created but DNS setup and verification were not performed.

## Completion checklist

- [x] Subdomain created
- [x] Tenant display name updated
- [x] Technical contact reviewed
- [x] Country/region and data location reviewed
- [x] Tenant ID located and recorded
- [x] Global privacy contact configured
- [x] Privacy statement URL configured
- [x] Privacy statement opened and verified
- [x] Evidence captured and redacted
- [x] Findings documented
