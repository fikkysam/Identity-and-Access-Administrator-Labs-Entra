# Lab 06 — Google External Identity Provider Federation

**Module:** Identity Management  
**Implementation status:** Implemented and validated  
**Evidence status:** Screenshot package prepared; repository publication pending

## Objective

Configure Google as an external identity provider in Microsoft Entra ID, invite a Google account as a B2B guest, and validate that the guest can authenticate through Google federation.

## Environment and components

- Microsoft Entra tenant: `fikayo.onmicrosoft.com`
- External identity provider: Google
- Google Cloud project: `IAM-Lab6-Google-Federation`
- OAuth client type: Web application
- Test identity: an external Gmail account
- Validation surfaces: Entra guest user record, sign-in identifiers, sign-in logs, and authentication details

No client secret, password, access token, or recovery code is included in this documentation.

## Implementation summary

### 1. Google OAuth application

- Created a Google Cloud project for the federation integration and configured the Google Auth Platform branding and OAuth client.
- Created a Web application OAuth client.
- Added the Microsoft sign-in origin `https://microsoftonline.com`.
- Configured the three Microsoft Entra redirect URIs:
  - `https://login.microsoftonline.com`
  - `https://login.microsoftonline.com/te/afde456b-8877-41b2-89b8-7e0da32e0125/oauth2/authresp`
  - `https://login.microsoftonline.com/te/fikayo.onmicrosoft.com/oauth2/authresp`
- Saved the OAuth client ID and client secret for use in Entra. The secret is intentionally not recorded here.
- Completed the Google branding/consent configuration.

### 2. Microsoft Entra federation

- Opened **External Identities → All identity providers → Built-in → Google**.
- Entered the Google OAuth client ID and client secret and saved the provider configuration.
- Confirmed that Google appeared with a green status indicator and the status **Configured**.

### 3. Guest invitation and redemption

- Created an Entra B2B guest invitation for the external Gmail identity.
- Located the Microsoft invitation in Gmail. It was initially delivered to Spam, so it was reported as **Not spam** and then opened from All Mail.
- Followed **Accept invitation** and completed the Google sign-in/consent sequence.
- Accepted the Microsoft permissions prompt for profile and activity data.
- Confirmed the guest record showed **Invitation state: Accepted**.

### 4. Authentication validation

- Re-ran the authentication test through the external identity provider flow.
- Confirmed the guest's sign-in identifiers included a federated sign-in type with issuer `google.com`.
- Confirmed a successful Entra sign-in event.
- In **Authentication Details**, the method was recorded as **Previously satisfied** and **Succeeded = true**; the result detail indicated the first-factor requirement was satisfied.
- Confirmed the Google provider remained **Configured** in the Entra provider list.

The My Apps dashboard displayed no applications. This is consistent with the guest not having any enterprise applications assigned; it did not invalidate the successful authentication result.

## Troubleshooting and resolutions

### Google test-user account reported as ineligible

**Observed:** Google Cloud displayed an “Ineligible accounts not added” message for the initially entered test-user address.

**Action:** Rechecked the Google account being used for the federation test and continued the test with the external Google identity that completed the invitation and sign-in flow. The rejected address was not treated as a successfully added test user.

### Invitation email delivered to Spam

**Observed:** The Microsoft invitation from `invites@fikayo.onmicrosoft.com` appeared in Gmail Spam.

**Resolution:** Reviewed the sender and organization details, selected **Report not spam**, opened the message from All Mail, and used its **Accept invitation** link.

### Gmail address was not recognized by the Microsoft username/password page

**Observed:** Entering the Gmail address directly into the standard Microsoft sign-in username field returned “We couldn't find an account with that username.”

**Cause:** The Gmail identity is an external federated identity, not a native Microsoft account in the tenant. Typing it into the ordinary Microsoft account lookup does not itself initiate Google federation.

**Resolution:** Started from the Entra guest invitation redemption / organization federation flow and selected the Google account when the identity-provider flow presented the account picker. The later Entra sign-in log confirmed the federated issuer as `google.com`.

### Initial sign-in event returned error 500141

**Observed:** An early sign-in event showed error code `500141` with the message that redemption was complete but the request was not initiated by the target application.

**Investigation and resolution:** Reviewed the guest's sign-in history and the invitation flow rather than treating the first failed event as proof of a completed sign-in. Reinitiated the authentication through the intended invitation/federation flow and checked the subsequent sign-in event. The later event recorded **Success**, and Authentication Details showed the first-factor requirement as previously satisfied and successful.

### My Apps dashboard showed no applications

**Observed:** After invitation redemption, the My Apps dashboard displayed “There are no apps to show.”

**Interpretation:** No enterprise applications had been assigned to this guest. The empty application list was not an authentication failure. Federation was validated separately using the guest's accepted invitation state, federated sign-in identifier, and successful Entra sign-in log.

## Validation results

| Validation | Result |
|---|---|
| Google OAuth web client created | Successful |
| Three Microsoft Entra redirect URIs configured | Successful |
| Google provider credentials saved in Entra | Successful |
| Google identity provider status | Configured |
| B2B guest invitation | Accepted |
| Federated issuer in sign-in identifiers | `google.com` |
| Entra sign-in event | Success |
| Authentication Details | First-factor requirement previously satisfied; succeeded = true |

## Evidence

The ordered screenshot package and per-image explanations are in [`screenshots/`](./screenshots/). See [`screenshots/README.md`](./screenshots/README.md) for the evidence index.

## Security considerations

- The OAuth client secret is not included in the repository documentation or evidence index.
- Do not commit secrets, passwords, tokens, or recovery codes.
- Review and redact personal identifiers from screenshots before publishing them in a public repository.
- Use a non-production tenant and dedicated test identities for federation testing.

## Completion state

Implementation and authentication validation are complete. The evidence archive is prepared for upload to the repository. The progress tracker should remain at **Validated** until the screenshots are published in the Lab 06 `screenshots/` directory.
