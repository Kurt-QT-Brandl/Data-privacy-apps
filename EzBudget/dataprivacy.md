# EzBudget

## Privacy Policy

**Last updated: July 25, 2026**

This document is published at [github.com/Kurt-QT-Brandl/Data-privacy-apps/ezbudget/dataprivacy.md](https://github.com/Kurt-QT-Brandl/Data-privacy-apps/blob/main/ezbudget/dataprivacy.md). A German version is available at [datenschutz-DE.md](https://github.com/Kurt-QT-Brandl/Data-privacy-apps/blob/main/ezbudget/datenschutz-DE.md).

This Privacy Policy describes how the Android app **EzBudget** (package name `com.curtisqt.ezbudget`, the "App") handles information, in accordance with the requirements of the Google Play [User Data policy](https://support.google.com/googleplay/android-developer/answer/9859455) and related Google Play Console policy topics.

## 1. Controller

The developer and person responsible for this App is:

**CurtisQT**
Email: [curtis.qt.apps@gmail.com](mailto:curtis.qt.apps@gmail.com)

For any question, request, or concern regarding privacy or this policy, please contact the email address above.

## 2. Summary (TL;DR)

EzBudget is a **local-first, offline personal finance app**. In short:

- The App does **not** request the `INTERNET` permission. It is technically incapable of sending data to the internet, to the developer, or to any server, because Android enforces this permission for any network socket access and it is not present in the App's manifest.
- There is **no user account, no sign-up, and no login**.
- There are **no advertisements**, **no analytics SDKs**, **no crash-reporting SDKs**, **no tracking libraries**, and **no third-party data-sharing integrations** built into the App.
- All of your financial data (accounts, transactions, categories, budgets, notes) is stored **exclusively on your device**, in a local database.
- The only way data ever leaves your device is if **you** actively choose to (a) share/export a CSV file via Android's share sheet, or (b) use the optional "Shared Pots" feature to sync group-expense data **directly with another device you choose**, over Bluetooth/Wi‑Fi, with no server in between.
- The App is distributed through Google Play, which independently collects certain limited technical/diagnostic information under its own privacy policy (see Section 9).

## 3. Data Stored Locally On Your Device

EzBudget uses a local database (Room/SQLite) and local app preferences (Android DataStore) stored in the App's private storage area on your device. This includes:

- **Accounts**: name, type (e.g. checking, savings, cash), balance, currency, color/icon
- **Transactions**: amount, type (income/expense), category, optional note, optional tags, date, linked account(s)
- **Categories and Budgets**: names, types, budget limits and periods
- **Recurring transactions** and **import history** (e.g. which CSV rows were previously imported, to avoid duplicates)
- **Shared Pots / group data** (see Section 4): group names, member display names you enter, group expenses, splits, and settlement/payment records
- **App settings**: selected currency, theme, language, default account, biometric-lock toggle, custom exchange rates you enter, your own display name used in Shared Pots, and onboarding/navigation preferences

None of this data is transmitted anywhere by the App itself. It exists only in the App's local storage on your device, until you delete it (via in-app deletion, clearing the App's storage in Android system settings, or uninstalling the App).

### Android system backup

Like most Android apps, EzBudget's local database and preferences are eligible for Android's built-in **Auto Backup / cloud backup** system, which — if enabled on your device — can back up this data to **your own Google Account** (Google Drive) so it can be restored if you reinstall the App or set up a new device. This backup process is performed by the Android operating system and Google, not by the App's developer; the developer has no access to these backups. You can disable this in your device's system backup settings. Google's handling of such backups is governed by [Google's Privacy Policy](https://policies.google.com/privacy).

## 4. Shared Pots (Local Group Expense Sync)

The optional "Shared Pots" feature lets you split expenses with other people (similar to Splitwise). It works entirely **peer-to-peer, without any server or account**:

- To sync a group, EzBudget uses Google's **Nearby Connections API** (part of Google Play Services), which connects two nearby devices directly via **Bluetooth and/or Wi‑Fi (Wi‑Fi Direct)**.
- Group data exchanged this way — group name, member display names, expenses, amounts, categories, and settlement records — is sent **directly between the participating devices**. EzBudget does not operate, and does not send this data to, any backend server.
- Because this feature relies on Bluetooth/Wi‑Fi device discovery, Android requires the App to request `ACCESS_FINE_LOCATION` and Bluetooth/Wi‑Fi related permissions (see Section 6). This location permission is used **solely to enable Bluetooth/Wi‑Fi scanning as required by the Android OS** — the App does not read, store, or use your GPS location or coordinates for any purpose, and no location data is included in any synced payload.
- Member "identities" in Shared Pots are just display names/emoji/colors you or your group members type in — there is no verification, no linked account, and no central directory of users.
- You choose which nearby device to connect to and confirm the connection; data is only exchanged with devices you actively pair with during an active sync session.

## 5. CSV Import and Export

- **Import**: You can import transactions from a CSV file stored on your device. This file is read locally by the App; it is not uploaded anywhere.
- **Export**: You can export your transactions to a CSV file. This file is written to the App's private cache directory and shared only via Android's standard **share sheet** (`Intent.ACTION_SEND`) through a `FileProvider`. Whether and with whom this exported file is subsequently shared (e.g. email, cloud storage, messaging app) is entirely your choice and outside of the App's or developer's control — that third-party app's own privacy policy would then apply.

## 6. App Permissions and Why They Are Needed

| Permission | Purpose |
|---|---|
| `USE_BIOMETRIC` / `USE_FINGERPRINT` | To let you optionally lock the App behind your device's fingerprint/face/biometric screen lock. Biometric data itself is captured, matched, and stored entirely by the Android operating system's secure biometric subsystem — the App never receives, sees, or stores any biometric data. It only receives a yes/no "authenticated" result. |
| `BLUETOOTH`, `BLUETOOTH_ADMIN`, `BLUETOOTH_SCAN`, `BLUETOOTH_ADVERTISE`, `BLUETOOTH_CONNECT` | Required to discover and connect to a nearby device for the optional Shared Pots sync feature (Section 4). |
| `ACCESS_WIFI_STATE`, `CHANGE_WIFI_STATE`, `NEARBY_WIFI_DEVICES` | Required by the Nearby Connections API to establish a direct Wi‑Fi Direct link between two devices for Shared Pots sync. |
| `ACCESS_FINE_LOCATION` | Required by Android for Bluetooth/Wi‑Fi device discovery (an OS-level requirement for this type of scanning on many Android versions). Not used to determine or store your actual location. |
| `READ_EXTERNAL_STORAGE` / `WRITE_EXTERNAL_STORAGE` (legacy, only used on older Android versions) | Required so you can pick a CSV file to import and save an exported CSV file. |
| `ACCESS_NETWORK_STATE` | Used internally by the Nearby Connections/Google Play Services and WorkManager libraries to check connectivity state; the App itself has no general internet access (no `INTERNET` permission). |
| `WAKE_LOCK`, `RECEIVE_BOOT_COMPLETED`, `FOREGROUND_SERVICE` | Used by Android's WorkManager library to reliably run local, on-device background tasks (e.g. processing recurring transactions and updating the home-screen widget) even after a device restart. No data leaves your device as a result of these background tasks. |

The App does **not** request the `INTERNET` permission, and does not request access to your contacts, camera, microphone, SMS, call logs, or precise location beyond what is described above.

## 7. Advertising, Analytics, and Third-Party SDKs

EzBudget contains **no advertising SDKs**, **no analytics/telemetry SDKs** (e.g. no Firebase Analytics, no Google Analytics), **no crash-reporting SDKs** (e.g. no Crashlytics), and **no social-media or marketing SDKs**. The only third-party library involved in any data exchange is Google's Nearby Connections API described in Section 4, which facilitates direct device-to-device transfer and does not send your data to Google or the developer.

We do not sell, rent, or trade your personal data to anyone, because we never receive it in the first place.

## 8. Children's Privacy

EzBudget is a general-purpose budgeting tool not directed at children. It does not knowingly collect any personal information from children, and since the App collects no data on the developer's side at all, there is no server-side data of any kind — from children or otherwise — for the developer to hold.

## 9. Google Play Distribution

The App is distributed via the Google Play Store. Google independently collects certain limited technical information in connection with distribution and operation of the Play Store itself (e.g. install/uninstall counts, basic device compatibility data, and — via Android's built-in Play Vitals system — automatically generated crash/ANR (App Not Responding) diagnostic reports). This collection is performed by Google as the store operator, independent of any code added by the developer, and is governed by [Google's Privacy Policy](https://policies.google.com/privacy) and [Google Play's Data Safety](https://support.google.com/googleplay/answer/11416267) framework, not by this policy.

## 10. Your Rights

Because EzBudget does not transmit your personal data to the developer or any server, the developer holds no copy of your data against which to exercise access, rectification, deletion, restriction, or portability requests — all of your data resides solely on your device, under your direct control at all times. In practice, you exercise these rights yourself, directly in the App or your device settings:

- **Access / Portability**: use the in-app CSV export feature.
- **Rectification**: edit any transaction, account, category, budget, or group directly in the App.
- **Erasure**: delete individual records in the App, clear the App's storage via Android Settings → Apps → EzBudget → Storage → Clear data, or uninstall the App.
- **Objection / Restriction**: simply stop using the relevant feature (e.g. Shared Pots, biometric lock) at any time via Settings.

If you believe your data protection rights have been affected in a way connected to this App, you may contact the developer at the email in Section 1, or lodge a complaint with your local data protection supervisory authority (in Germany, e.g. your state's `Landesbeauftragte(r) für Datenschutz`).

## 11. Data Security

Since your data never leaves your device (except when you explicitly export/share it, or when you explicitly use the peer-to-peer Shared Pots sync feature), the primary safeguard is the security of your own device and its operating system, plus Android's app sandboxing, which keeps EzBudget's private storage inaccessible to other apps without root access. We recommend enabling the App's optional biometric lock and keeping your device's operating system up to date.

## 12. Changes to This Policy

This Privacy Policy may be updated from time to time, for example if new features are added that change how data is handled. The "Last updated" date at the top of this document will reflect the most recent revision. Continued use of the App after changes take effect constitutes acceptance of the revised policy.

## 13. Contact

Questions about this Privacy Policy or the App's data practices can be sent to: **[curtis.qt.apps@gmail.com](mailto:curtis.qt.apps@gmail.com)**
