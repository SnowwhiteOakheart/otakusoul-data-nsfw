# 🔞 OtakuSoul NSFW & FSK18 Inhalts-Gateway (`otakusoul-data-nsfw`)

> **Hinweis:** Dieses Repository ist das offizielle FSK18- / NSFW-Inhalts-Gateway für die [OtakuSoul](https://github.com/SnowwhiteOakheart/OtakuSoul) Desktop-App.
> Es enthält nicht-jugendfreie Anime-Geschichten (Soul Stages), Romance- und Erotik-Szenarien, adulte Lorebooks und optionale Expressions für Charaktere.
> 
> **Status:** Privater Aufbau & Kuratierung.

---

## 🏛️ Zweck & Struktur

Dieses Repository dient als sekundäre Hub-Quelle für OtakuSoul:
* Das Haupt-Repository [`otakusoul-data`](https://github.com/SnowwhiteOakheart/otakusoul-data) bleibt 100 % Safe-for-Work (SFW) und jugendfrei.
* In diesem Repository werden FSK18-Kampagnen, adulte Szenarien und freizügige Expressions gepflegt.

### Verzeichnisstruktur
```text
soul_registry.json              Index adulter Charaktere & Varianten
stages_registry.json            Index der FSK18 Soul Stages / Szenen
lorebooks_registry.json          Index adulter Lorebooks
cards_gateway/*.png             Hub-fertige V2-Charakterkarten
stages_gateway/*.json           Hub-fertige Szenendefinitionen (mit nsfw: true)
lorebooks_gateway/*.json        Hub-fertige Lorebooks
presets/<paket>/                Quellpakete (Expressions, Hintergründe, JSONs)
tools/                          Validierungswerkzeuge
AI.md                           Wegweiser für KI-Assistenten
CONTENT_INDEX.md                Tokensparende Schnellreferenz
ROADMAP.md                      Status & geplante NSFW-Inhalte
```

---

## 🎭 Erweiterte Erotik- & Romance-Emotionen

Karten in diesem Repository können neben den 6 Standard-Emotionen (`neutral`, `happy`, `relaxed`, `surprised`, `angry`, `sad`) auch die erweiterten Romance-/NSFW-Ausdrücke mitbringen:
* **`blush`:** Starkes Erröten, Verlegenheit, Scham
* **`seductive`:** Verführerischer Blick, herausforderndes Lächeln
* **`aroused`:** Körperliche Erregung, beschleunigter Atem
* **`ecstasy`:** Lustempfinden, Höhepunkt, überwältigte Mimik
* **`afterglow`:** Erschöpfte Zufriedenheit, Post-Coital-Entspannung

---

## 🛠️ Validierung vor jedem Commit

```sh
python3 tools/validate_content.py
python3 tools/validate_content.py --sync-registry
```
