# Project – Privileged Role Assignment and User Lifecycle Management

**Project area:** Microsoft Entra ID identity and access management  
**Implementation status:** Completed  
**Environment:** Non-production Microsoft 365 / Microsoft Entra tenant

## Project overview

This implementation demonstrates how directory roles affect administrative capabilities, how elevated access can be removed, and how user lifecycle operations can be performed through the Microsoft Entra admin center, bulk CSV provisioning, and Microsoft Graph PowerShell.

The work also examines auditability, delegated Graph permissions, attribute source of authority in a hybrid identity environment, deleted-user recovery, and licence administration.

## Implementation

### 1. Role-based access control and least privilege

- Created the test identity **Lami** and completed the initial sign-in process.
- Recorded the account's baseline application-creation permissions before role assignment.
- Assigned the **Application Administrator** directory role to Lami.
- Signed in as the test user and verified that the application-creation option became available.
- Removed the Application Administrator role and rechecked the experience.
- Verified that the application-creation restriction returned after role removal.

**Outcome:** The before-and-after checks demonstrated that the directory role changed the user's administrative capability and that removing the role withdrew that elevated access. No unnecessary application was created.

### 2. Bulk user provisioning and audit verification

- Prepared a CSV file for bulk user creation.
- Corrected an invalid UPN domain encountered during the initial import attempt.
- Submitted the corrected bulk operation successfully.
- Reviewed Microsoft Entra audit logs and verified the corresponding user-add events.

**Outcome:** Bulk provisioning completed successfully, and the directory audit trail provided independent evidence of the user creation activity.

### 3. Microsoft Graph PowerShell administration

- Installed and verified the Microsoft Graph PowerShell SDK.
- Authenticated to Microsoft Graph using delegated permissions.
- Queried directory users and verified the active Graph context.
- Created the cloud-only test identity **Samuel Adeyemi** through Microsoft Graph PowerShell.
- Updated user profile attributes, including department and job title.
- Queried the user again and verified the resulting attribute values.

**Outcome:** The Graph workflow demonstrated directory read, create, and update operations, with read-after-write verification of the profile changes.

### 4. Hybrid identity source-of-authority investigation

- Investigated an attribute update against directory-synchronized user objects.
- The update was rejected because the relevant attributes are mastered on-premises.
- No changes were made to those synchronized accounts.

**Outcome:** Confirmed the source-of-authority boundary for synchronized identities: attributes mastered in on-premises Active Directory must be changed at their authoritative source and then synchronized to Microsoft Entra ID.

### 5. Deleted-user recovery

- Deleted the Lami test identity.
- Located the account in **Deleted users**.
- Restored the account and verified that it returned to **All users**.

**Outcome:** The soft-delete and restore workflow was completed and verified.

### 6. Licence administration review

- Reviewed the tenant's licence inventory and the Windows Enterprise E3 licence-selection workflow.
- Selected Lami in the user licence-assignment interface and reviewed the available tenant licence information.
- The exact licence assignment was not independently confirmed in the available evidence.

**Outcome:** The licence workflow and available licence information were reviewed. This project does not claim a completed Windows Enterprise E3 assignment.

## Validation summary

| Area | Result | Evidence |
|---|---|---|
| Test identity and baseline permissions | **Verified** | Lami profile and pre-role application-creation restriction |
| Application Administrator assignment | **Verified** | Role assignment and application-creation availability |
| Role removal | **Verified** | Role removal and restored restriction |
| Bulk CSV provisioning | **Verified** | Successful import and audit-log user-add events |
| Microsoft Graph authentication and queries | **Verified** | Graph connection, context, and user query |
| Graph user creation | **Verified** | Samuel Adeyemi created and visible in the directory |
| Graph profile updates | **Verified** | Department and job-title values confirmed after update |
| Synchronized identity attribute limitation | **Investigated** | Rejected update documented; no synchronized account changed |
| Deleted-user recovery | **Verified** | Lami restored to All users |
| Windows Enterprise E3 assignment | **Reviewed, not confirmed** | Licence-selection and tenant inventory screenshots |

## Technical findings

- **Least privilege:** Administrative capability changed when Application Administrator was assigned and reverted when the role was removed.
- **CSV validation:** An invalid UPN domain prevented the initial import; correcting the domain allowed the bulk operation to complete.
- **Auditability:** Audit logs supplied evidence of the bulk user-add events.
- **Graph delegated permissions:** Microsoft Graph operations ran within an authenticated delegated session, bounded by the granted scopes and signed-in administrator's permissions.
- **Read-after-write verification:** Re-querying the user confirmed the profile attributes were saved.
- **Hybrid identity:** Directory-synchronized attributes are controlled by their on-premises source of authority.
- **Licence assignment:** Licence availability and selection were reviewed, but the evidence does not establish a completed Windows Enterprise E3 assignment.

## Evidence

The screenshot evidence guide contains 29 entries in workflow order. Each entry explains the action performed, what the screenshot demonstrates, and why the evidence matters.

See [screenshots/README.md](./screenshots/README.md).

Screenshots containing plaintext temporary passwords were excluded. Review all evidence for personal information, tenant identifiers, email addresses, and other sensitive values before public release. Do not publish source CSV files containing passwords.

## Completion

**Status: Completed.** The role assignment and removal, bulk provisioning, Microsoft Graph operations, synchronized-identity limitation investigation, and deleted-user recovery were completed and documented. The licence-selection workflow was reviewed, but a completed Windows Enterprise E3 assignment is not claimed.
