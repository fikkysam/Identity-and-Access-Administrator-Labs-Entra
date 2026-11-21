# Repository Architecture

## Purpose

This repository organizes a 28-lab Microsoft Entra ID / SC-300 practical learning portfolio. It is a standalone project and does not contain or replace the separate Conditional Access policy repository.

## Logical learning domains

```text
Microsoft Entra ID – Identity and Access Administrator
|
+-- Module 01: Identity Management (Labs 01–07)
|   +-- Directory roles and tenant configuration
|   +-- Group-based licensing, assigned groups, and dynamic membership
|   +-- External collaboration and guest access controls
|   +-- Guest identities, federation, hybrid identity
|
+-- Module 02: Authentication and Access (Labs 08–16)
|   +-- MFA, SSPR, VM authentication
|   +-- Privileged Azure resource roles
|   +-- Smart lockout, Conditional Access, risk policies
|   +-- Authentication registration and managed identities
|
+-- Module 03: Application Access (Labs 17–21)
|   +-- Defender for Cloud Apps
|   +-- Application registration and access
|   +-- Tenant-wide admin consent
|
+-- Module 04: Identity Governance (Labs 22–28)
    +-- Entitlement management and Terms of Use
    +-- External identity lifecycle and access reviews
    +-- PIM for Entra roles
    +-- Sentinel KQL and Identity Secure Score
```

## Lab evidence workflow

```text
Official Microsoft lab instructions
            |
            v
Review prerequisites and licensing
            |
            v
Implement in a controlled test environment
            |
            v
Validate expected behavior and record validation boundaries
            |
            v
Capture and redact evidence
            |
            v
Document implementation, security implications, and findings
            |
            v
Publish evidence and update lab status
```

## Standard lab folder

Each lab should use a consistent structure:

```text
Lab-XX-Short-Name/
|-- README.md
|-- screenshots/
|   \-- README.md       (evidence index and screenshot descriptions)
|-- notes/
|-- scripts/            (only when applicable)
\-- evidence/           (only when applicable)
```

Not every lab needs scripts or separate notes. Add only artifacts that were actually used. Screenshot indexes explain what each image proves; image files must be redacted before publication.

## Environment and security boundaries

- Prefer a dedicated non-production Microsoft Entra tenant and test identities.
- Confirm required Entra ID, Microsoft 365, Azure, and Defender licensing before implementation.
- Keep emergency access accounts protected and excluded from disruptive test policies where appropriate.
- Never publish credentials, secrets, tokens, recovery codes, or sensitive personal/tenant data.
- Redact administrator identities, tenant identifiers, domains, usernames, IP addresses, and other identifying details when disclosure is not necessary.

## Documentation principles

- Distinguish planned work from attempted, implemented, validated, and completed work.
- Record actual outcomes; do not claim a feature worked unless tested.
- Clearly distinguish configuration-state verification from end-to-end functional testing.
- Note licensing constraints, portal changes, and deviations from Microsoft instructions.
- Link each lab to its official Microsoft Learning source.
