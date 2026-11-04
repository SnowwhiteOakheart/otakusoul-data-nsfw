# AI.md – Wegweiser für das NSFW-Inhaltsrepository (`otakusoul-data-nsfw`)

Dieses Dokument ist der verbindliche Leitfaden für `SnowwhiteOakheart/otakusoul-data-nsfw`, das separate FSK18-/NSFW-Inhaltsrepository von OtakuSoul. Es enthält Daten, Szenarien und Bilder für Erwachsene, keinen App-Code. Eine tokensparende Schnellreferenz aller Inhalte und Validierungs-Checks bietet [`CONTENT_INDEX.md`](CONTENT_INDEX.md) – schlage hier in `AI.md` gezielt die jeweiligen Themenabschnitte nach.

## Zusammenarbeit und Veröffentlichung

- Mit dem Nutzer auf Deutsch kommunizieren; thematische Commit-Beschreibungen auf Deutsch.
- Das Repository bleibt bis auf Weiteres **privat**. Keine Inhalte unbedacht öffentlich machen oder in das SFW-Repository `otakusoul-data` überführen.
- Nur beauftragte Arbeit committen und pushen. Nach jedem fertiggestellten Paket/Charakter: `ROADMAP.md` und `CONTENT_INDEX.md` aktualisieren.
- Keine Maschinenpfade, Geheimnisse oder temporären Caches einchecken.

## Verzeichnisstruktur

```text
README.md                       Einstieg & Projektübersicht
AI.md                           dieser verbindliche Wegweiser
AGENTS.md / CLAUDE.md            Verweise auf CONTENT_INDEX.md und AI.md
CONTENT_INDEX.md                tokensparende Inhalts- und Architekturreferenz
ROADMAP.md                      Arbeitsstand und geplante FSK18-Inhalte
soul_registry.json              Charakterindex (mit nsfw: true)
cards_gateway/*.png             Hub-fertige V2-Charakterkarten
stages_registry.json             Szenenindex (mit nsfw: true)
stages_gateway/*.json            Hub-fertige FSK18-Szenen
lorebooks_registry.json          Lorebook-Index (mit nsfw: true)
lorebooks_gateway/*.json         Hub-fertige Lorebooks
collections_registry.json        Sammlungen je Paket mit Titelbild (mit nsfw: true)
presets/<paket>/                 Quellpakete (JSONs, Expressions, Hintergründe)
tools/validate_content.py        Validierungswerkzeug
```

## FSK18-Spezifikationen & Kennzeichnung

1. **Registries:**
   * Jeder Eintrag in `soul_registry.json`, `stages_registry.json` und `lorebooks_registry.json` trägt `"nsfw": true`.
   * `collections_registry.json` (Aufbau wie im Haupt-Repository: `id`, `title`, `description`, `cover_url` auf `presets/<paket>/cover.webp`, `lorebooks`/`scenes`/`characters` als Registry-Schlüssel) fasst die Inhalte eines Pakets im Hub zu einer Karte zusammen. Neue Figuren, Szenen oder Lorebooks eines Pakets dort mit eintragen; die App bevorzugt bei gleichen Namen (z. B. Jibril, Albedo, Mint) die Einträge dieses Repositorys.
   * Wie im Haupt-Repository gilt: Bei jeder inhaltlichen Änderung `revision` um 1 erhöhen und `updated` auf das Tagesdatum setzen.
2. **Szenen (`stages_gateway/*.json`):**
   * Unter `extensions.otakusoul_story`:
     - `notes`: muss mindestens `["nsfw", "adult", "romance"]` enthalten.
     - `rating`: `"18+"`
   * Hintergründe unter `extensions.otakusoul_assets.backgrounds` auflisten.
3. **Emotionsbilder (`extensions.expressions`):**
   * Unterstützt die 6 Standard-Emotionen (`neutral`, `happy`, `relaxed`, `surprised`, `angry`, `sad`) sowie die 5 erweiterten Erotik- und Romance-Emotionen:
     - `blush`: Scham, starkes Erröten, Verlegenheit
     - `seductive`: Verführerisch, neckend, herausfordernder Blick
     - `aroused`: Körperliche Erregung, beschleunigter Atem
     - `ecstasy`: Lustempfinden, intimer Höhepunkt
     - `afterglow`: Erschöpfte Zufriedenheit, Kuscheln
   * Dazu die Nischen-Schlüssel `teasing`, `fear`, `disgust` und `crying`.
4. **App-Markierung `extensions.otakusoul_nsfw`:**
   * Jede Karte (`data.extensions`, in Preset-JSON, Preset-PNG und `cards_gateway`-PNG), jede Szene und jedes Lorebook
     (oberste Ebene `extensions`) trägt `"otakusoul_nsfw": true`. OtakuSoul blendet so markierte Inhalte aus, solange
     „Inhalte für Erwachsene (18+)“ aus ist – auch bei Import als Datei. Der Validator meldet eine fehlende Markierung als Fehler.
   * Volljährigkeit jeder Figur steht ausdrücklich in der Karte (Beschreibung bzw. `creator_notes`, alle Sprachen).
5. **Validierung vor jedem Push:**
   * Vor jedem Commit `python3 tools/validate_content.py` ausführen.


- Musik: `extensions.otakusoul_music` (Englisch, nicht übersetzen; Schema in `docs/stage_music.md` der App). Szenen tragen `set` (eine Sammlung = ein Set, die Sammlungs-ID), `style` und `moods.<stimmung>` mit ACE-Step-`caption` (optional `lyrics` + `vocal_language` für leisen Gesang, `bpm`, `duration`, `count`); Lorebooks die Klangwelt `style`, Karten ein Leitmotiv `theme` (optional `moods`). Alle Szenen einer Sammlung haben denselben Abschnitt. Gepflegt in `tools/music_settings.json`, geschrieben mit `tools/set_music.py` (Szenen nach Titel, Lorebooks nach Name, Karten nach `data.name`: JSON, Preset- und Gateway-PNG; erhöht `revision`/`updated` der geänderten Registry-Einträge selbst). Neue Szenen, Lorebooks und Figuren dort eintragen; Captions beschreiben nur Musik, auch bei 18+-Inhalten nicht explizit. Fertige Titel liegen unter `music/<set>/<stimmung>/` und werden in `tracks` der Szenen eingetragen (Pfad + SHA-256).

## Einreichungen aus der App

Die App speichert Beiträge als ZIP im Repo-Layout (`cards_gateway/<name>.png` oder `stages_gateway/<name>.json`, dazu `EINREICHUNG.json` mit Lizenz, Altersmarke, Prüfsummen und `README.txt`) und öffnet ein vorbefülltes Issue „Beitrag: …“. Der Workflow prüft jedes neue oder bearbeitete Issue mit diesem Titel (oder Label `einreichung`) und hält genau einen Ergebniskommentar aktuell. Geprüft werden: Archiv (höchstens 25 MB / 20 Dateien, nur erlaubte Pfade, keine Verknüpfungen), Manifest (Prüfsummen, Lizenz CC0/CC BY/CC BY-SA, Autor:in, richtiges Repository je Altersmarke), Inhalt (Karte im PNG bzw. Szenen-Pflichtfelder, `otakusoul_license`, `otakusoul_nsfw` passend zum Repository), keine Spuren des fremden Rechners (Laufwerks- und Benutzerpfade, `file://`) und keine `vroid:`-Verweise, keine Dubletten (Datei, Figurenname, Szenen-ID) sowie die üblichen Regeln aus `validate_content.py`. Gefährten, die weder im Hub noch unter den Starterfiguren der App (`APP_STARTERS`) sind, ergeben nur einen Hinweis.

Das Paket wird nur gelesen, nie ausgeführt; der Issue-Text erreicht die Schritte nur über Umgebungsvariablen. Erst das Label `aufnehmen` (nur Maintainer können Labels setzen) übernimmt die Datei in Kleinbuchstaben, ergänzt den Registry-Eintrag (`revision: 1`), führt `validate_content.py --sync-registry` aus und legt den Branch `beitrag/issue-<n>` samt Pull Request an. Dürfen Actions keine Pull Requests anlegen (Einstellung „Allow GitHub Actions to create and approve pull requests“), steht im Issue ein Ein-Klick-Link. Rechte, Ton und Altersfreigabe prüft weiterhin ein Mensch vor dem Mergen. Lokal: `python3 tools/check_submission.py --zip paket.zip [--apply --issue <n>]`. Skript und Workflow sind in `otakusoul-data` und `otakusoul-data-nsfw` gleich; das Repository erkennt sich am Namen.
