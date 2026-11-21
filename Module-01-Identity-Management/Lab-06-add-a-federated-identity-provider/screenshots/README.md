# Lab 06 — Google Federation Evidence Index

This folder contains 15 selected screenshots documenting the Google external identity provider implementation, guest invitation redemption, troubleshooting, and successful federated sign-in validation. The selection removes repetitive setup captures while retaining the key implementation and diagnostic evidence.

## Evidence index

| File | What it demonstrates |
|---|---|
| `01-google-cloud-project.png` | Google Cloud project used for the federation setup. |
| `02-google-oauth-redirect-uri-configuration.png` | Google OAuth web client redirect URI configuration. |
| `03-entra-google-provider-credentials.png` | Google OAuth client ID and secret entered in Microsoft Entra. |
| `04-entra-google-guest-user-record.png` | Entra guest user record created for the external Google identity. |
| `05-google-invitation-delivered-to-spam.png` | Google invitation email initially delivered to Gmail Spam. |
| `06-microsoft-b2b-invitation-acceptance-link.png` | Microsoft B2B invitation email and acceptance link. |
| `07-microsoft-consent-prompt.png` | Microsoft permissions and consent prompt during invitation redemption. |
| `08-google-account-selected.png` | Google guest account selected in the Microsoft sign-in flow. |
| `09-b2b-invitation-accepted.png` | Entra guest record showing the B2B invitation was accepted. |
| `10-initial-signin-failure-error-500141.png` | Initial failed sign-in and error 500141 details. |
| `11-microsoft-username-lookup-failure.png` | Direct Microsoft username lookup failure for the Gmail address. |
| `12-federated-issuer-google-com.png` | Entra sign-in identifiers showing google.com as the federated issuer. |
| `13-successful-federated-signin.png` | Successful Entra sign-in event for the Google guest. |
| `14-authentication-details-success.png` | Authentication details showing the first-factor requirement succeeded. |
| `15-google-provider-configured.png` | Final Entra identity provider list showing Google as Configured. |

## Upload location

`Module-01-Identity-Management/Lab-06-add-a-federated-identity-provider/screenshots/`

## Security review

Before publishing this folder, inspect each image for personal identifiers and ensure no passwords, client secrets, access tokens, or other credentials are exposed. The selected screenshots are intended as portfolio evidence; do not publish unmasked secrets.
