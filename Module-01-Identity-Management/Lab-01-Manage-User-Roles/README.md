# Lab 01 – Manage User Roles

**Module:** 01 – Implement an Identity Management Solution  
**Status:** Planned  
**Estimated time in Microsoft instructions:** 30 minutes (actual time may vary)

## Scenario

A new employee needs application administrator responsibilities. Create the user, test the permissions before role assignment, assign the least-privileged appropriate role, verify the changed permissions, remove the role, and complete the user-management exercises.

## Official Microsoft instructions

[Lab 01 – Manage user roles](https://microsoftlearning.github.io/SC-300-Identity-and-Access-Administrator/Instructions/Labs/Lab_01_ManageUserRoles.html)

## Lab environment and sign-in

The Microsoft instructions specify the Microsoft 365 + E5 tenant sign-in (MOD Administrator account) for this lab. Use a dedicated training tenant you are authorized to administer. Do not use production identities or reuse passwords from other services.

The lab may prompt for MFA. Follow the tenant's authorized sign-in process. Confirm current licensing and available roles before starting.

## Exercise 1 – Create a user and test application administrator rights

### Task 1 – Add a new user
1. Open the Microsoft Entra admin center: https://entra.microsoft.com.
2. Sign in with the lab administrator account.
3. Navigate to **Entra ID → Users → All users → New user → Create new user**.
4. Create the test user using the lab's specified identity values: **ChrisG** (user principal name) and **Chris Green** (display name).
5. Use the portal's auto-generated password option.
6. Store the temporary credentials securely for the lab session; do not add them to this repository.
7. Review and create the user.

### Task 2 – Verify permissions before role assignment
1. Open a new InPrivate browser window.
2. Sign in to https://entra.microsoft.com as Chris Green.
3. Complete the required first sign-in password change and any prompted MFA setup.
4. Open **Enterprise applications**.
5. Observe that **New application → Create your own application** is unavailable to this unprivileged test user.
6. Check the relevant consent and user settings to understand the current permission boundary.
7. Sign out.

**Record:** Capture the before-role-assignment state, with usernames, tenant identifiers, and other sensitive details redacted.

## Exercise 2 – Assign Application Administrator and verify

### Task 1 – Assign the role
1. Sign in with an administrator account authorized to assign directory roles.
2. Navigate to **Entra ID → Users → All users → Chris Green → Assigned roles**.
3. Select **Add assignments**.
4. Choose **Application Administrator**.
5. Follow the assignment workflow. Select an assignment type supported by the tenant and lab instructions; if PIM is active, follow the lab's PIM-specific permanent/eligible assignment guidance rather than assuming the controls are identical.
6. Provide a meaningful justification, then assign the role.
7. Refresh and verify the role appears.

### Task 2 – Verify application permissions
1. Open a new InPrivate browser window and sign in as Chris Green.
2. Open **Enterprise applications → New application**.
3. Verify that **Create your own application** is now available.
4. Do not create or consent to an unnecessary production application. For this validation, record the availability of the control as the expected permission change.
5. Sign out.

**Record:** Document the role, assignment type, justification, before/after observations, and any licensing or PIM behavior.

## Exercise 3 – Remove the role assignment
1. Sign in with an authorized administrator account.
2. Open **Microsoft Entra roles and administrators**.
3. Select **Application Administrator** and review its assignments.
4. Locate the test user and remove the assignment.
5. Confirm the removal and verify that the user no longer has the role.

**Record:** Capture the role assignment before removal and the post-removal state, with sensitive details redacted.

## Exercise 4 – Bulk user creation
1. Navigate to **Entra ID → Users → All users → Bulk operations → Bulk create**.
2. Download the current CSV template or use the sample file supplied with the official lab environment.
3. Populate only the required fields and valid tenant domain values.
4. Upload the CSV and submit the bulk creation.
5. Verify the resulting test users in **All users**.

Do not commit CSV files containing real user information or passwords. If you retain a sanitized example, use fictional identities and placeholder values only.

## Exercise 5 – Bulk user creation with Microsoft Graph PowerShell
The official lab uses the Microsoft Graph PowerShell SDK and a delegated permission scope for user creation.

1. Use PowerShell 7.2 or later as specified by the lab.
2. Install the Microsoft Graph module if it is not already available:
   `Install-Module Microsoft.Graph -Scope CurrentUser`
3. Confirm module installation:
   `Get-InstalledModule Microsoft.Graph`
4. Connect using the scope specified by the lab:
   `Connect-MgGraph -Scopes "User.ReadWrite.All"`
5. Verify the signed-in Graph context and inspect users:
   `Get-MgUser`
6. Create only clearly identified test users, using a unique test UPN in your tenant and a securely handled password profile.
7. Verify the created user in the Entra admin center and with Microsoft Graph.
8. Disconnect the Graph session when finished.

Never paste real passwords into committed scripts or documentation. Use secure credential handling and least-privilege permissions appropriate to the task.

## Exercise 6 – Delete and restore a test user
1. Select a dedicated test user in **Entra ID → Users → All users**.
2. Delete the test user and confirm the action.
3. Open **Deleted users**.
4. Select the test user and restore it.
5. Verify that it reappears in **All users**.

Use only a lab-created test identity. Confirm the tenant's current deleted-user retention behavior before relying on recovery.

## Exercise 7 – Assign a license to a user
1. Find the unlicensed test user specified by the official lab data.
2. Verify the user has a **Usage location**; license assignment requires a usage location.
3. Open the Microsoft 365 admin center: https://admin.microsoft.com.
4. Navigate to **Billing → Licenses**, select the available license specified by the lab, and assign it to the test user.
5. Return to the Entra admin center and verify the license assignment.

Only assign a license if it is available and permitted in your training tenant. Do not purchase a subscription or consume paid licenses without authorization.

## Validation checklist

- [ ] Test user created successfully.
- [ ] Baseline application permissions observed before role assignment.
- [ ] Application Administrator role assigned and visible.
- [ ] Application creation control becomes available to the test user.
- [ ] Role removed and assignment no longer present.
- [ ] Bulk CSV user creation tested and verified.
- [ ] Microsoft Graph user creation tested and verified.
- [ ] Test user deletion and restoration verified.
- [ ] License assignment and usage location verified, if the required license is available.

## Evidence to capture

Save screenshots in this folder's `screenshots/` directory. Suggested evidence:
1. Test user profile (redacted).
2. Before-role application creation restriction.
3. Assigned role and assignment type.
4. After-role application creation availability.
5. Role removal confirmation.
6. Bulk user creation result.
7. Microsoft Graph verification output (no secrets).
8. Deleted user and restored user states.
9. License assignment and usage location.

## Findings and troubleshooting

_To be completed during the hands-on session. Record actual errors, root causes, resolutions, portal differences, role propagation delays, and licensing limitations._

## Completion

This lab remains **Planned** until all applicable tasks have been performed, validated, and documented. Update the root [progress tracker](../../../PROGRESS.md) only after validation.