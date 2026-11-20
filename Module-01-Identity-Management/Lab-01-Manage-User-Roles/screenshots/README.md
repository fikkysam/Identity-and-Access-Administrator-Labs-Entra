# SC-300 Lab 01 — Screenshot Evidence Guide

This folder contains the Lab 01 screenshots in workflow order. Each entry explains **what was done**, **what the screenshot shows**, and **why the step matters**. The aim is to make the evidence understandable to a reviewer who did not participate in the lab.

## Evidence index and explanations

### User creation and role-based access control

1. **`01-Created-Lami-Test-User.png`**
   - **Action:** Created the test identity named Lami in Microsoft Entra ID.
   - **What it shows:** The new user record in the directory.
   - **Why it matters:** Establishes the test account used to demonstrate user administration and role-based access control (RBAC).

2. **`02-Completed-Lami-First-Sign-In.png`**
   - **Action:** Signed in to the new account for the first time and completed the initial password-change flow.
   - **What it shows:** The first sign-in process was completed.
   - **Why it matters:** Confirms the test identity can authenticate and is ready for the permission tests.

3. **`03-Verified-Lami-User-Profile-and-Baseline.png`**
   - **Action:** Inspected Lami's profile and checked the account's baseline access before assigning an administrative role.
   - **What it shows:** The user profile and the initial application-creation experience.
   - **Why it matters:** Establishes a before-state so the effect of adding and removing a role can be compared.

4. **`04-Assigned-Application-Administrator-Role.png`**
   - **Action:** Assigned the Application Administrator directory role to Lami.
   - **What it shows:** The role assignment for the test user.
   - **Why it matters:** Demonstrates how administrative permissions are granted through Microsoft Entra roles rather than by making every user an administrator.

5. **`05-Verified-Application-Creation-Access.png`**
   - **Action:** Signed in as the test user and checked the application-creation experience after the role assignment.
   - **What it shows:** The application-creation option is available while the Application Administrator role is assigned.
   - **Why it matters:** Provides the after-state evidence that the role changed the user's administrative capability. The screenshot demonstrates access; it does not claim that an application was created.

6. **`06-Removed-Application-Administrator-Role.png`**
   - **Action:** Removed the Application Administrator role from Lami.
   - **What it shows:** The role removal action or resulting role-assignment state.
   - **Why it matters:** Demonstrates that elevated access can be withdrawn when it is no longer required.

7. **`07-Rechecked-Application-Creation-After-Role-Removal.png`**
   - **Action:** Rechecked the application-creation experience after removing the role.
   - **What it shows:** The application-creation capability is no longer available to the test user.
   - **Why it matters:** Completes the before/after test and demonstrates the principle of least privilege: the user loses the elevated capability when the role is removed.

### Bulk user provisioning and audit verification

8. **`08-Prepared-Bulk-User-Provisioning-CSV.png`**
   - **Action:** Prepared a CSV file containing the user information required for bulk provisioning.
   - **What it shows:** The input data structure used for the bulk user operation.
   - **Why it matters:** Shows how administrators can prepare multiple user records for a single provisioning workflow instead of creating every account individually.

9. **`09-Reviewed-Bulk-User-Provisioning-CSV.png`**
   - **Action:** Reviewed the CSV headers and user rows before submitting the bulk operation.
   - **What it shows:** A pre-submission check of the import file.
   - **Why it matters:** Validating the file helps catch formatting and UPN-domain errors before provisioning. Sensitive values, especially initial passwords, must not be exposed in public evidence.

10. **`10-Completed-Bulk-User-Creation.png`**
    - **Action:** Submitted the corrected CSV bulk-creation job.
    - **What it shows:** The successful completion result after the UPN-domain issue was corrected.
    - **Why it matters:** Demonstrates successful bulk provisioning and the importance of correcting input validation issues before retrying.

11. **`11-Verified-Bulk-User-Creation-in-Audit-Logs.png`**
    - **Action:** Reviewed Microsoft Entra audit logs for the user-add events.
    - **What it shows:** Audit records corresponding to the bulk user creation activity.
    - **Why it matters:** Audit logs provide an administrative record that can be used to investigate and verify directory changes, rather than relying only on the import success message.

### Microsoft Graph PowerShell administration

12. **`12-Verified-PowerShell-Environment.png`**
    - **Action:** Checked the PowerShell environment used for the command-line exercises.
    - **What it shows:** The PowerShell version/environment available for the lab.
    - **Why it matters:** Records the execution environment so the administration steps can be reproduced and troubleshooting can account for version differences.

13. **`13-Verified-Microsoft-Graph-SDK-Installation.png`**
    - **Action:** Checked that the Microsoft Graph PowerShell SDK was installed.
    - **What it shows:** The Graph module installation/version information.
    - **Why it matters:** Microsoft Graph PowerShell provides command-line access to Microsoft Entra and Microsoft 365 directory operations.

14. **`14-Authenticated-to-Microsoft-Graph.png`**
    - **Action:** Connected to Microsoft Graph using delegated authentication and requested the required permissions.
    - **What it shows:** The Graph sign-in and consent process.
    - **Why it matters:** Shows that Graph commands run within an authenticated session and that the session's delegated permissions determine which operations can be performed.

15. **`15-Verified-Graph-Connection-and-Queried-Users.png`**
    - **Action:** Checked the active Graph context and queried directory users.
    - **What it shows:** A successful Graph connection and returned user data.
    - **Why it matters:** Confirms that the session can read directory information before attempting write operations.

16. **`16-Created-Samuel-Adeyemi-with-Graph.png`**
    - **Action:** Used Microsoft Graph PowerShell to create the cloud-only test user Samuel Adeyemi.
    - **What it shows:** The user-creation command and its output, with the plaintext-password version of the screenshot excluded.
    - **Why it matters:** Demonstrates programmatic user provisioning through Microsoft Graph instead of the portal. The screenshot is evidence of the command/output, not a place to store credentials.

17. **`17-Verified-Graph-Delegated-Scopes.png`**
    - **Action:** Inspected the delegated scopes associated with the Graph session.
    - **What it shows:** The permissions granted to the authenticated session.
    - **Why it matters:** Helps explain the security boundary of the session: Graph operations are limited by the consented scopes and the signed-in user's privileges.

18. **`18-Verified-Samuel-Adeyemi-Account.png`**
    - **Action:** Located and inspected the newly created Samuel Adeyemi account.
    - **What it shows:** The resulting user object in Microsoft Entra ID.
    - **Why it matters:** Independently verifies that the programmatic creation step resulted in a directory account.

19. **`19-Updated-User-Department-with-Graph.png`**
    - **Action:** Ran a Microsoft Graph PowerShell update to set the user's department attribute.
    - **What it shows:** The attribute-update command.
    - **Why it matters:** Demonstrates how an administrator can maintain user profile attributes through Graph after an account has been created.

20. **`20-Verified-Department-Attribute-Update.png`**
    - **Action:** Queried the user again after the update.
    - **What it shows:** The updated department and job-title values.
    - **Why it matters:** A read-after-write check confirms the intended values were saved, rather than assuming that a command succeeded.

21. **`21-Diagnosed-Directory-Synced-User-Update-Limitation.png`**
    - **Action:** Attempted an optional attribute update on directory-synchronized user objects and reviewed the resulting error.
    - **What it shows:** The update was rejected because the relevant attributes are mastered on-premises.
    - **Why it matters:** Demonstrates an important hybrid identity concept: when an attribute is authoritative in on-premises Active Directory, it must generally be changed at its source and synchronized to Microsoft Entra ID. This is a troubleshooting finding, not a successful update.

22. **`22-Recorded-Cloud-Only-User-Attribute-Baseline.png`**
    - **Action:** Recorded the starting attributes of a cloud-only user for comparison.
    - **What it shows:** The user's attribute values before the additional update.
    - **Why it matters:** Provides a baseline for checking the effect of a subsequent Graph update.

23. **`23-Ran-Graph-Attribute-Update.png`**
    - **Action:** Executed the additional Microsoft Graph attribute-update command.
    - **What it shows:** The command used to modify the cloud-only user's profile data.
    - **Why it matters:** Demonstrates the write operation in the Graph workflow and complements the baseline and verification screenshots.

24. **`24-Verified-Graph-Attribute-Update.png`**
    - **Action:** Queried the account after the additional update.
    - **What it shows:** The resulting attribute values returned by Microsoft Graph.
    - **Why it matters:** Confirms the final state and closes the update workflow with verification.

### Deleted-user recovery and licensing review

25. **`25-Verified-Lami-in-Deleted-Users.png`**
    - **Action:** Deleted the Lami test account and opened the Deleted users area.
    - **What it shows:** Lami listed among deleted users.
    - **Why it matters:** Demonstrates the soft-delete stage and shows where an administrator can locate an account before permanent deletion.

26. **`26-Restored-Lami-to-All-Users.png`**
    - **Action:** Restored Lami from Deleted users.
    - **What it shows:** Lami returned to the active All users list.
    - **Why it matters:** Demonstrates account recovery and verifies that the user object can be restored rather than recreated from scratch.

27. **`27-Reviewed-Windows-Enterprise-E3-Licence-Selection.png`**
    - **Action:** Reviewed the available Windows Enterprise E3 licence selection as part of the licensing exercise.
    - **What it shows:** The relevant licence-selection panel.
    - **Why it matters:** Provides context for the licence option being reviewed. It should not be interpreted as proof of a completed assignment unless the visible status explicitly confirms one.

28. **`28-Selected-Lami-for-Licence-Assignment.png`**
    - **Action:** Selected Lami as the user in the licence-assignment workflow.
    - **What it shows:** Lami selected in the assignment interface.
    - **Why it matters:** Identifies the correct test account used for this licensing step and distinguishes it from the separate Samuel Graph PowerShell exercise.

29. **`29-Reviewed-Tenant-Licence-Overview.png`**
    - **Action:** Reviewed the tenant's licence overview.
    - **What it shows:** The tenant-level licence inventory and assignment information visible in the portal.
    - **Why it matters:** Gives administrative context about available and assigned licences. The overview is supporting evidence and should not be treated as proof of a specific user's assignment unless that user's assignment status is shown.

## Overall skills demonstrated

- Creating and managing Microsoft Entra user identities.
- Assigning and removing directory roles and validating the effect on user capabilities.
- Applying least-privilege principles through role-based access control.
- Preparing CSV-based bulk provisioning and checking the result in audit logs.
- Authenticating to Microsoft Graph PowerShell, inspecting delegated scopes, querying users, creating accounts, and updating profile attributes.
- Verifying changes with read-after-write checks.
- Understanding the source-of-authority limitation for directory-synchronized identities in a hybrid environment.
- Recovering a soft-deleted user and reviewing licence assignment workflows.

## Evidence and security notes

- The screenshot showing a plaintext temporary password was intentionally excluded. Never commit passwords, access tokens, client secrets, recovery codes, or other credentials.
- Review screenshots for personal information, tenant identifiers, and email addresses before sharing the repository publicly. Redact details that are not necessary to demonstrate the task.
- Do not upload a source CSV containing initial passwords.
- The licensing screenshots relate to Lami. The unrelated Samuel licence-panel screenshot was excluded.
- Screenshots document the visible actions and outcomes. Where an item is described as a review or troubleshooting observation, it should not be interpreted as proof of a successful assignment or update.
