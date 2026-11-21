# Lab 03 Screenshot Evidence

All screenshots in this folder were redacted before publication. Browser tabs/address bars and the signed-in administrator identity are obscured. Email-address fields are obscured where visible.

| File | What it demonstrates |
|---|---|
| `01-Jones-Direct-License-Baseline.png` | Jones baseline: Microsoft 365 E5 is active and assigned directly. |
| `02-Security-Group-sec001-Created.png` | Security group sec-001 creation form showing Security, Assigned membership, one owner and one member. |
| `03-sec001-E5-License-Assigned.png` | Microsoft 365 E5 appears under Assigned to this group for sec-001. |
| `04-Lami-Inherited-E5-License.png` | Lami has an active Microsoft 365 E5 licence inherited from sec-001. |
| `05-sec002-M365-Group-Members.png` | Microsoft 365 group sec-002 with two assigned members. |
| `06-All-Users-Dynamic-Rule.png` | Dynamic membership rule user.objectId -ne null. |
| `07-dynamic001-Group-Configuration.png` | Dynamic security group configuration, Dynamic User membership, description and owner. |
| `08-dynamic001-70-Members.png` | dynamic-001 overview showing 70 user members after processing. |
| `09-dynamic001-Member-List.png` | dynamic-001 Members page showing 70 group members. |
| `10-Guest-Only-Dynamic-Rule.png` | Guest-only dynamic rule using user.userType -eq Guest. |
| `11-Guest-Only-Group-2-Members.png` | dynamic guest-001 overview showing two automatically included guest users. |
| `12-Member-Only-Group-68-Members.png` | dynamic member-001 overview showing 68 automatically included member users. |

## Evidence notes

- The tenant used Microsoft 365 E5, not the Office 365 E3 product in the Microsoft sample instructions.
- Lami was used as the test user instead of Delia Dennis. Jones was inspected first and had a directly assigned Microsoft 365 E5 licence; that direct assignment was left unchanged.
- The security group was named `sec-001` rather than `sg-SC300-O365`. The Microsoft 365 group was named `sec-002` rather than `Northwest Sales`.
- The all-users dynamic group was named `dynamic-001` rather than `SC300-myDynamicGroup`.
- The `sec-002` group contained the two tenant test accounts selected during the exercise.
- Dynamic membership results observed: 70 users in `dynamic-001`, 2 users in `dynamic guest-001`, and 68 users in `dynamic member-001`. The Guest and Member counts reconcile with the 70-user all-users group.
- The original lab asks for a baseline Office-app access check and a post-assignment Office-app access check. Those specific Office web-app screenshots were not captured in this session; the licence state and inherited assignment path were verified in Entra ID instead.
