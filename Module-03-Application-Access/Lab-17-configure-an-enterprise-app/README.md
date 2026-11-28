# Lab 17 – Configure an Enterprise App

**Module:** 03 – Application Access  
**Status:** Completed  
**Application:** GitHub Enterprise Cloud – Enterprise Account  
**Identity provider:** Microsoft Entra ID  
**Protocol:** SAML 2.0

## Objective

Configure an enterprise application in Microsoft Entra ID, assign a permitted user, establish SAML trust with GitHub Enterprise Cloud, and validate SAML single sign-on.

## Exercise 1 – Configure an enterprise app

### Task 1 – Add GitHub Enterprise Cloud to the Entra tenant

- Opened **Entra ID → Enterprise apps → New application**.
- Searched the Microsoft Entra gallery for **GitHub**.
- Selected **GitHub Enterprise Cloud – Enterprise Account** and created the enterprise application.
- The application was created in the Entra tenant and its enterprise application management page was opened.

### Task 2 – Assign a user to the application

- Opened **Users and groups** for the enterprise application.
- Assigned **Debbie O** to the application.
- This is an intentional adaptation of the source lab, which uses **Adele Vance** and a MOD administrator account as sample identities. Debbie O was used as the test identity in this tenant.
- Verified Debbie O appeared in the enterprise application's **Users and groups** assignment list.

The assignment is an application access assignment. It should not be confused with assigning a Microsoft Entra directory administrator role to Debbie O.

## Additional SAML configuration and validation

The exercise was extended to configure the GitHub Enterprise Cloud enterprise account as a SAML service provider.

### Microsoft Entra SAML configuration

Configured the following Basic SAML Configuration values:

| Setting | Configured value |
|---|---|
| Identifier (Entity ID) | `https://github.com/enterprises/oluwafikayo` |
| Reply URL (ACS) | `https://github.com/enterprises/oluwafikayo/saml/consume` |
| Sign-on URL | Left blank |
| Relay State | Left blank |
| Logout URL | Left blank in Basic SAML Configuration |

The Entra SAML signing certificate was active during validation, with an expiry date of **November 27, 2029**. The Entra **Login URL**, **Microsoft Entra Identifier**, and Base64 public certificate were copied into the GitHub Enterprise SAML configuration. The Entra logout URL was also available in the SAML setup details.

### GitHub Enterprise Cloud SAML settings

Configured GitHub Enterprise account authentication security with the Entra-provided values:

- **Sign on URL:** Microsoft Entra Login URL.
- **Issuer:** Microsoft Entra Identifier.
- **Public certificate:** Entra Base64 certificate.
- **Signature method:** RSA-SHA256.
- **Digest method:** SHA256.
- **Require SAML authentication:** enabled.

### Validation result

GitHub's SAML test returned:

**“Passed: Successfully authenticated your SAML SSO identity.”**

The GitHub Enterprise settings page subsequently showed that SAML single sign-on was enabled. The Entra **Users and groups** page also showed Debbie O assigned to the enterprise application.

## Completion checklist

- [x] Add **GitHub Enterprise Cloud – Enterprise Account** from the Entra gallery.
- [x] Create the enterprise application in the tenant.
- [x] Assign a test user to the application (Debbie O used instead of the sample Adele Vance).
- [x] Verify the user appears in **Users and groups**.
- [x] Configure the GitHub Enterprise Cloud SAML Entity ID and ACS URL in Entra.
- [x] Configure GitHub Enterprise with the Entra Login URL, issuer, and public certificate.
- [x] Validate SAML authentication successfully.
- [x] Enable SAML single sign-on in GitHub Enterprise Cloud.

## Security and evidence notes

- Never publish SAML recovery codes, private keys, client secrets, passwords, access tokens, or unredacted SAML assertions.
- The GitHub recovery-code screenshot shared during setup contained sensitive recovery codes. It must not be committed to the repository. If those codes may have been exposed, regenerate the recovery codes in GitHub and store the new set securely.
- Publish only redacted screenshots of the Entra application assignment, Entra SAML configuration, GitHub SAML configuration, successful SAML test, and enabled SAML status.
- The screenshots were reviewed in the guided conversation. The repository should contain only sanitized image files; the recovery-code screenshot is expressly excluded.

## Source

Microsoft SC-300 Identity and Access Administrator learning lab, **Configure an Enterprise App** (personal roadmap: Lab 17).