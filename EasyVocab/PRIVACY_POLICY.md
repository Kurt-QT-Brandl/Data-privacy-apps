# EasyVocab — Privacy Policy

*Effective: 21 September 2026*
*Applies to: EasyVocab for Android (`com.curtisqt.EasyVocab`)*

Also published as a shareable page: https://claude.ai/artifact/FwnLckePFn2k29xNJWprmA

## In short

- EasyVocab has no accounts, no analytics, no ads, and no internet permission — it cannot send data anywhere on its own.
- Everything you enter (vocabulary, photos, progress) stays in a local database on your device.
- Data only ever leaves your device if you deliberately export or share it yourself, to a destination you pick.

## 1. Overview

EasyVocab is a vocabulary learning app built around the Leitner spaced-repetition method. You create your own language pairs and vocabulary cards, and the app schedules reviews for you. It is designed to work entirely offline, and this policy explains exactly what that means for your data.

## 2. Who's responsible

EasyVocab is developed by an independent developer. For any privacy question, see [Contact](#12-contact) below.

## 3. What we don't collect

EasyVocab does not create user accounts, does not use analytics or crash-reporting SDKs, does not show ads, and does not include any third-party tracking libraries. The app's Android manifest does not request the `INTERNET` permission at all — meaning the app is technically unable to make a network request, whether to our servers (we don't have any) or anyone else's.

## 4. What's stored on your device

Everything you do in EasyVocab is saved locally, in a private database and file storage area that only EasyVocab can access:

| Data | What it is |
|---|---|
| Vocabulary | Your language pairs, cards, example sentences, word types, groups and notes |
| Photos | Any images you attach to a card, stored as files inside the app's private folder |
| Learning progress | Leitner phase, due dates and answer history, tracked per card and per direction |
| Preferences | Theme, app display language, and image-reveal timing |
| Reminders | The local schedule used to notify you when cards are due |

None of this is uploaded automatically. It stays in Android's app-private storage, which is removed the moment you uninstall EasyVocab.

## 5. Permissions

- **Camera** — optional, requested only when you tap the camera option while adding a photo to a card. Used solely to capture that one photo.
- **Notifications** — used to show local reminders when cards are due for review. Every notification is generated on your device; nothing is sent to or received from a server.
- **Photos / gallery** — EasyVocab uses Android's built-in photo picker to let you choose an existing image. This picker runs outside the app, so EasyVocab is never granted broad access to your photo library — only the one picture you select.

## 6. When data leaves your device

There are exactly two ways data can leave your device, and both require you to start them on purpose:

- **Backup / export.** You can export a language pair (or your whole collection) as a CSV or ZIP file and share it via Android's share sheet — to a cloud drive, email, another app, wherever you choose.
- **AI review hand-off.** You can export newly-added cards as text so you can hand them to an AI assistant of your choice for translation help or proofreading, then paste the corrected result back in to import it.

In both cases, you choose the destination app yourself through the Android share sheet at the moment of sharing. EasyVocab has no default recipient, sends nothing automatically, and has no visibility into or control over what happens to the data once it reaches the app you picked.

## 7. Third parties

EasyVocab does not embed any third-party analytics, advertising, or backend SDK. The only outside code involved is the Android platform itself and the AndroidX/Jetpack libraries used to build the app's local database, background reminders, and interface — none of which transmit your data anywhere.

## 8. Retention & deletion

Your data is retained locally for as long as you keep EasyVocab installed. You can delete an individual card, an entire language pair, or a photo at any time from within the app. Uninstalling EasyVocab permanently deletes its private database and files as part of Android's normal app-removal process.

## 9. Children's privacy

EasyVocab is not directed at children and does not knowingly collect personal information from anyone, regardless of age — it doesn't collect personal information at all, since nothing you enter ever reaches us.

## 10. Security

Because your vocabulary data never travels off your device, the main safeguard is the security of the device itself. We recommend using a device screen lock, since anyone with unlocked access to your phone can open any locally-installed app, including this one.

## 11. Changes to this policy

If EasyVocab's data practices ever change — for example, if a future version adds an optional online feature — this policy will be updated first, and the "Effective" date at the top will change accordingly.

## 12. Contact

Questions about this policy or your data can be sent to `your-contact-email@example.com`.

> **Placeholder** — replace with the support email you want listed on the Play Store before publishing.
