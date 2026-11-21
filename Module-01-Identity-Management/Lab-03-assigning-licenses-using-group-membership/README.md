# Project – Group-Based Licensing and Dynamic Membership

**Project area:** Microsoft Entra ID identity and access management  
**Implementation status:** Completed — configuration, membership results, and published evidence verified  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Objective

Implement group-based licence assignment and dynamic group membership in Microsoft Entra ID. The work covers assigned security groups, Microsoft 365 groups, licence inheritance, and dynamic classification of all users, guest users, and member users.

## Environment

The implementation used the following tenant identities, licence SKU, and group names:

| Component | Implemented configuration |
|---|---|
| Licence validation identity | **Lami** — used for inherited-licence validation |
| Licence SKU | **Microsoft 365 E5** |
| Direct-assignment baseline | **Jones** — existing direct assignment inspected and left unchanged |
| Licensing security group | **sec-001** — assigned security group for group-based licensing |
| Microsoft 365 group | **sec-002** |
| All-users dynamic group | **dynamic-001** |
| Guest-only dynamic group | **dynamic guest-001** |
| Member-only dynamic group | **dynamic member-001** |

Jones was inspected as an initial licensing baseline. Jones had an active Microsoft 365 E5 licence assigned **Directly**. That existing assignment was left unchanged. Lami was used as the test identity for group-based licence inheritance.

## Implementation

### 1. Group-based licence assignment

1. Inspected Jones's user licence page. Microsoft 365 E5 was active, with 91 of 91 services enabled, and the assignment path was Direct.
2. Created the assigned-membership security group **sec-001**, with one administrator owner and Lami as its member.
3. In Microsoft 365 admin center, assigned Microsoft 365 E5 to **sec-001**. The portal showed 23 of 25 E5 licences available before assignment and 22 of 25 after assignment.
4. Opened Lami's Entra ID licence page and verified Microsoft 365 E5 was Active, with 91 of 91 services enabled, and the assignment path was **Inherited (sec-001)**.

**Observed result:** Group-based licence inheritance was verified in Entra ID. Microsoft 365 E5 was used for licence assignment. Validation was performed using the licence assignment path in Entra ID.

### 2. Microsoft 365 group configuration

1. Created **sec-002** with group type **Microsoft 365** and membership type **Assigned**.
2. Added the two tenant accounts selected for this implementation: **bbb** and **Samuel Adeyemi**.
3. Verified the group membership page showed two members.

**Observed result:** The Microsoft 365 group was created successfully with two assigned members.

### 3. Dynamic group for all users

Created the security group **dynamic-001** with **Dynamic User** membership and the rule:

~~~text
user.objectId -ne null
~~~

The rule includes user objects with a non-null Object ID. The group initially showed zero members while membership processing was pending. After processing, the overview showed **70 users**, and the Members page showed 70 group members.

**Important clarification:** The group's description is informational text only. It does not filter membership. The membership rule above includes all matching user objects; it is not an EU-country filter. No EU-country group was created as part of this implementation.

### 4. Dynamic groups for guests and members

Created two additional security groups to validate separate Guest and Member membership rules without changing **dynamic-001**.

**Guest-only group:** **dynamic guest-001**

~~~text
(user.objectId -ne null) and (user.userType -eq "Guest")
~~~

**Observed result:** The group overview showed **2 users**.

**Member-only group:** **dynamic member-001**

~~~text
(user.objectId -ne null) and (user.userType -eq "Member")
~~~

**Observed result:** The group overview showed **68 users**.

The counts reconcile with the all-users group: 2 guest users + 68 member users = 70 users. This is consistent with the observed tenant membership results.

## Validation results

| Test | Expected result | Observed result |
|---|---|---|
| Jones licence baseline | Existing licence and assignment path visible | **Pass** – Microsoft 365 E5 Active; assignment path Direct |
| Security group creation | Assigned security group with owner and test member | **Pass** – sec-001 created with one owner and one member |
| Group licence assignment | E5 assigned to security group | **Pass** – Microsoft 365 E5 appears under Assigned to this group |
| User licence inheritance | Group member receives licence through group | **Pass** – Lami shows E5 Active; path Inherited (sec-001) |
| Microsoft 365 group | Group created with two assigned members | **Pass** – sec-002 shows two members |
| All-users dynamic group | Matching users populate automatically | **Pass** – dynamic-001 shows 70 users |
| Guest-only dynamic group | Only Guest users match | **Pass** – dynamic guest-001 shows 2 users |
| Member-only dynamic group | Only Member users match | **Pass** – dynamic member-001 shows 68 users |
| Guest/member reconciliation | Guest and Member results reconcile to all-users total | **Pass** – 2 + 68 = 70 |
| Evidence publication | Redacted implementation screenshots available in repository | **Pass** – 12 screenshots and their evidence index are published in this lab's screenshots folder |

## Evidence

The repository contains 12 redacted screenshots documenting the implementation and validation results. Browser tabs, address-bar details, signed-in administrator identity, breadcrumb identifiers, and visible email-address fields have been obscured where applicable.

See [screenshots/README.md](./screenshots/README.md) for the filename-by-filename evidence descriptions.

**Validation boundary:** The screenshots document the licence state, group configuration, membership rules, and observed membership results in Microsoft Entra ID. Separate end-user sign-in to Office web apps was not captured and is not claimed as a test result.

## Technical notes and lessons learned

- **Licence SKU:** Microsoft 365 E5 was used for group-based assignment. The available licence count decreased from 23 to 22 after group assignment.
- **Direct versus inherited assignment:** Jones's licence was Direct. Lami's licence showed Inherited (sec-001), confirming the group-based assignment path.
- **Dynamic membership delay:** dynamic-001 initially showed zero members. After membership processing, it populated to 70 users.
- **Description versus rule:** A group's description does not control dynamic membership. The rule syntax determines which users are included.
- **Country filtering:** The all-users expression is not an EU-country filter. A country-based group would require a separate rule based on user country attributes and was outside the scope of this implementation.
- **Licence validation:** Licence status and inherited assignment path were verified in Microsoft Entra ID.

## Security and publication notes

- No passwords, access tokens, recovery codes, or licence purchase information are included.
- Public evidence is redacted to avoid exposing account and tenant details.
- Test identities and group names are documented where needed to explain the implemented configuration and observed results.

## Implementation checklist

- [x] Tenant licence inventory and test-user baseline inspected
- [x] Security group created
- [x] Microsoft 365 E5 assigned to the security group
- [x] Inherited licence assignment verified on the test user
- [x] Microsoft 365 group created and two members verified
- [x] All-users dynamic group created and 70 users verified
- [x] Guest-only dynamic rule tested and 2 users verified
- [x] Member-only dynamic rule tested and 68 users verified
- [x] Validation results and implementation details documented
- [x] Screenshots captured and redacted
- [x] Redacted screenshots published in this repository
- [x] Final repository evidence review completed
