# EzBudget

## Datenschutzerklärung

**Stand: 25. Juli 2026**

Dieses Dokument ist veröffentlicht unter [github.com/Kurt-QT-Brandl/Data-privacy-apps/ezbudget/datenschutz-DE.md](https://github.com/Kurt-QT-Brandl/Data-privacy-apps/blob/main/ezbudget/datenschutz-DE.md). Eine englische Fassung finden Sie unter [dataprivacy.md](https://github.com/Kurt-QT-Brandl/Data-privacy-apps/blob/main/ezbudget/dataprivacy.md).

Diese Datenschutzerklärung beschreibt, wie die Android-App **EzBudget** (Paketname `com.curtisqt.ezbudget`, im Folgenden "die App") mit Daten umgeht. Sie orientiert sich an den Anforderungen der Google-Play-Richtlinie ["Nutzerdaten"](https://support.google.com/googleplay/android-developer/answer/9859455?hl=de) sowie den zugehörigen Richtlinienthemen der Google Play Console.

## 1. Verantwortlicher

Verantwortlich für diese App im Sinne der Datenschutz-Grundverordnung (DSGVO) ist:

**CurtisQT**
E-Mail: [kurt.qt.brandl@gmail.com](mailto:kurt.qt.brandl@gmail.com)

Bei Fragen, Anliegen oder Anträgen zum Datenschutz wenden Sie sich bitte an die oben genannte E-Mail-Adresse.

## 2. Zusammenfassung (Kurzfassung)

EzBudget ist eine **lokale, offline funktionierende Finanz- und Haushaltsbuch-App**. Kurz zusammengefasst:

- Die App fordert **keine `INTERNET`-Berechtigung** an. Sie ist technisch nicht in der Lage, Daten an das Internet, an den Entwickler oder an irgendeinen Server zu senden, da Android für jeglichen Netzwerkzugriff diese Berechtigung zwingend voraussetzt und sie im Manifest der App nicht vorhanden ist.
- Es gibt **kein Benutzerkonto, keine Registrierung und keinen Login**.
- Die App enthält **keine Werbung**, **keine Analyse-SDKs**, **keine Absturzberichts-SDKs** (Crash-Reporting) und **keine Tracking- oder Marketing-Bibliotheken** von Drittanbietern.
- Sämtliche Finanzdaten (Konten, Transaktionen, Kategorien, Budgets, Notizen) werden **ausschließlich lokal auf Ihrem Gerät** in einer lokalen Datenbank gespeichert.
- Daten verlassen Ihr Gerät nur dann, wenn **Sie selbst** aktiv (a) eine CSV-Datei über die Android-Teilen-Funktion exportieren/versenden oder (b) die optionale Funktion "Shared Pots" (gemeinsame Ausgabenverwaltung) nutzen, um Gruppendaten **direkt mit einem von Ihnen ausgewählten anderen Gerät** zu synchronisieren – ganz ohne zwischengeschalteten Server.
- Die App wird über Google Play vertrieben. Google erhebt dabei eigenständig bestimmte begrenzte technische Diagnosedaten gemäß seiner eigenen Datenschutzerklärung (siehe Abschnitt 9).

## 3. Lokal auf Ihrem Gerät gespeicherte Daten

EzBudget verwendet eine lokale Datenbank (Room/SQLite) sowie lokale App-Einstellungen (Android DataStore), die im privaten Speicherbereich der App auf Ihrem Gerät abgelegt werden. Dazu gehören:

- **Konten**: Name, Typ (z. B. Girokonto, Sparkonto, Bargeld), Kontostand, Währung, Farbe/Symbol
- **Transaktionen**: Betrag, Art (Einnahme/Ausgabe), Kategorie, optionale Notiz, optionale Tags, Datum, verknüpfte(s) Konto(en)
- **Kategorien und Budgets**: Bezeichnungen, Typen, Budgetlimits und -zeiträume
- **Wiederkehrende Transaktionen** und **Importverlauf** (z. B. welche CSV-Zeilen bereits importiert wurden, um Duplikate zu vermeiden)
- **Shared-Pots-/Gruppendaten** (siehe Abschnitt 4): Gruppennamen, von Ihnen eingegebene Anzeigenamen der Mitglieder, Gruppenausgaben, Aufteilungen und Ausgleichszahlungen
- **App-Einstellungen**: gewählte Währung, Design (Theme), Sprache, Standardkonto, Ein-/Ausschalten der biometrischen Sperre, von Ihnen eingegebene Wechselkurse, Ihr eigener Anzeigename für Shared Pots sowie Einstellungen zu Onboarding und Navigation

Keine dieser Daten wird von der App selbst irgendwohin übertragen. Sie existieren ausschließlich im lokalen Speicher der App auf Ihrem Gerät, bis Sie sie löschen (über die Löschfunktion in der App, über das Löschen des App-Speichers in den Android-Systemeinstellungen oder durch Deinstallation der App).

### Android-Systemsicherung (Backup)

Wie bei den meisten Android-Apps können die lokale Datenbank und die Einstellungen von EzBudget durch das in Android integrierte **Auto-Backup/Cloud-Backup-System** gesichert werden. Sofern auf Ihrem Gerät aktiviert, kann dieses die Daten in **Ihrem eigenen Google-Konto** (Google Drive) sichern, damit sie bei einer Neuinstallation oder auf einem neuen Gerät wiederhergestellt werden können. Dieser Sicherungsvorgang wird vom Android-Betriebssystem und von Google durchgeführt, nicht vom Entwickler der App; der Entwickler hat keinen Zugriff auf diese Sicherungen. Sie können dies in den System-Sicherungseinstellungen Ihres Geräts deaktivieren. Der Umgang von Google mit solchen Sicherungen unterliegt der [Datenschutzerklärung von Google](https://policies.google.com/privacy?hl=de).

## 4. Shared Pots (lokale Synchronisation gemeinsamer Ausgaben)

Die optionale Funktion "Shared Pots" ermöglicht es, Ausgaben mit anderen Personen zu teilen (ähnlich wie Splitwise). Sie funktioniert vollständig **von Gerät zu Gerät (Peer-to-Peer), ohne Server oder Benutzerkonto**:

- Zur Synchronisation einer Gruppe nutzt EzBudget die **Nearby-Connections-API** von Google (Teil der Google-Play-Dienste), die zwei in der Nähe befindliche Geräte direkt über **Bluetooth und/oder WLAN (Wi‑Fi Direct)** verbindet.
- Die auf diesem Weg ausgetauschten Gruppendaten – Gruppenname, Anzeigenamen der Mitglieder, Ausgaben, Beträge, Kategorien und Ausgleichszahlungen – werden **direkt zwischen den beteiligten Geräten** übertragen. EzBudget betreibt keinen Backend-Server und sendet diese Daten an keinen solchen.
- Da diese Funktion auf der Geräteerkennung über Bluetooth/WLAN beruht, verlangt Android von der App die Berechtigung `ACCESS_FINE_LOCATION` sowie weitere Bluetooth-/WLAN-Berechtigungen (siehe Abschnitt 6). Diese Standortberechtigung wird **ausschließlich benötigt, um die vom Android-Betriebssystem vorgeschriebene Bluetooth-/WLAN-Suche zu ermöglichen** – die App liest, speichert oder nutzt Ihren tatsächlichen GPS-Standort zu keinem Zweck, und keine Standortdaten sind Teil der synchronisierten Inhalte.
- "Mitglieder" in Shared Pots sind lediglich von Ihnen oder Ihren Gruppenmitgliedern eingegebene Anzeigenamen, Emojis und Farben – es findet keine Verifizierung statt, keine Kontoverknüpfung und kein zentrales Nutzerverzeichnis.
- Sie wählen selbst aus, mit welchem Gerät in der Nähe eine Verbindung hergestellt wird, und bestätigen diese aktiv. Daten werden nur mit Geräten ausgetauscht, mit denen Sie sich während einer aktiven Sync-Sitzung aktiv verbinden.

## 5. CSV-Import und -Export

- **Import**: Sie können Transaktionen aus einer auf Ihrem Gerät gespeicherten CSV-Datei importieren. Diese Datei wird lokal von der App gelesen und nirgendwohin hochgeladen.
- **Export**: Sie können Ihre Transaktionen in eine CSV-Datei exportieren. Diese Datei wird im privaten Cache-Verzeichnis der App abgelegt und ausschließlich über die Standard-Teilen-Funktion von Android (`Intent.ACTION_SEND`) mittels eines `FileProvider` weitergegeben. Ob und mit wem diese exportierte Datei anschließend geteilt wird (z. B. per E-Mail, Cloud-Speicher, Messenger), liegt vollständig in Ihrer eigenen Entscheidung und außerhalb der Kontrolle der App bzw. des Entwicklers – in diesem Fall gilt die Datenschutzerklärung der jeweils genutzten Drittanbieter-App.

## 6. App-Berechtigungen und ihr Zweck

| Berechtigung | Zweck |
|---|---|
| `USE_BIOMETRIC` / `USE_FINGERPRINT` | Ermöglicht die optionale Sperrung der App per Fingerabdruck-/Gesichts-/Bildschirmsperre Ihres Geräts. Die biometrischen Daten selbst werden vollständig vom sicheren biometrischen Subsystem des Android-Betriebssystems erfasst, abgeglichen und gespeichert – die App erhält, sieht oder speichert zu keinem Zeitpunkt biometrische Daten. Sie erhält lediglich ein Ja/Nein-Ergebnis ("authentifiziert"). |
| `BLUETOOTH`, `BLUETOOTH_ADMIN`, `BLUETOOTH_SCAN`, `BLUETOOTH_ADVERTISE`, `BLUETOOTH_CONNECT` | Erforderlich, um für die optionale Shared-Pots-Synchronisation (Abschnitt 4) ein anderes Gerät in der Nähe zu finden und sich damit zu verbinden. |
| `ACCESS_WIFI_STATE`, `CHANGE_WIFI_STATE`, `NEARBY_WIFI_DEVICES` | Von der Nearby-Connections-API benötigt, um eine direkte Wi‑Fi-Direct-Verbindung zwischen zwei Geräten für die Shared-Pots-Synchronisation herzustellen. |
| `ACCESS_FINE_LOCATION` | Von Android für die Bluetooth-/WLAN-Geräteerkennung vorausgesetzt (systemseitige Anforderung für diese Art der Suche auf vielen Android-Versionen). Wird nicht verwendet, um Ihren tatsächlichen Standort zu bestimmen oder zu speichern. |
| `READ_EXTERNAL_STORAGE` / `WRITE_EXTERNAL_STORAGE` (veraltet, nur auf älteren Android-Versionen relevant) | Ermöglicht die Auswahl einer zu importierenden CSV-Datei sowie das Speichern einer exportierten CSV-Datei. |
| `ACCESS_NETWORK_STATE` | Wird intern von den Bibliotheken Nearby Connections/Google Play-Dienste sowie WorkManager verwendet, um den Verbindungsstatus zu prüfen; die App selbst verfügt über keinen allgemeinen Internetzugriff (keine `INTERNET`-Berechtigung). |
| `WAKE_LOCK`, `RECEIVE_BOOT_COMPLETED`, `FOREGROUND_SERVICE` | Wird von der Android-Bibliothek WorkManager genutzt, um lokale Hintergrundaufgaben auf dem Gerät zuverlässig auszuführen (z. B. Verarbeitung wiederkehrender Transaktionen und Aktualisierung des Homescreen-Widgets), auch nach einem Geräteneustart. Durch diese Hintergrundaufgaben verlassen keine Daten Ihr Gerät. |

Die App fordert **keine** `INTERNET`-Berechtigung an und verlangt keinen Zugriff auf Ihre Kontakte, Kamera, Ihr Mikrofon, SMS, Anrufprotokolle oder Ihren genauen Standort über das oben Beschriebene hinaus.

## 7. Werbung, Analyse und Drittanbieter-SDKs

EzBudget enthält **keine Werbe-SDKs**, **keine Analyse-/Telemetrie-SDKs** (z. B. keine Firebase Analytics, kein Google Analytics), **keine Absturzberichts-SDKs** (z. B. keine Crashlytics) und **keine Social-Media- oder Marketing-SDKs**. Die einzige Drittanbieter-Bibliothek, die an einem Datenaustausch beteiligt ist, ist die in Abschnitt 4 beschriebene Nearby-Connections-API von Google, die den direkten Datenaustausch zwischen zwei Geräten ermöglicht und Ihre Daten dabei nicht an Google oder den Entwickler sendet.

Wir verkaufen, vermieten oder handeln nicht mit Ihren personenbezogenen Daten, da wir diese von vornherein zu keinem Zeitpunkt erhalten.

## 8. Datenschutz für Kinder

EzBudget ist ein allgemeines Werkzeug zur Haushaltsbuchführung und richtet sich nicht gezielt an Kinder. Es werden wissentlich keine personenbezogenen Daten von Kindern erhoben. Da die App auf Seiten des Entwicklers grundsätzlich keine Daten sammelt, existieren serverseitig auch keinerlei Daten – weder von Kindern noch von anderen Nutzern –, über die der Entwickler verfügen könnte.

## 9. Vertrieb über Google Play

Die App wird über den Google Play Store vertrieben. Google erhebt im Zusammenhang mit dem Vertrieb und Betrieb des Play Stores eigenständig bestimmte begrenzte technische Informationen (z. B. Installations-/Deinstallationszahlen, grundlegende Gerätekompatibilitätsdaten und – über das in Android integrierte Play-Vitals-System – automatisch erzeugte Absturz-/ANR-Diagnoseberichte ("App reagiert nicht")). Diese Erhebung erfolgt durch Google als Betreiber des Stores, unabhängig von jeglichem vom Entwickler hinzugefügtem Code, und unterliegt der [Datenschutzerklärung von Google](https://policies.google.com/privacy?hl=de) sowie dem Rahmenwerk ["Datensicherheit" von Google Play](https://support.google.com/googleplay/answer/11416267?hl=de), nicht dieser Datenschutzerklärung.

## 10. Ihre Rechte

Da EzBudget Ihre personenbezogenen Daten nicht an den Entwickler oder einen Server überträgt, verfügt der Entwickler über keine Kopie Ihrer Daten, gegenüber der Auskunfts-, Berichtigungs-, Löschungs-, Einschränkungs- oder Übertragbarkeitsansprüche geltend gemacht werden könnten – all Ihre Daten befinden sich ausschließlich auf Ihrem Gerät, jederzeit unter Ihrer eigenen Kontrolle. In der Praxis üben Sie diese Rechte selbst aus, direkt in der App oder in den Geräteeinstellungen:

- **Auskunft/Datenübertragbarkeit** (Art. 15, 20 DSGVO): Nutzen Sie die CSV-Exportfunktion in der App.
- **Berichtigung** (Art. 16 DSGVO): Bearbeiten Sie jede Transaktion, jedes Konto, jede Kategorie, jedes Budget oder jede Gruppe direkt in der App.
- **Löschung** (Art. 17 DSGVO): Löschen Sie einzelne Einträge in der App, leeren Sie den App-Speicher über Android-Einstellungen → Apps → EzBudget → Speicher → Daten löschen, oder deinstallieren Sie die App.
- **Widerspruch/Einschränkung** (Art. 18, 21 DSGVO): Beenden Sie einfach jederzeit über die Einstellungen die Nutzung der jeweiligen Funktion (z. B. Shared Pots, biometrische Sperre).

Sollten Sie der Ansicht sein, dass Ihre Datenschutzrechte im Zusammenhang mit dieser App beeinträchtigt wurden, können Sie sich an den Entwickler über die in Abschnitt 1 genannte E-Mail-Adresse wenden oder eine Beschwerde bei der für Sie zuständigen Datenschutz-Aufsichtsbehörde einreichen (in Deutschland z. B. bei der/dem Landesbeauftragten für Datenschutz Ihres Bundeslandes).

## 11. Datensicherheit

Da Ihre Daten Ihr Gerät nicht verlassen (außer wenn Sie sie ausdrücklich exportieren/teilen oder die Peer-to-Peer-Funktion Shared Pots ausdrücklich nutzen), liegt die wichtigste Schutzmaßnahme in der Sicherheit Ihres eigenen Geräts und Betriebssystems sowie im App-Sandboxing von Android, das den privaten Speicher von EzBudget ohne Root-Zugriff vor anderen Apps schützt. Wir empfehlen, die optionale biometrische Sperre der App zu aktivieren und das Betriebssystem Ihres Geräts stets aktuell zu halten.

## 12. Änderungen dieser Datenschutzerklärung

Diese Datenschutzerklärung kann von Zeit zu Zeit aktualisiert werden, etwa wenn neue Funktionen hinzugefügt werden, die den Umgang mit Daten verändern. Das Datum "Stand" am Anfang dieses Dokuments zeigt die letzte Aktualisierung an. Die fortgesetzte Nutzung der App nach Inkrafttreten von Änderungen gilt als Zustimmung zur aktualisierten Fassung.

## 13. Kontakt

Fragen zu dieser Datenschutzerklärung oder zum Umgang der App mit Daten richten Sie bitte an: **[kurt.qt.brandl@gmail.com](mailto:kurt.qt.brandl@gmail.com)**
