# Lab 06 — Screenshot Evidence

This directory contains the 15 selected screenshots for the Google external identity provider federation lab.

## Evidence index

| File | What it demonstrates |
|---|---|
| 01-google-cloud-project.png | Google Cloud project used for the federation integration. |
| 02-google-oauth-redirect-uri-configuration.png | OAuth web client and Microsoft Entra redirect URI configuration. |
| 03-entra-google-provider-credentials.png | Google OAuth client credentials entered in the Entra Google identity-provider configuration. |
| 04-entra-google-guest-user-record.png | Entra B2B guest user record created for the external Google identity. |
| 05-google-invitation-delivered-to-spam.png | Microsoft B2B invitation received in Gmail Spam. |
| 06-microsoft-b2b-invitation-acceptance-link.png | Invitation email and the Accept invitation action. |
| 07-microsoft-consent-prompt.png | Microsoft permissions/consent prompt presented during redemption. |
| 08-google-account-selected.png | Google identity selected during the federated sign-in flow. |
| 09-b2b-invitation-accepted.png | Entra guest record showing the invitation was accepted. |
| 10-initial-signin-failure-error-500141.png | Initial failed sign-in event and error 500141 investigated during troubleshooting. |
| 11-microsoft-username-lookup-failure.png | Standard Microsoft username lookup did not recognize the Gmail address as a native Microsoft account. |
| 12-federated-issuer-google-com.png | Entra sign-in identifiers showing the federated issuer as google.com. |
| 13-successful-federated-signin.png | Successful Entra sign-in event for the guest identity. |
| 14-authentication-details-success.png | Authentication Details showing the first-factor requirement was previously satisfied and succeeded. |
| 15-google-provider-configured.png | Entra identity-provider list showing Google with status Configured. |

## Publication and security notes

- These screenshots are selected to show configuration, guest invitation and redemption, troubleshooting, and successful validation without unnecessary duplicates.
- Review screenshots for personal email addresses and other identifiers before publishing to a public repository.
- Never publish OAuth client secrets, passwords, access tokens, or recovery codes.

