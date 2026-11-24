# Lab 09 – Enable Microsoft Entra Self-Service Password Reset (SSPR)

**Module:** Authentication and Access  
**Status:** Completed – adapted hands-on implementation  
**Test identity:** Lami (`lami@fikayo.onmicrosoft.com`)  
**Additional group member:** Jones

## Objective
Configure scoped SSPR, validate the selected security-group scope, and test an end-user password reset.

## Implementation performed
1. Created a cloud-based **Security** group named `self service reset password` with assigned membership.
2. Added Lami and Jones as direct members.
3. Opened Microsoft Entra **Password reset > Properties**.
4. Set **Self service password reset enabled** to **Selected** and selected the group.
5. Saved the policy and confirmed the successful-save notification.
6. Reviewed Lami's Security info page. It showed a password method and Microsoft Authenticator push notification registered on an iPhone 14 Pro Max.
7. Opened the Microsoft password reset portal and submitted Lami's username.
8. Completed the verification flow, entered and confirmed a new password, and received **Your password has been reset**.
9. Signed in to the Azure portal as Lami after the reset; the portal home page loaded under Lami's account.

## Validation results

| Test | Observed result |
|---|---|
| SSPR scope | Selected security group displayed in the policy |
| Policy save | Portal showed “Password reset policy saved” |
| Verification flow | Advanced to the new-password form |
| Password reset | Portal confirmed “Your password has been reset” |
| Post-reset sign-in | Azure portal home page loaded as Lami |

## Important observations and limitations
- SSPR was scoped to the selected security group, not enabled tenant-wide.
- Lami and Jones were the two direct group members shown in the evidence. Only Lami's reset was tested.
- Lami's registered Authenticator method was visible in Security info. The screenshots do not conclusively identify which verification factor was used during the reset flow.
- This is an adapted hands-on implementation using the tenant's existing test identity, not a verbatim recreation of every Microsoft Learning sample task.
- The post-reset Azure portal sign-in validates the new credential, but does not test every SSPR setting or notification behavior.

## Troubleshooting and lessons learned
- Enabling SSPR does not automatically force a password change. A user initiates a reset at [passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com/).
- A registered sign-in method alone does not prove SSPR works; the reset portal and subsequent sign-in were both tested.
- Policy save, reset completion, and post-reset sign-in were captured as separate validation points.

## Evidence
See the `screenshots/` directory and its evidence index. Review and redact screenshots before public sharing; do not publish passwords, recovery codes, tokens, or unnecessary personal information.

## Completion checklist
- [x] Create security group
- [x] Add test users to group
- [x] Configure selected-group SSPR scope
- [x] Save SSPR policy
- [x] Review test user's registered security information
- [x] Complete an SSPR password reset
- [x] Verify post-reset sign-in
- [x] Capture evidence and document limitations
