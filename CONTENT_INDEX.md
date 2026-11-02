# 📑 OtakuSoul NSFW Content Index & Schnellreferenz

> **Zweck für AI-Agenten:** Dieses Dokument dient als tokensparende Schnellreferenz für den FSK18-/NSFW-Inhaltsbestand (`otakusoul-data-nsfw`).
>
> **Stand:** Öffentliches FSK18-Gateway (Veröffentlicht).

---

## 🏛️ Inhaltskatalog nach Universen & Kampagnen

| Paket (`presets/<id>`) | Franchise / Setting | Charaktere (`soul_registry.json`) | Soul Stages (`stages_gateway/*.json`) | Aktive Lorebooks (`lorebooks_gateway/*.json`) |
|---|---|---|---|---|
| `final-fantasy-vii-midnight` | Final Fantasy VII · alternative erwachsene Kontinuität | `Tifa Lockhart` (20), `Aerith Gainsborough` (22), `Cloud Strife` (21), `Sephiroth` (hier 30) | `Masken, Mako und Mitternacht` (`ff7_masken_mako_mitternacht_18.json`), vier Akte, ca. 90 Min., drei Enden | `Midgar nach Mitternacht`, `Masken & Beziehungen`, `Der ECHO-Maskenball` (alle `Final Fantasy VII – … (18+)`; Dateien `ff7_midnight_*.json`), 16 Einträge |
| `neverness-to-everness` | Neverness to Everness (NTE) | `Mint` *(Sinnliche Spürnase)* | `Nachtschicht in Hethereau` (`nachtschicht_in_hethereau.json`) | `Neverness to Everness – Esper-Intimität` (`nte_esper_intimacy.json`) |
| `no-game-no-life` | No Game No Life (NGNL) | `Jibril` *(Devote Flügel-Bibliothekarin)* | *(in Vorbereitung)* | - |
| `overlord` | Overlord | `Albedo` *(Besessene Wächteraufseherin)* | *(in Vorbereitung)* | - |
| `tokyo-first-shift` | Original, Tokio, erster Job | `Aoi Shirahama` *(Nachtproducerin)*, `Ren Kisaragi` *(Nachtbarkeeper)* | *(in Vorbereitung)* | - |
| `shared` | Universell / Übergreifend | - | - | `Adulte Romance & Erotik` (`adult_romance_eroticism.json`) |


---

## ⚙️ Technische Spezifikationen (NSFW)

1. **`nsfw: true`:**
   * Jeder Eintrag in `stages_registry.json`, `soul_registry.json` und `lorebooks_registry.json` muss `"nsfw": true` tragen.
   * Szenen tragen unter `extensions.otakusoul_story`:
     ```json
     "notes": ["nsfw", "adult", "romance"],
     "rating": "18+"
     ```
2. **App-Markierung:** Karten (`data.extensions`), Szenen und Lorebooks (`extensions`) tragen `"otakusoul_nsfw": true`;
   die App blendet sie aus, solange 18+ aus ist (Validator prüft das).
3. **Kanonische Expressions:**
   * Standard: `neutral`, `happy`, `relaxed`, `surprised`, `angry`, `sad`
   * Erweiterte Romance/NSFW-Schlüssel: `blush`, `seductive`, `aroused`, `ecstasy`, `afterglow`
   * Erweiterte Nischen-Schlüssel: `teasing`, `fear`, `disgust`, `crying`
4. **Validierung vor dem Push:**
   * `python3 tools/validate_content.py` muss mit 0 Fehlern durchlaufen.

## Paket-Titelbilder

Die fünf Pakete `neverness-to-everness`, `no-game-no-life`, `overlord`, `tokyo-first-shift` und `shared` enthalten jeweils `cover.webp` (960×540) und den Generierungsnachweis `cover_prompt.json`. Die Titelbilder sind atmosphärische, nicht explizite KI-Illustrationen. Bei Paketen mit nur einer Figur zeigt das Cover diese Figur und ihren Schauplatz; das gemeinsame Romance-Lorebook verwendet die originalen erwachsenen Figuren Aoi und Ren. Die Bilder sind als Paketassets vorbereitet; dieses Repository besitzt bislang keine Sammlungs-Registry.

## Final Fantasy VII: Maskenball-Variante · 02.11.2026

Vier DE/EN/RU-Profile, jeweils acht verschiedene Expressions und ein Ganzkörperbild; zwei Hintergründe, Titelbild, Promptnachweise und vollständige Sammlung `final_fantasy_vii_midnight_18`. Nicht explizite erwachsene Romance mit freizügiger blickdichter Mode, ohne Nacktheit. Sephiroth bleibt ein gegnerisches Spiegelbild. Die ursprüngliche SFW-Geschichte bleibt unverändert. Details: [`presets/final-fantasy-vii-midnight/README.md`](presets/final-fantasy-vii-midnight/README.md).

  * `extensions.otakusoul_music` (Englisch): Musik für ACE-Step – Szenen `set`/`style`/`moods`, Lorebooks `style`, Karten `theme`; Quelle `tools/music_settings.json`, schreiben mit `tools/set_music.py tools/music_settings.json` (`--check` prüft nur).