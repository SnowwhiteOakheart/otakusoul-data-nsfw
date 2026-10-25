# 🗺️ Roadmap für otakusoul-data-nsfw (FSK 18)

> **Stand:** Initialer Aufbau. Dieses Dokument verwaltet den Status der FSK18-Charaktere, Szenen und Pakete.

---

## 0. Grundaufbau & Werkzeuge
- [x] Repository initialisieren (`main`-Branch)
- [x] Grundlegende Verzeichnisstruktur (`cards_gateway`, `stages_gateway`, `lorebooks_gateway`, `presets`, `tools`)
- [x] Registries initialisieren (`soul_registry.json`, `stages_registry.json`, `lorebooks_registry.json`)
- [x] Validierungswerkzeug `tools/validate_content.py` einrichten (mit NSFW- und Expressions-Prüfung)
- [x] Öffentliches GitHub-Repository `SnowwhiteOakheart/otakusoul-data-nsfw` verknüpfen und veröffentlichen

---

## 1. Erste NSFW-Pakete & Charaktere
- [x] **Mint (NTE):** FSK18-/Romance-Charakterkarte mit 11 Emotions-Platzhaltern (`presets/neverness-to-everness/mint.json` & `mint.png`, `cards_gateway/mint.png`)
- [x] **Aoi Shirahama und Ren Kisaragi:** originale 21-jährige Berufseinsteiger in Tokio, je 15 Emotionsbilder plus Kartenporträt (`presets/tokyo-first-shift/`)
- [x] **Albedo (Overlord):** FSK18-/Romance-Charakterkarte, Kartenporträt und 15 Emotionsbilder (`presets/overlord/`)
- [x] Erste FSK18-Soul-Stage für Mint vorbereiten (`presets/neverness-to-everness/scenes/nachtschicht_in_hethereau.json`)
- [x] Adulte Lorebooks für Erotik- und Romance-Begriffe anlegen (`nte_esper_intimacy.json`, `adult_romance_eroticism.json`)
- [x] App-Markierung `extensions.otakusoul_nsfw` in allen Karten (JSON, Preset- und Gateway-PNG), Szenen und Lorebooks;
  Validator meldet fehlende Markierung als Fehler
- [x] Mint: Alter ausdrücklich volljährig (21) in allen Sprachen
- [x] Integration mit der OtakuSoul-App (Multi-Hub) testen – Live-Test mit öffentlichem Repository
  in `modules::hub::tests::nsfw_hub_live_registry_check` erfolgreich verifiziert.



## Paket-Titelbilder (25.10.2026)

- [x] Alle fünf Pakete mit individuellen Titelbildern als `presets/<paket>/cover.webp` (960×540 WebP) ausgestattet; vollständig bekleidete Figuren, passende Schauplätze und Prompt-/Referenznachweise in `cover_prompt.json`.
