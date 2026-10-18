# 📑 OtakuSoul NSFW Content Index & Schnellreferenz

> **Zweck für AI-Agenten:** Dieses Dokument dient als tokensparende Schnellreferenz für den FSK18-/NSFW-Inhaltsbestand (`otakusoul-data-nsfw`).
>
> **Stand:** Initialer Aufbau (Private Vorbereitung).

---

## 🏛️ Inhaltskatalog nach Universen & Kampagnen

| Paket (`presets/<id>`) | Franchise / Setting | Charaktere (`soul_registry.json`) | Soul Stages (`stages_gateway/*.json`) | Aktive Lorebooks (`lorebooks_gateway/*.json`) |
|---|---|---|---|---|
| `neverness-to-everness` | Neverness to Everness (NTE) | `Mint` *(Sinnliche Spürnase)* | *(in Vorbereitung)* | - |


---

## ⚙️ Technische Spezifikationen (NSFW)

1. **`nsfw: true`:**
   * Jeder Eintrag in `stages_registry.json`, `soul_registry.json` und `lorebooks_registry.json` muss `"nsfw": true` tragen.
   * Szenen tragen unter `extensions.otakusoul_story`:
     ```json
     "notes": ["nsfw", "adult", "romance"],
     "rating": "18+"
     ```
2. **Kanonische Expressions:**
   * Standard: `neutral`, `happy`, `relaxed`, `surprised`, `angry`, `sad`
   * Erweiterte Romance/NSFW-Schlüssel: `blush`, `seductive`, `aroused`, `ecstasy`, `afterglow`
   * Erweiterte Nischen-Schlüssel: `teasing`, `fear`, `disgust`, `crying`
3. **Validierung vor dem Push:**
   * `python3 tools/validate_content.py` muss mit 0 Fehlern durchlaufen.
