# Lab 12 – Microsoft Entra Smart Lockout Evidence

Evidence screenshots captured during the Lab 12 hands-on test.

1. `01-Smart-Lockout-Password-Protection-Settings.png` – threshold 5, duration 120 seconds, Enforced mode.
2. `02-Lami-Temporary-Lockout-Message.png` – temporary lockout message shown during sign-in.
3. `03-Lami-Post-Lockout-Entra-Portal-Access.png` – subsequent access to the Entra admin center.
4. `04-Lami-Interactive-Sign-In-Events.png` – interactive sign-in events showing failed attempts and a later success.
5. `05-Lami-Sign-In-Failure-Error-50053-Details.png` – failure details show error 50053 and an account-locked reason.

Note: Error 50053 can also be returned for malicious IP activity. The event details support an account-lockout finding but do not, by themselves, prove the exact trigger mechanism.
