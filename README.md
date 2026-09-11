# CABO

Punktezähler und Regel-Nachschlagewerk für das Kartenspiel **CABO** —
als installierbare Web-App (PWA) fürs Handy.

## Funktionen

- **Punkteingabe pro Runde** mit automatischer Strafpunkt-Berechnung:
  Wer CABO ruft und nicht die niedrigste Kartensumme hat, bekommt +5.
- **Drei Spielmodi** — 10 Runden, bis 100 Punkte, oder offenes Ende.
- **Rundenkorrektur** — jede gespielte Runde lässt sich nachträglich
  bearbeiten oder löschen; Strafpunkte und Gesamtstand werden neu berechnet.
- **Statistik** — Schnitt pro Runde, gewonnene Runden, beste und schlechteste
  Runde, CABO-Rufe und wie oft die danebengingen.
- **Regelübersicht** mit allen Karten und Sonderaktionen.
- **Offline nutzbar**, der Spielstand überlebt das Schließen der App.

## Auf dem iPhone installieren

Die Seite in **Safari** öffnen → Teilen-Symbol → „Zum Home-Bildschirm".
Danach startet sie im Vollbild mit eigenem Icon und funktioniert ohne Netz.

## Lokal starten

```bash
python3 -m http.server 4173
```

Dann http://localhost:4173 aufrufen. Über einen Server statt per Doppelklick,
weil der Service Worker sonst nicht registriert wird.

## Aufbau

Eine einzelne `index.html` ohne Build-Schritt und ohne Abhängigkeiten.

| Datei | Inhalt |
|---|---|
| `index.html` | Komplette App — Markup, Styles, Logik |
| `sw.js` | Service Worker fürs Offline-Caching |
| `manifest.json` | PWA-Manifest (Name, Farben, Icons) |
| `icon-*.png` | Homescreen-Icons |

Der Spielstand liegt ausschließlich im `localStorage` des jeweiligen Geräts —
es gibt kein Backend, und nichts verlässt das Handy.
