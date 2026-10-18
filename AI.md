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
presets/<paket>/                 Quellpakete (JSONs, Expressions, Hintergründe)
tools/validate_content.py        Validierungswerkzeug
```

## FSK18-Spezifikationen & Kennzeichnung

1. **Registries:**
   * Jeder Eintrag in `soul_registry.json`, `stages_registry.json` und `lorebooks_registry.json` trägt `"nsfw": true`.
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
4. **Validierung vor jedem Push:**
   * Vor jedem Commit `python3 tools/validate_content.py` ausführen.
