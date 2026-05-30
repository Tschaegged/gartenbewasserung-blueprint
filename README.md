# 🌿 Gartenbewässerung – Home Assistant Blueprint

Ein flexibles Blueprint für automatische Gartenbewässerung mit Wettercheck, Bodenfeuchte und Push-Benachrichtigungen.

## Features

- **Mehrere Ventile** – beliebig viele Ventile werden nacheinander bewässert
- **Bis zu 3 Tageszeiten** – Hauptzeit + 2 optionale weitere Zeiten
- **Wettercheck** – überspringt die Bewässerung bei:
  - Regen (vorhergesagt oder aktuell)
  - Hoher Regenwahrscheinlichkeit (konfigurierbar)
  - Frost (aktuelle Temperatur unter Schwellwert)
  - Zu niedrigem Tagesmaximum (Nutztemperatur)
- **Bodenfeuchtigkeitssensor** – optionaler Sensor überspringt Bewässerung wenn Boden bereits feucht
- **Saisonsteuerung** – Bewässerung nur zwischen konfigurierbaren Monaten aktiv
- **Push-Benachrichtigungen** – bei Abschluss oder übersprungener Bewässerung

## Installation

### Über HACS (empfohlen)

1. HACS öffnen → **Automations** → Drei-Punkte-Menü → **Custom repositories**
2. URL: `https://github.com/Tschaegged/gartenbewasserung-blueprint` – Kategorie: **Automation**
3. Blueprint suchen und importieren

### Manuell

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://raw.githubusercontent.com/Tschaegged/gartenbewasserung-blueprint/main/blueprints/automation/gartenbewasserung.yaml)

Oder direkt in Home Assistant:  
**Einstellungen → Automationen → Blueprints → Blueprint importieren** und folgende URL eingeben:

```
https://raw.githubusercontent.com/Tschaegged/gartenbewasserung-blueprint/main/blueprints/automation/gartenbewasserung.yaml
```

## Konfiguration

| Parameter | Beschreibung | Standard |
|-----------|-------------|---------|
| Bewässerungszeit | Uhrzeit der täglichen Bewässerung | – |
| Bewässerungsventile | Ventile (switch/valve) in Reihenfolge | – |
| Bewässerungsdauer | Minuten pro Ventil | 20 min |
| Wettervorhersage | Weather-Entität für Prüfungen | – |
| Regenvorausschau | Stunden voraus auf Regen prüfen | 12 h |
| Max. Regenwahrscheinlichkeit | Schwellwert für Skip | 40 % |
| Frostschutz | Min. aktuelle Temperatur | 5 °C |
| Nutztemperatur | Min. vorhergesagtes Tagesmaximum | 12 °C |
| Saisonbeginn | Erster aktiver Monat | April (4) |
| Saisonende | Letzter aktiver Monat | Oktober (10) |
| Bodenfeuchtigkeitssensor | Optionaler Sensor | – |
| Feuchtigkeitsschwellwert | Skip wenn ≥ diesem Wert | 60 % |

## Anforderungen

- Home Assistant 2024.6 oder neuer (wegen `weather.get_forecasts`)
- Eine Wetterentität (z.B. `weather.forecast_home`)
- Ventile als `switch`- oder `valve`-Entitäten

## Lizenz

MIT
