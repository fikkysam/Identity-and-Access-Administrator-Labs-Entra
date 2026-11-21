# Group-Based Licensing and Dynamic Membership — Evidence

This index describes the 12 redacted screenshots prepared for this project. The archive is currently available to download from the ChatGPT conversation and has not yet been uploaded into this project evidence folder.

| File | What the screenshot demonstrates |
|---|---|
| **01-Jones-Direct-License-Baseline.png** | Jones's Microsoft 365 E5 licence is Active and assigned Directly. |
| **02-Security-Group-sec001-Created.png** | Security group sec-001 configured with Assigned membership, one owner, and one member. |
| **03-sec001-E5-License-Assigned.png** | Microsoft 365 E5 shown as assigned to sec-001. |
| **04-Lami-Inherited-E5-License.png** | Lami's Microsoft 365 E5 licence is Active and inherited from sec-001. |
| **05-sec002-M365-Group-Members.png** | Microsoft 365 group sec-002 and its two assigned members. |
| **06-All-Users-Dynamic-Rule.png** | Dynamic rule user.objectId -ne null. |
| **07-dynamic001-Group-Configuration.png** | Dynamic security group configuration, Dynamic User membership, description, and owner. |
| **08-dynamic001-70-Members.png** | dynamic-001 overview showing 70 user members after processing. |
| **09-dynamic001-Member-List.png** | Members page showing 70 users in dynamic-001. |
| **10-Guest-Only-Dynamic-Rule.png** | Guest-only rule using user.userType -eq "Guest". |
| **11-Guest-Only-Group-2-Members.png** | dynamic guest-001 overview showing two guest users. |
| **12-Member-Only-Group-68-Members.png** | dynamic member-001 overview showing 68 member users. |

## Redaction

Browser tabs and address-bar details, the signed-in administrator identity, breadcrumb identifiers, and visible email-address fields were obscured where applicable. No passwords, access tokens, or recovery codes are included.

## Implementation context

- Lami was used for inherited-licence validation; Jones's direct assignment was inspected and left unchanged.
- Group names used in the tenant were sec-001, sec-002, dynamic-001, dynamic guest-001, and dynamic member-001.
