# Lab 18 – Screenshot Evidence

These screenshots were recovered from the conversation evidence for the **Demo app** registration exercise. They document the application registration and custom-role tasks.

| File | Evidence |
|---|---|
| `01-demo-app-registration.png` | New application registration form for **Demo app** |
| `02-demo-app-overview.png` | Registered **Demo app** overview |
| `03-web-redirect-uri-configured.png` | Web platform redirect URI `https://localhost` |
| `04-client-secret-creation-settings.png` | Client-secret settings, including the 90-day lifetime |
| `05-client-secret-created-REDACTED.png` | Client secret created; secret Value is redacted |
| `06-api-scopes-configured.png` | Expose an API page showing both enabled delegated scopes |
| `07-custom-role-permissions-selected.png` | The two selected custom-role permissions |
| `08-custom-role-review.png` | Review page for **My custom app role** |
| `09-custom-role-created.png` | Custom role visible in Microsoft Entra ID roles |

## Security review

- The client-secret **Value** is fully obscured in screenshot 05.
- Do not publish the actual secret value, passwords, access tokens, or recovery codes.
- The screenshots are evidence of the portal configuration; they do not imply that the secret should be retained or used in production.
