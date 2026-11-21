# Project – Microsoft Entra Tenant Configuration and Privacy Controls

**Project area:** Microsoft Entra ID tenant administration  
**Implementation status:** Completed  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Project overview

This implementation covers tenant-level configuration and organizational privacy information. It includes creating a custom `.onmicrosoft.com` subdomain, updating the tenant display name, reviewing tenant location metadata, recording the Tenant ID securely, and configuring and validating the organizational privacy notice.

## Implementation

### 1. Custom subdomain configuration

- Opened **Entra ID → Domain names** and initiated the custom-domain workflow.
- Used the Microsoft 365 admin center to manage the `.onmicrosoft.com` subdomain.
- Created **`sales.fikayo.onmicrosoft.com`**.
- Stopped at the DNS-record stage; DNS records were not configured or verified.

**Observed state:** The subdomain appears in the Microsoft 365 Domains list with **Incomplete setup**. The tenant's default domain remained **Healthy**.

**Configuration note:** The subdomain creation is documented as completed, but the domain is not presented as DNS-verified or production-ready.

### 2. Tenant properties and data location review

- Updated the tenant display name to **Contoso Marketing**.
- Reviewed the technical contact and retained the administrator contact already configured in the tenant.
- Confirmed the tenant country/region displayed as **Canada**.
- Reviewed the displayed **Data location (Primary Copy): United States datacenters** value in the Entra portal.
- Located the unique Tenant ID and recorded it for future administration. The identifier is intentionally not published.

### 3. Organizational privacy configuration

- Set the **Global privacy contact** to the existing tenant user **Lami**.
- Configured the organizational privacy statement URL used for this implementation.
- Opened **My Account → Data and Privacy → Organization's notice**.
- Selected the organizational privacy statement and confirmed that the Contoso Privacy Statement Sample PDF opened successfully.

**Observed result:** The organizational privacy notice was accessible to the user through the My Account privacy experience.

## Validation summary

| Area | Result | Evidence |
|---|---|---|
| Custom subdomain | **Created** | `sales.fikayo.onmicrosoft.com` listed in Microsoft 365 Domains |
| DNS configuration | **Intentionally not completed** | Domain remains Incomplete setup |
| Default domain | **Healthy** | Domain status reviewed |
| Tenant display name | **Updated** | Contoso Marketing displayed |
| Technical contact | **Reviewed** | Existing administrator contact retained |
| Country/region | **Reviewed** | Canada |
| Primary-copy data location | **Reviewed** | United States datacenters, as displayed in the portal |
| Tenant ID | **Located and recorded privately** | Identifier not included in public documentation |
| Global privacy contact | **Configured** | Lami |
| Organizational privacy notice | **Verified** | Notice opened and sample PDF displayed |

## Technical findings

- **Domain administration:** The Microsoft 365 admin center was used for the `.onmicrosoft.com` subdomain workflow.
- **DNS status:** Creating the subdomain does not itself complete DNS verification. The domain remains in **Incomplete setup** because DNS configuration was deliberately not performed.
- **Tenant metadata:** Country/region and primary-copy data location are distinct tenant properties and were recorded as displayed by the portal.
- **Privacy notice:** The organization-level notice was accessible through **My Account → Data and Privacy → Organization's notice**.
- **Privacy statement limitation:** The configured Contoso Privacy Statement Sample PDF is demonstration content, not a production legal privacy policy.

## Evidence

The redacted evidence package contains six screenshots:

| File | What the screenshot demonstrates |
|---|---|
| `01-Domain-Created.png` | Microsoft 365 Domains list showing the new sales subdomain and its Incomplete setup status |
| `02-DNS-Setup-Skipped.png` | DNS-record stage, documenting that DNS configuration was not performed |
| `03-Tenant-Properties-Redacted.png` | Tenant display name, country/region, primary-copy data location, and redacted Tenant ID field |
| `04-Privacy-Configuration-Redacted.png` | Technical contact, global privacy contact, and privacy statement configuration fields |
| `05-Organization-Privacy-Notice.png` | Organization's notice section in Microsoft My Account |
| `06-Privacy-Statement-Verified.png` | Contoso Privacy Statement Sample PDF opened successfully |

Sensitive tenant identifiers and contact details are omitted or redacted in public evidence.

## Completion

**Status: Completed.** The tenant display name, privacy contact, and organizational privacy notice were configured and validated. The custom subdomain was created, but DNS configuration and verification were intentionally left incomplete and are not represented as completed.
