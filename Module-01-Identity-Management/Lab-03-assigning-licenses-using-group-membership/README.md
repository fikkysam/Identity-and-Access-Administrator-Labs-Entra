# Lab 03 – Assigning Licenses Using Group Membership

**Module:** 01 – Identity Management  
**Status:** Validated — redacted evidence package prepared; screenshot upload to this repository remains pending  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Objective

Create and manage assigned security and Microsoft 365 groups, assign a Microsoft 365 licence to a security group, verify inherited licensing, and use dynamic membership rules to automatically classify all users, guest users, and member users.

## Official instructions

[Microsoft SC-300 – Lab 03: Assigning Licenses Using Group Membership](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_03_AssignLicensesToUsersByGroupMembershipAAD.html)

## Environment adaptations

The Microsoft sample instructions use Delia Dennis, Office 365 E3, and the group names **sg-SC300-O365**, **Northwest Sales**, and **SC300-myDynamicGroup**. This tenant used different test identities and naming conventions:

| Microsoft sample | Actual implementation |
|---|---|
| Delia Dennis | Lami for inherited-licence validation |
| Office 365 E3 | Microsoft 365 E5 |
| sg-SC300-O365 | sec-001 |
| Northwest Sales | sec-002 |
| SC300-myDynamicGroup | dynamic-001 |

Jones was inspected as an initial licensing baseline. Jones had an active Microsoft 365 E5 licence assigned **Directly**. That existing assignment was left unchanged. Lami was used as the test identity for group-based licence inheritance.

## Implementation

### Exercise 1 – Create a security group and assign a licence

1. Inspected Jones's user licence page. Microsoft 365 E5 was active, with 91 of 91 services enabled, and the assignment path was Direct.
2. Created the assigned-membership security group **sec-001**, with one administrator owner and Lami as its member.
3. In Microsoft 365 admin center, assigned Microsoft 365 E5 to **sec-001**. The portal showed 23 of 25 E5 licences available before assignment and 22 of 25 after assignment.
4. Opened Lami's Entra ID licence page and verified Microsoft 365 E5 was Active, with 91 of 91 services enabled, and the assignment path was **Inherited (sec-001)**.

**Observed result:** Group-based licence inheritance was verified in Entra ID. The original Office 365 E3 product was not available in the same form in this tenant, so Microsoft 365 E5 was used instead. The separate Microsoft 365 web-app sign-in checks described in the sample exercise were not captured; validation was performed from the user licence assignment path.

### Exercise 2 – Create a Microsoft 365 group

1. Created **sec-002** with group type **Microsoft 365** and membership type **Assigned**.
2. Added the two tenant test accounts selected during the exercise: **bbb** and **Samuel Adeyemi**.
3. Verified the group membership page showed two members.

**Observed result:** The Microsoft 365 group was created successfully with two assigned members. The sample name **Northwest Sales** and sample users Alex Wilber and Bianca Pisani were not used.

### Exercise 3 – Create a dynamic group containing all users

Created the security group **dynamic-001** with **Dynamic User** membership and the rule:

~~~text
user.objectId -ne null
~~~

The rule includes user objects with a non-null Object ID. The group initially showed zero members while membership processing was pending. After processing, the overview showed **70 users**, and the Members page showed 70 group members.

**Important clarification:** The group's description is informational text only. It does not filter membership. The membership rule above includes all matching user objects; it is not an EU-country filter. No EU-country group was created as part of this lab.

### Exercise 3 – Alternate dynamic membership rules

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

The redacted screenshot package contains 12 images and a screenshot index. Browser tabs, address-bar details, signed-in administrator identity, breadcrumb identifiers, and visible email-address fields have been obscured where applicable.

The archive is prepared locally for extraction into this lab's screenshots folder. It has not yet been uploaded to this GitHub repository.

See [screenshots/README.md](./screenshots/README.md) for the filename-by-filename evidence descriptions after the screenshot folder is populated.

## Troubleshooting and lessons learned

- **Sample users were not used:** The lab's Delia Dennis, Alex Wilber, and Bianca Pisani sample identities were replaced with tenant test accounts.
- **Licence SKU adaptation:** Microsoft 365 E5 was used instead of Office 365 E3. The available licence count decreased from 23 to 22 after group assignment.
- **Direct versus inherited assignment:** Jones's licence was Direct. Lami's licence showed Inherited (sec-001), proving the group-based assignment path.
- **Dynamic membership delay:** dynamic-001 initially showed zero members. After membership processing, it populated to 70 users.
- **Description versus rule:** A group's description does not control dynamic membership. The rule syntax determines which users are included.
- **Country filtering:** The all-users expression is not an EU-country filter. A country-based group would require a separate rule based on user country attributes and was outside this lab's specified all-users exercise.
- **Office web-app validation:** The sample's separate Office web-app sign-in checks were not performed or claimed. The licence status and inherited assignment path were verified in Entra ID.

## Security and publication notes

- No passwords, access tokens, recovery codes, or licence purchase information are included.
- Public evidence is being redacted to avoid exposing account and tenant details.
- Test identities and group names are documented only where needed to explain the observed configuration.

## Completion checklist

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
