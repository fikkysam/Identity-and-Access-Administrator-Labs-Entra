# SC-300 Lab 01 — Screenshot Evidence

This folder contains the Lab 01 screenshots in **one flat folder** so they can be selected and uploaded together to GitHub. File names are numbered in workflow order and describe the action or result shown.

## Evidence index

- **`01-Created-Lami-Test-User.png`** — Created the Lami test identity in Microsoft Entra ID.
- **`02-Completed-Lami-First-Sign-In.png`** — Captured the first sign-in and password-change flow.
- **`03-Verified-Lami-User-Profile-and-Baseline.png`** — Recorded the user profile and baseline state before role elevation.
- **`04-Assigned-Application-Administrator-Role.png`** — Captured assignment of the Application Administrator role.
- **`05-Verified-Application-Creation-Access.png`** — Verified the application-creation option became available with the role.
- **`06-Removed-Application-Administrator-Role.png`** — Captured removal of the elevated role.
- **`07-Rechecked-Application-Creation-After-Role-Removal.png`** — Rechecked the application-creation panel after role removal.
- **`08-Prepared-Bulk-User-Provisioning-CSV.png`** — Prepared the CSV input for bulk user creation.
- **`09-Reviewed-Bulk-User-Provisioning-CSV.png`** — Reviewed the CSV structure before submission.
- **`10-Completed-Bulk-User-Creation.png`** — Captured the successful bulk operation result after correcting the UPN domain.
- **`11-Verified-Bulk-User-Creation-in-Audit-Logs.png`** — Verified user-add events in the audit logs.
- **`12-Verified-PowerShell-Environment.png`** — Recorded the PowerShell environment and Graph tooling.
- **`13-Verified-Microsoft-Graph-SDK-Installation.png`** — Verified Microsoft Graph PowerShell SDK installation.
- **`14-Authenticated-to-Microsoft-Graph.png`** — Captured Graph sign-in and delegated-consent flow.
- **`15-Verified-Graph-Connection-and-Queried-Users.png`** — Verified the Graph connection and queried directory users.
- **`16-Created-Samuel-Adeyemi-with-Graph.png`** — Captured the Graph PowerShell user-creation command output; plaintext-password screenshot was excluded.
- **`17-Verified-Graph-Delegated-Scopes.png`** — Recorded the delegated scopes available in the Graph session.
- **`18-Verified-Samuel-Adeyemi-Account.png`** — Verified the created user account.
- **`19-Updated-User-Department-with-Graph.png`** — Captured the department attribute update command.
- **`20-Verified-Department-Attribute-Update.png`** — Verified the updated department and job-title attributes.
- **`21-Diagnosed-Directory-Synced-User-Update-Limitation.png`** — Captured the error encountered when attempting to update directory-synced users; these attributes are mastered on-premises.
- **`22-Recorded-Cloud-Only-User-Attribute-Baseline.png`** — Recorded the cloud-only user attribute baseline for comparison.
- **`23-Ran-Graph-Attribute-Update.png`** — Captured the additional Graph attribute-update command.
- **`24-Verified-Graph-Attribute-Update.png`** — Verified the resulting attribute values.
- **`25-Verified-Lami-in-Deleted-Users.png`** — Verified Lami appeared in Deleted users after deletion.
- **`26-Restored-Lami-to-All-Users.png`** — Verified Lami was restored and appeared in All users.
- **`27-Reviewed-Windows-Enterprise-E3-Licence-Selection.png`** — Captured the relevant licence-selection panel during the licensing exercise.
- **`28-Selected-Lami-for-Licence-Assignment.png`** — Captured Lami selected in the licence-assignment panel.
- **`29-Reviewed-Tenant-Licence-Overview.png`** — Captured the tenant licence overview and assignment count.

## What the evidence demonstrates

- Created and inspected a test user, assigned and removed Application Administrator, and checked application-creation access before and after role elevation.
- Prepared and submitted a bulk user-creation CSV, then checked the operation result and audit logs.
- Installed and used Microsoft Graph PowerShell to connect, query users, create a cloud user, update attributes, and verify the resulting values.
- Recorded an optional troubleshooting result: updates to directory-synchronized users were blocked because the relevant attributes are mastered on-premises. This is documented as a limitation encountered, not as a successful update.
- Deleted and restored Lami, then verified the restored account in All users.
- Captured the relevant licensing workflow evidence for Lami and the tenant licence overview. 

## How to upload this folder to GitHub

1. Extract the ZIP archive on your computer.
2. Open the repository and navigate to the location where you want the evidence folder.
3. Create or open a folder named `Lab-01-Screenshots` (if needed, create it by adding a file with that folder path).
4. Choose **Add file → Upload files** and select all 29 PNG files plus this `README.md` from the extracted folder.
5. Commit the upload. GitHub will show the screenshots and this index together in the same folder.

## Review before making the repository public

- Review every screenshot for personal information, tenant identifiers, email addresses, and other details you do not want publicly visible; redact them where appropriate.
- The original PowerShell screenshot containing a plaintext temporary password was intentionally excluded. Do not add it.
- The CSV screenshots may expose user identifiers or other account details. Do not upload the original CSV if it contains initial passwords.
- The Lami licence-panel screenshot shows Lami selected during the licence-assignment workflow. The tenant overview is supporting context; do not infer a specific assignment status beyond what the screenshots visibly show.
- Screenshots document the visible steps and outcomes. They should not be read as proof that optional sample-specific tasks were reproduced exactly in every tenant.
