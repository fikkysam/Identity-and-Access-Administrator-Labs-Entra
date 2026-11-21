# Lab 05 — Add Guest Users to the Directory: Evidence Pack

This pack contains selected screenshots from the hands-on Lab 05 session. Personal email addresses, account identifiers, tenant identifiers, and invitation-link areas have been obscured where visible.

## Evidence index

1. **Individual guest invitation success** — Entra admin center success notification after inviting the individual guest.
2. **Audit-log invitation events** — Microsoft Entra audit log showing successful `Invite external user` operations. Identity-bearing columns are obscured.
3. **Bulk invitation CSV template** — the downloaded CSV template used to prepare the bulk guest invitation entries; identity values are obscured.
4. **Microsoft Graph module installed** — PowerShell confirms Microsoft.Graph module version 2.40.0 from PSGallery.
5. **Graph authentication context** — delegated Microsoft Graph context and PowerShell version; account and tenant identifiers are obscured.
6. **Graph invitation parameters** — the Microsoft Graph invitation setup; external email addresses and tenant/account identifiers are obscured. This is parameter preparation evidence, not the command result.
7. **Guest invitation email** — evidence that the PowerShell-created guest invitation email was received. Personal details and actionable invitation links are obscured.
8. **Guest account accepted** — Entra user overview showing User type `Guest`, Creation type `Invitation`, Invitation state `Accepted`, and Account enabled `Yes`; personal identifiers are obscured.

## Validation boundary

The screenshots support the individual invitation success, bulk invitation audit events, Graph module installation and delegated authentication, invitation email delivery, and accepted guest state. The PowerShell command output containing the generated invitation ID and redemption URL is intentionally not included because redemption URLs are sensitive. Bulk guest redemption is not claimed; the accepted state shown is for the PowerShell-created guest.

## Handling

Keep invitation redemption URLs, credentials, access tokens, and unredacted personal or tenant identifiers out of public repositories. Review each image before publishing.


## Additional evidence — bulk invitation result details

9. `09-bulk-invitation-per-recipient-results-redacted.png` — downloaded bulk-operation result CSV opened in Excel. Both invitation rows show `Success`; external identifiers in the ObjectId column are redacted. This verifies two successful invitation records and no failed rows in this result file.


## Additional evidence

10. `10-powershell-invitation-execution-redacted.png` — Microsoft Graph `New-MgInvitation` execution output showing the returned invitation ID. The external email address and redemption URL are obscured.
