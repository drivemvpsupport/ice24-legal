# Drive MVP Privacy Policy

**Effective date:** 2026-06-06
**Last updated:** 2026-06-06

## 1. Who we are

**Drive MVP** ("we", "us", "our") operates the Drive MVP mobile application (the
"App"), a workforce platform for independent contractor drivers performing
on-demand delivery and trip work.

- **Company / legal entity:** ICE24, LLC
- **Registered address:** 12469 Saddlebrook Lane, Strongsville, OH 44149, United States
- **Contact email for privacy:** DriveMVPSupport@gmail.com
- **Data controller:** the entity above acts as the controller of personal data
  collected through the App.

## 2. Scope

This policy describes what personal data the App collects, why we collect it,
how we use it, who we share it with, how long we keep it, and your rights. It
covers the iOS and Android versions of the App and the Azure-hosted backend
services that support it. It does **not** cover any third-party app, website,
or service you reach from a link inside the App.

## 3. Data we collect

| Category | Specific data | Source | Why we collect it |
|---|---|---|---|
| **Identifiers** | Microsoft Entra External ID Object ID (OID, a GUID); the email address you sign up with | You, via Microsoft Entra External ID sign-in | To create and authenticate your account, link records together, and contact you about your account |
| **Profile data** | First name, last name, phone number, driver type, vehicle details, and other fields you choose to enter on the profile screen | You, via the in-app profile editor | To populate your profile, customize the App, and meet contractor onboarding requirements |
| **Precise location** | GPS coordinates, speed, heading, and motion sensor readings collected continuously while a trip is in progress, including in the background | Your device, via the DriveQuant DriveKit SDK | To analyze trips, score driving behavior (distraction, eco, safety), compute trip distance and duration, and provide telematics features that are core to the App |
| **Photos** | Photos of delivered packages or vehicle conditions that you choose to capture inside the App | You, via the in-app camera | To attach photographic proof of delivery or condition to a trip record |
| **Device & diagnostics** | App version, OS version, device model, anonymized device identifier, crash stack traces, performance traces, structured event logs | Your device automatically, via Microsoft Application Insights | To diagnose crashes, measure reliability, and improve the App |
| **Account-recovery / abuse signals** | Rate-limit counters, failed-login events | Your interactions with our backend | To prevent abuse and protect the service |

We **do not** knowingly collect:

- Payment card numbers (we do not process payments in this App).
- Biometric data.
- Data from children under 13 (the App is intended for adult contractor drivers
  only; see Section 11).
- Any "sensitive personal information" as that term is used in the
  California Consumer Privacy Act ("CCPA"), beyond precise geolocation
  disclosed above.

## 4. How we use your data

We use the data described in Section 3 to:

1. **Provide the App.** Authenticate you, sync your profile, record trips,
   capture and store delivery photos, and display your history.
2. **Compute telematics.** Convert raw sensor and GPS data into trip summaries
   and driving-behavior scores via DriveQuant DriveKit.
3. **Operate and secure the service.** Rate-limit abusive traffic, prevent
   account takeover, investigate suspicious activity.
4. **Improve the App.** Diagnose crashes, measure feature reliability, and
   prioritize fixes. We do **not** use telematics data for advertising or sell
   it to data brokers.
5. **Communicate with you.** Send account-related emails (password reset,
   security alerts, material changes to this policy). We do not send marketing
   email from this App as of v1.

**Legal bases (EEA / UK users).** Where the EU GDPR or UK GDPR applies, our
legal bases are:

- **Performance of a contract** (Art. 6(1)(b)) — for processing required to
  deliver core App functionality (authentication, profile, trips, photos).
- **Legitimate interests** (Art. 6(1)(f)) — for service security, abuse
  prevention, and crash diagnostics. You can object; see Section 10.
- **Consent** (Art. 6(1)(a)) — for background location collection, which the
  operating system asks you to grant explicitly before DriveKit can record.

## 5. Background location, in detail

Because telematics is the core of the App and is sensitive, this section
spells out the background-location flow precisely:

- The App requests **"While Using"** location permission first. On Android the
  manifest also declares `ACCESS_BACKGROUND_LOCATION` so trips can continue
  after you switch apps or lock the screen.
- On iOS the App declares `NSLocationAlwaysAndWhenInUseUsageDescription` so
  iOS displays the "Always Allow" upgrade prompt.
- Location collection is **performed by DriveQuant SAS** through their
  DriveKit SDK embedded in the App. DriveQuant is a third-party processor;
  see Section 6.
- You can stop location collection at any time by revoking the App's location
  permission in your device's OS settings. Doing so will disable trip
  recording but will not delete previously recorded trips.

## 6. Third parties we share data with

We share data only with the third parties below, and only the data they need
to perform their function. None of them are paid by us to advertise to you.

| Third party | Purpose | Data shared | Region |
|---|---|---|---|
| **Microsoft Corporation** — Azure (storage, compute, monitoring) and Microsoft Entra External ID (authentication) | App backend hosting, authentication, crash and event analytics (Application Insights) | All categories listed in Section 3 | United States |
| **DriveQuant SAS** — DriveKit SDK | Trip recording, sensor processing, driving-behavior scoring | Identifiers (OID), precise location, motion sensor data, trip metadata | European Union (France) |
| **Apple Inc.** | App distribution via the App Store and TestFlight; crash reporting via Xcode Organizer if you opt in at the OS level | App identifiers, OS-collected crash logs | United States |
| **Google LLC** | App distribution via Google Play; map tiles and place lookup via Maps Platform | App identifiers, queried map locations | United States |

We do **not** sell or share your personal data for cross-context behavioral
advertising as those terms are defined under the CCPA / CPRA.

We may disclose information when required by law (subpoena, court order,
or comparable legal process), or to protect the rights, property, or safety
of Drive MVP, our users, or the public.

## 7. International data transfers

The App is operated from the United States. If you access the App from outside
the United States, you understand that your data will be transferred to, and
processed in, the United States and (for DriveQuant) the European Union. Where
required by EU GDPR, transfers from the EEA to the United States rely on the
EU–US Data Privacy Framework and Standard Contractual Clauses.

## 8. How long we keep your data

- **Account data, profile data, trip summaries:** for as long as your account
  is active, and for up to **24 months** after account closure to satisfy
  legal and audit obligations. After that, we delete or aggregate-anonymize.
- **Raw GPS and sensor data inside DriveKit's cloud:** retained per DriveQuant's
  retention policy (typically 12 months after collection); their policy lives
  at https://www.drivequant.com/en/privacy-policy.
- **Crash stack traces and diagnostic logs:** retained in Application Insights
  for **90 days**.
- **Delivery photos:** retained for **12 months** then deleted unless
  flagged for a dispute.

## 9. How we protect your data

- **In transit:** all App ↔ backend traffic uses TLS 1.2 or higher. The Android
  build trusts only the system CA store for our endpoints.
- **At rest:** Azure Storage data is encrypted at rest (AES-256) with
  Microsoft-managed keys.
- **Access control:** backend functions enforce per-user authorization on every
  call. All storage paths are keyed on your immutable Entra OID; one user
  cannot read or write another user's data.
- **Secret hygiene:** we do not embed long-lived backend secrets in the App.
  The App authenticates with short-lived OAuth tokens issued by Microsoft Entra
  External ID. Release signing keys and backend secrets are stored in Azure
  Key Vault.
- No system is perfectly secure. If we become aware of a breach affecting
  your data, we will notify you within the time required by applicable law.

## 10. Your rights and choices

Depending on where you live, you may have some or all of the following
rights with respect to your personal data:

- **Access** — request a copy of the data we hold about you.
- **Correction** — ask us to correct inaccurate data. You can correct most
  profile fields directly inside the App.
- **Deletion** — ask us to delete your account and personal data. We will
  honor the request unless we are required to retain data for a legal or
  audit purpose. Trip data inside DriveKit's cloud is deleted separately;
  we will trigger that deletion on your behalf.
- **Portability** — receive your data in a machine-readable format.
- **Objection / restriction** — ask us to stop or limit certain processing
  based on legitimate interest.
- **Withdraw consent** — revoke OS-level location permission at any time.

To exercise any of these rights, email **DriveMVPSupport@gmail.com** from
the address associated with your account. We will respond within 30 days, or
sooner where required by law (15 business days in California).

**Account deletion in the App.** You can also request deletion in-app from
*Profile → Settings → Delete my account* (or, while that flow is being
finalized, by emailing the address above). Deletion takes effect within 30
days.

**California residents (CCPA / CPRA).** In addition to the rights above, you
have the right to know what personal information we collect, the right to
delete, the right to correct, and the right to non-discrimination for
exercising these rights. We do not "sell" or "share" personal information for
cross-context behavioral advertising.

**EEA / UK residents (GDPR).** You also have the right to lodge a complaint
with your local data-protection authority.

## 11. Children

The App is **not directed to children under 13**, and not intended for use by
anyone under 18. We do not knowingly collect personal data from children. If
you believe a child has provided us with personal data, contact us at
DriveMVPSupport@gmail.com and we will delete it.

## 12. Changes to this policy

We may update this policy from time to time. When we do, we will update the
"Last updated" date at the top, post the new version at the same URL, and —
for material changes — notify you in-app or by email before the change takes
effect.

## 13. Contact

Questions about this policy or our data practices:

**ICE24, LLC**
12469 Saddlebrook Lane, Strongsville, OH 44149, United States
Email: **DriveMVPSupport@gmail.com**
