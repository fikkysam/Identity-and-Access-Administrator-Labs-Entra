# Project – Group-Based Licensing and Dynamic Membership

**Project area:** Microsoft Entra ID identity and access management  
**Implementation status:** Validated — redacted evidence package prepared; screenshot upload to this repository remains pending  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Objective

Create and manage assigned security and Microsoft 365 groups, assign a Microsoft 365 licence to a security group, verify inherited licensing, and use dynamic membership rules to automatically classify all users, guest users, and member users.

## Environment adaptations

The Microsoft sample instructions use Delia Dennis, Office 365 E3, and the group names **sg-SC300-O365**, **Northwest Sales**, and **SC300-myDynamicGroup**. This tenant used different test identities and naming conventions:

| Microsoft sample / exercise | Actual implementation in this tenant |
|---|---|
| Delia Dennis | **Lami** — used for inherited-licence validation |
| Office 365 E3 | **Microsoft 365 E5** |
| sg-SC300-O365 | **sec-001** — assigned security group for group-based licensing |
| Northwest Sales | **sec-002** — Microsoft 365 group |
| SC300-myDynamicGroup | **dynamic-001** — all-users dynamic security group |
| Alternate guest-only rule (additional tenant test) | **dynamic guest-001** |
| Alternate member-only rule (additional tenant test) | **dynamic member-001** |

The final two groups are additional tenant-specific groups created to test the alternate Guest and Member rules in the dynamic membership configuration; they are not replacements for separate named groups in the Microsoft sample.

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
2. Added the two tenant test accounts selected during the exercise: **bbb** and **Samuel Adeyemi**.
3. Verified the group membership page showed two members.

**Observed result:** The Microsoft 365 group was created successfully with two assigned members. 

### 3. Dynamic group for all users

Created the security group **dynamic-001** with **Dynamic User** membership and the rule:

~~~text
user.objectId -ne null
~~~

The rule includes user objects with a non-null Object ID. The group initially showed zero members while membership processing was pending. After processing, the overview showed **70 users**, and the Members page showed 70 group members.

**Important clarification:** The group's description is informational text only. It does not filter membership. The membership rule above includes all matching user objects; it is not an EU-country filter. No EU-country group was created as part of this lab.

### 4. Dynamic groups for guests and members

Created two additional security groups to test the alternate rules without changing **dynamic-001**.

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

## Evidence

The project evidence package contains 12 redacted screenshots and a screenshot index. Browser tabs, address-bar details, signed-in administrator identity, breadcrumb identifiers, and visible email-address fields have been obscured where applicable.

The 12-image archive is prepared as a local deliverable for extraction into this project's screenshots folder. It has not yet been uploaded to this GitHub repository.

See [screenshots/README.md](./screenshots/README.md) for the filename-by-filename evidence descriptions and upload checklist.

## Technical notes and lessons learned

- **Licence SKU adaptation:** Microsoft 365 E5 was used instead of Office 365 E3. The available licence count decreased from 23 to 22 after group assignment.
- **Direct versus inherited assignment:** Jones's licence was Direct. Lami's licence showed Inherited (sec-001), proving the group-based assignment path.
- **Dynamic membership delay:** dynamic-001 initially showed zero members. After membership processing, it populated to 70 users.
- **Description versus rule:** A group's description does not control dynamic membership. The rule syntax determines which users are included.
- **Country filtering:** The all-users expression is not an EU-country filter. A country-based group would require a separate rule based on user country attributes and was outside the scope of this project.
- **Office web-app validation:** Licence status and inherited assignment path were verified in Microsoft Entra ID.

## Security and publication notes

- No passwords, access tokens, recovery codes, or licence purchase information are included.
- Public evidence is being redacted to avoid exposing account and tenant details.
- Test identities and group names are documented only where needed to explain the observed configuration.

## Implementation checklist

- [x] Tenant licence inventory and test-user baseline inspected
- [x] Security group created
- [x] Microsoft 365 E5 assigned to the security group
- [x] Inherited licence assignment verified on the test user
- [x] Microsoft 365 group created and two members verified
- [x] All-users dynamic group created and 70 users verified
- [x] Guest-only dynamic rule tested and 2 users verified
- [x] Member-only dynamic rule tested and 68 users verified
- [x] Validation results and deviations documented
- [x] Screenshots captured and redacted
- [ ] Redacted screenshot archive uploaded and extracted into this repository
- [ ] Final repository evidence review completed
