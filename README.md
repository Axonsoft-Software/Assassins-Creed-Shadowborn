# Assassin’s Creed: Shadowborn

Technischer Fan-Prototyp eines narrativen Stealth-Actionspiels im industriellen Frankreich von 1885. Das Repository enthält einen spielbaren Hafen-Vertical-Slice, ein Animus-inspiriertes Start- und Menüsystem, eine Metal-Renderingbasis sowie deterministische Gameplay-, Missions-, Streaming- und Audiosysteme.

> **Wichtiger Hinweis:** Dies ist ein nicht offizielles, nicht kommerzielles Fan-/Lernprojekt. Assassin’s Creed und zugehörige Marken gehören Ubisoft. Für eine öffentliche oder kommerzielle Veröffentlichung müssen eigener Name, eigene Bildsprache und vollständig lizenzierte Assets verwendet werden.

## Gesamtstatus

**Stand:** 17. Oktober 2026  
**Entwicklungsphase:** Vertical Slice G5  
**Aktueller Arbeitsschritt:** Hafen-Streaming W1–W6 und STREAM-001–005-Kernabnahme integriert; Langzeitlauf und Geräteprofiling folgen
**Reifegrad:** spielbarer Technikprototyp, nicht produktions- oder veröffentlichungsfertig

| Bereich | Status | Aktueller Umfang |
|---|---|---|
| macOS-Spiel | In Entwicklung | Spielbarer M01-Hafenprototyp mit Metal-Renderer und Gameplay-Loop |
| iOS-Oberfläche | In Entwicklung | Animus-Startfluss, Titel, Modusauswahl und Hub; noch keine vollständige Gameplay-Portierung |
| Rendering | Prototyp integriert | Metal, dynamisches Hafenlicht, Fog, Frame-Telemetrie und adaptives FPS-Ziel |
| Audio | Prototyp integriert | Audio-Busse, Dialog-Ducking, 3D-Emitter, Stimmenbudget und Audio-Bank-Vertrag |
| Gameplay | Vertical Slice | Bewegung, Schleichen, Wachen, Dialoge, Interaktionen und Missionsfortschritt |
| Simulation | Vertical Slice | Deterministischer Takt, Hafenarbeiter, Zug, Schiffe und Liegeplatzlogik |
| Speichern | Prototyp integriert | Versionierte Checkpoints mit Primary-/Backup-Datei und Wiederaufnahme |
| Streaming | W1–W6-Basis integriert | Zellplanung, CPU-/GPU-Residency, Culling, Speicherdruck, Referenzledger und Telemetrie |
| Tests | Teilweise verifiziert | Letzter vollständiger Core-Lauf: 99/99; zusätzliche Audio-, Lizenz- und Streamingtests vorhanden |

## Plattform-Support

| Plattform | Buildstatus | Laufzeitstatus |
|---|---|---|
| macOS / Apple Silicon | Erfolgreich gebaut | Primäre Entwicklungsplattform; manueller vollständiger Abnahmelauf offen |
| iOS / iPad-Kompatibilitätsziel | Erfolgreich auf `My Mac (Designed for iPad)` gebaut | Start- und Menüfluss vorhanden |
| Physisches iPhone | Erfolgreich gebaut | `iPhone 17 Pro Max von kevin`; sichtbarer Gerätelauf weiterhin offen |
| Linux | Kein App-Target | Nur Teile des plattformunabhängigen Swift-Kerns sind über SwiftPM nutzbar |

Apple-Plattformen benötigen Xcode mit Metal-/MetalKit- und AVFAudio-Unterstützung. Konkrete Release-Mindestversionen sind noch nicht als stabiler öffentlicher Supportvertrag freigegeben.

Die momentane Xcode-Projektkonfiguration verwendet die Beta-SDK-Ziele iOS 27.2 und macOS 27.2. Das beschreibt den aktuellen Entwicklungsstand und ist noch keine endgültige öffentliche Mindestanforderung.

## Bereits implementiert

- Animus-inspirierter Lade-, Entwicklungsinfo-, Login-, Update-, Fehler- und Titelablauf
- Automatischer Übergang nach der Vorbereitung zu „Zum Starten tippen“
- Offline-/Online-Auswahl und kachelbasierter, transparenter Animus-Hub
- Animierte 2D-/3D-Animus-Hintergründe mit Reduce-Motion-Rücksicht
- Spielbarer M01-Hafen mit Greybox-Geometrie und Missionszielen
- Spielerbewegung, Kamera, Sprint, Schleichen, Springen und Weltinteraktion
- Wachpatrouillen mit Sicht, Verdacht, Verfolgung und Checkpoint-Rückkehr
- Dialogentscheidungen, Missionsjournal und Missionsabschlussbericht
- Deterministische Zug-, Schiffs-, Arbeiter- und Hafen-Simulation
- Versioniertes Savegame mit Backup und sicherem Fallback
- Metal-Rendering mit Beleuchtung, Nebel und CPU-/GPU-Frametelemetrie
- Audio-Engine mit Music-, Ambience-, Foley-, Dialogue-, SFX-, UI- und Accessibility-Bussen
- Dialog-Ducking, räumliche Monoquellen, Occlusion und priorisiertes 24-Stimmen-Budget
- Validiertes Audio-Bank-Manifest mit Concurrency-Gruppen und Untertitelbindung
- Validiertes Asset-Lizenzregister, das Platzhalter erlaubt, aber einen Release nachvollziehbar blockiert
- Abbrechbares CPU-Asset-Preloading mit atomarem Commit, Residency-Cache und prozeduralen Assettypen
- W1/W2-Streamingverträge werden im macOS-Bundle geladen; der initiale Central-Preload ist zur Laufzeit nachgewiesen
- W3 kopiert CPU-residente Daten per Metal-Blit in private GPU-Puffer und schaltet sie erst nach GPU-Completion sichtbar
- Spielerposition priorisiert Fokus- und Nachbarzellen; veraltete Übergänge werden abgebrochen und entfernte Zellassets evictet
- W4 blendet nur NPC-Renderrepräsentationen aus; Wach-, Arbeiter-, Quest- und Save-Zustände simulieren unverändert weiter
- W5 reagiert auf macOS-Speicherdruck, reduziert Sichtweite und Renderbudget und hält beim Streaming nur die Fokuszelle resident
- W6 erfasst Requests, Completions, Abbrüche, Fehler, Speicherdruck, CPU-Bytes, GPU-Sichtbarkeit und maximale Zellresidenz
- Ein referenzgezählter Residency-Ledger schützt gemeinsam verwendete Assets und weist veraltete Commits zurück
- STREAM-002–005 sichern Zugkontinuität, Missionsbeweise, saubere Uploadabbrüche und konsistente Checkpoint-Wiederaufnahme

## Noch nicht fertig

- Finale Charakter-, Gebäude-, Animations-, VFX- und Audioassets
- Vollständiges Parkour-, Kampf- und Klettersystem
- Vollständige Kampagne und offene Welt
- Vollständiger iOS-Gameplay-Loop
- Musik-Crossfades, Lautheitsabnahme und Geräte-Hörtests
- Zehnminütige STREAM-001-bis-005-Laufzeitabnahme und belastbare Geräte-Benchmarks
- Finale VoiceOver-, Dynamic-Type-, Kontrast- und Motion-Safety-Abnahme auf Geräten
- Release-Signing, Store-Verteilung, Lizenzprüfung und produktionsreifes Branding

## macOS-Steuerung

| Taste / Aktion | Funktion |
|---|---|
| WASD | Bewegen |
| Maus ziehen | Kamera drehen |
| Umschalt | Sprinten |
| C halten | Schleichen |
| Leertaste | Springen |
| E | Interagieren / Dialog öffnen |
| 1 / 2 | Dialogoption auswählen |
| Tab | Missionsjournal |
| P | Pause / Fortsetzen |
| F5 | Manuell speichern |
| R, danach erneut R | Neuen Durchlauf bestätigen und Checkpoint löschen |

## Projekt öffnen

1. `AssassinsCreedShadowborn.xcodeproj` in Xcode öffnen.
2. Für den spielbaren Prototyp das Scheme `AssassinsCreedShadowborn macOS` und `My Mac` auswählen.
3. Für den iOS-Start- und Menüfluss das Scheme `AssassinsCreedShadowborn` mit einem kompatiblen iOS-Ziel verwenden.
4. `App/ShadowbornApp.swift` ist eine alternative SwiftUI-Schablone mit eigenem `@main` und darf nicht gleichzeitig mit dem storyboardbasierten App-Einstieg aktiviert werden.

Der macOS-Checkpoint liegt standardmäßig unter:

```text
~/Library/Application Support/Shadowborn/M01-checkpoint.json
```

## Tests und Validierung

```sh
swift test
python3 Tools/ValidateContent.py
python3 Tools/ValidateEra.py
python3 Tools/ValidateXcodeProject.py
bash Tools/CheckProject.sh
```

Letzter bestätigter Stand:

- 99 von 99 Core-Tests in 18 Suites bestanden
- 5 von 5 `ShadowbornContracts`-Xcode-Tests bestanden
- macOS-App zuletzt auf `My Mac` erfolgreich gebaut, 0 Buildfehler
- iOS-App zuletzt auf `My Mac (Designed for iPad)` erfolgreich gebaut, 0 Buildfehler
- W1-/W2-Manifest und Assetkatalog wurden im macOS-App-Bundle ohne Fallback geladen
- Der Central-Preload lud Layout, Interaktionen und Pfade mit positiver residenter Bytezahl
- Ein ausgeführter Fehlerpfad bestätigte atomaren Rollback und anschließende Cache-Wiederverwendung
- Achtundzwanzig neue Audio-, Lizenz- und Streamingtests sind vorhanden; der abschließende SwiftPM-Gesamtlauf wurde zuletzt durch einen verwaisten lokalen `.build`-Lock verhindert
- Ein echter Metal-Blit bestätigte GPU-Sichtbarkeit nach Completion sowie vollständige Eviction
- Ein Positionslauf bestätigte Central → Rail → Docks einschließlich deterministischer Nachbarpriorität und Eviction
- Ein Culling-/Speicherdrucklauf hielt 41 Simulationskandidaten erhalten, reduzierte kritisches Rendering auf 12 und behielt eine entfernte alarmierte Wache sichtbar
- Ein W6-Stresslauf bestätigte 100 duplikatfreie Rail-/Docks-Wechsel sowie getrennte Completion-, Abbruch-, Fehler- und Speicherdruckmetriken
- STREAM-002 ergab bei 2.500 Ticks und wiederholten Zellwechseln 0 Abweichungen zur Zugreferenz sowie eine planmäßige Ankunft
- STREAM-003 bestätigte einen konsistenten Missionsbeweis nach Serialisierung; STREAM-004 hinterließ nach Abbruch 0 residente Assets und 0 Bytes
- STREAM-005 deckt die Wiederaufnahme von Spieler-, Missions- und Zugzustand aus einem neu geöffneten Checkpoint-Store ab

Details stehen in `Docs/Docs/Handoff/G5/BUILD_REPORT.md`, `TEST_REPORT.md` und `KNOWN_ISSUES.md`.

## Nächste Planpunkte

1. Zehnminütige Hafenrunde mit I/O-, GPU- und Residency-Telemetrie aufzeichnen.
2. Echten Prozessabbruch mit anschließendem Checkpoint-Relaunch sichtbar prüfen.
3. Fokus- und Save-Wiederaufnahmetests auf realer Hardware ausführen.
4. Sichtbaren Lauf auf dem physischen iPhone und reale Accessibility-Abnahme durchführen.
5. G5-Abnahme mit Release-Build, GPU-Capture und echten Lizenznachweisen.

## Repository-Struktur

```text
App/                              Alternative SwiftUI-App-Schablone
AssassinsCreedShadowborn iOS/     iOS-Startfluss und Animus-Oberfläche
AssassinsCreedShadowborn macOS/   macOS-App-Einstieg
Engine/                           Metal-Renderer, Eingabe und Audio-Laufzeit
Game/                             Gameplay-, Simulations- und Contentverträge
Content/                          Laufzeitdaten des spielbaren Prototyps
Docs/                             Pläne, Story, technische Verträge und QA-Berichte
Tests/                            Swift-Tests des plattformunabhängigen Spielkerns
Tools/                            Content- und Projektvalidierung
```

## Dokumentation

Die Pläne unter `Docs/` sind die Entwicklungsgrundlage. Besonders relevant sind:

- `Docs/V4_5_LESEN_ZUERST.md`
- `Docs/116_VerticalSlice_G0_bis_G5_Arbeitsauftraege.md`
- `Docs/121_M01_Mac_Vertical_Slice_Implementierung.md`
- `Docs/Docs/Handoff/CHANGELOG_DESIGN.md`
- `Docs/Docs/QA/RELEASE_GATES.md`

Geplante Inhalte in den Dokumenten sind nicht automatisch bereits implementiert. Maßgeblich für den tatsächlichen Stand sind diese README, die G5-Handoff-Berichte und der ausführbare Code.

## Pflege dieser README

Diese Datei wird bei jeder wesentlichen Entwicklungsstufe mitgeführt. Änderungen an Plattform-Support, Buildstatus, Teststand, implementierten Systemen oder bekannten Einschränkungen müssen hier zusammen mit den zugehörigen Handoff-Berichten aktualisiert werden.
