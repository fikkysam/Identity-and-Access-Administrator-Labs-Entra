# Lab 09 – Enable Microsoft Entra Self-Service Password Reset (SSPR)

**Module:** Authentication and Access  
**Status:** Completed – adapted hands-on implementation  
**Test identity:** Lami (cloud-only test user)  
**Security group:** `self service reset password`

## Objective

Configure Microsoft Entra self-service password reset (SSPR) for a defined security group, then validate the end-user password reset and subsequent sign-in.

## Environment and configuration

- Microsoft Entra ID tenant with a cloud-only test identity.
- A cloud-based **Security** group named `self service reset password`.
- Assigned membership with Lami and Jones as direct members.
- SSPR scope configured as **Selected**, with the security group selected.

## Implementation performed

1. Created the cloud-based **Security** group `self service reset password` with assigned membership.
2. Added Lami and Jones as direct members and verified both appeared in the group's Members list.
3. Opened Microsoft Entra **Password reset > Properties**.
4. Set **Self service password reset enabled** to **Selected** and selected the `self service reset password` group.
5. Saved the policy and confirmed the portal's successful-save notification.
6. Reviewed Lami's **Security info** page and confirmed that a password method and Microsoft Authenticator push notification were registered.
7. Opened the Microsoft password reset portal and submitted Lami's username.
8. Completed the available verification flow, entered and confirmed a new password, and received the confirmation **Your password has been reset**.
9. Signed in to the Azure portal as Lami after the reset; the Azure portal home page loaded under that account.

## Validation results

| Test | Observed result |
|---|---|
| Security group | Group created successfully |
| Group membership | Lami and Jones shown as direct members |
| SSPR scope | Policy set to **Selected** and target group displayed |
| Policy save | Portal displayed **Password reset policy saved** |
| Reset verification | Flow advanced to the new-password form |
| Password reset | Portal confirmed **Your password has been reset** |
| Post-reset sign-in | Azure portal home page loaded as Lami |

## Troubleshooting and observations

- Enabling SSPR does not automatically force a user to change their password. The user must initiate a reset through the Microsoft password reset portal.
- A registered sign-in method by itself does not prove that SSPR works. The reset flow and a subsequent sign-in were both tested.
- The policy was scoped to the selected security group; it was not enabled for every user in the tenant.
- Both Lami and Jones were group members, but only Lami's password reset was tested.
- The evidence confirms that the reset completed and that a subsequent Azure portal sign-in succeeded. It does not establish that every SSPR verification method, notification option, or password writeback scenario was tested.
- This is an adapted hands-on implementation using the tenant's existing test identity, not a verbatim recreation of every Microsoft Learning sample task.

## Security considerations

- Keep test accounts separate from production identities.
- Do not commit passwords, recovery codes, MFA codes, access tokens, client secrets, or private keys to the repository.
- Redact unnecessary personal and tenant identifiers from screenshots before publishing them publicly.
- Use least-privilege access when administering the tenant.

## Evidence

See the [screenshot evidence index](screenshots/README.md) for the nine captured validation screenshots.

## Completion checklist

- [x] Create the SSPR security group
- [x] Add test users to the group
- [x] Configure selected-group SSPR scope
- [x] Save and verify the SSPR policy
- [x] Review the test user's registered security information
- [x] Complete an SSPR password reset
- [x] Verify post-reset sign-in
- [x] Capture evidence and document test scope and limitations
