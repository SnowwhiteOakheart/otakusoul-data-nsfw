# 📑 OtakuSoul NSFW Content Index & Schnellreferenz

> **Zweck für AI-Agenten:** Dieses Dokument dient als tokensparende Schnellreferenz für den FSK18-/NSFW-Inhaltsbestand (`otakusoul-data-nsfw`).
>
> **Stand:** Initialer Aufbau (Private Vorbereitung).

---

## 🏛️ Inhaltskatalog nach Universen & Kampagnen

| Paket (`presets/<id>`) | Franchise / Setting | Charaktere (`soul_registry.json`) | Soul Stages (`stages_gateway/*.json`) | Aktive Lorebooks (`lorebooks_gateway/*.json`) |
|---|---|---|---|---|
| `neverness-to-everness` | Neverness to Everness (NTE) | `Mint` *(Sinnliche Spürnase)* | `Nachtschicht in Hethereau` (`nachtschicht_in_hethereau.json`) | `Neverness to Everness – Esper-Intimität` (`nte_esper_intimacy.json`) |
| `no-game-no-life` | No Game No Life (NGNL) | `Jibril` *(Devote Flügel-Bibliothekarin)* | *(in Vorbereitung)* | - |
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
