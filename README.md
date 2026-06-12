# Urlaubsplaner Card

Custom Lovelace Card für Home Assistant – zeigt Status, 14-Tage-Vorschau und alle Urlaube des [Urlaubsplaner Add-ons](https://github.com/Melle79/HA-urlaubsplaner). Urlaube können **direkt in der Karte angelegt, bearbeitet und gelöscht** werden.

[![In HACS öffnen](https://img.shields.io/badge/HACS-Repository_in_Home_Assistant_öffnen-41BDF5?logo=home-assistant&logoColor=white&style=for-the-badge)](https://my.home-assistant.io/redirect/hacs_repository/?owner=Melle79&repository=HA-urlaubsplaner-card&category=plugin)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy_me_a_coffee-melle79-FFDD00?logo=buymeacoffee&logoColor=black&style=for-the-badge)](https://buymeacoffee.com/melle79)

**Funktionen:**
- Status-Badges: Heute Urlaub / Morgen Urlaub
- Nächster (oder laufender) Urlaub mit Datum, „in X Tagen" und Dauer
- 14-Tage-Streifen: Urlaubstage (grün), Wochenenden (abgedunkelt), heute umrandet
- Komplette Urlaubsliste mit Status (Aktiv / Geplant / Vorbei)
- **Eintragen, Bearbeiten und Löschen direkt in der Karte** – Datumsauswahl per Kalender-Popup oder manuelle Eingabe
- Visueller Editor für alle Optionen
- Passt sich automatisch dem Home-Assistant-Theme an (hell/dunkel)

## Voraussetzungen

- [Urlaubsplaner](https://github.com/Melle79/HA-urlaubsplaner) Add-on **ab Version 1.0.0** (liefert die Attribute `urlaube` und `vorschau` sowie das Command-Topic)
- MQTT-Integration in Home Assistant (Änderungen werden über den Service `mqtt.publish` an das Add-on gesendet)

## Installation

### Über HACS (empfohlen)

Entweder den Badge oben anklicken (öffnet das Repository direkt in HACS auf deiner HA-Instanz) – oder manuell:

1. HACS → ⋮ (oben rechts) → **Benutzerdefinierte Repositories** → URL `https://github.com/Melle79/HA-urlaubsplaner-card`, Typ **Dashboard** → hinzufügen
2. „Urlaubsplaner Card" installieren – HACS trägt die Ressource automatisch ein
3. Browser-Cache leeren (Strg/Cmd+Shift+R)

### Manuell

1. `dist/urlaubsplaner-card.js` nach `config/www/` kopieren
2. Unter *Einstellungen → Dashboards → ⋮ → Ressourcen* hinzufügen: URL `/local/urlaubsplaner-card.js`, Typ **JavaScript-Modul**

## Konfiguration

Minimal:

```yaml
type: custom:urlaubsplaner-card
```

Alle Optionen (auch über den visuellen Editor einstellbar):

| Option | Standard | Beschreibung |
|---|---|---|
| `title` | `Urlaub` | Titel der Karte (leer = kein Titel) |
| `show_badges` | `true` | Badges „Heute / Morgen Urlaub" anzeigen |
| `show_next` | `true` | Nächsten Urlaub anzeigen |
| `show_strip` | `true` | 14-Tage-Streifen anzeigen |
| `strip_days` | `14` | Anzahl Tage im Streifen (7–14, max. laut Add-on-Vorschau) |
| `show_list` | `true` | Urlaubsliste anzeigen |
| `allow_edit` | `true` | Eintragen / Bearbeiten / Löschen in der Karte erlauben |

Beispiel – reine Anzeige ohne Bearbeitung:

```yaml
type: custom:urlaubsplaner-card
title: Urlaubsübersicht
allow_edit: false
show_strip: false
```

## Lizenz

MIT – siehe [LICENSE](LICENSE).

## Haftungsausschluss

Dies ist ein **privates Hobby-Projekt** ohne kommerziellen Hintergrund. Die Nutzung erfolgt auf eigene Gefahr – **jegliche Haftung ist ausgeschlossen** (siehe auch MIT-Lizenz). Es findet **kein Support** statt; Issues und Pull Requests werden möglicherweise nicht beantwortet.
