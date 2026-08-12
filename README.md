# 🚀 Nebula Blaster

Ein touch-optimierter **Space Shooter** fürs Handy – geschrieben in reinem HTML5 Canvas + JavaScript, ohne Framework, ohne Build-Schritt. Räum die ALiens ab!

Installierbar als **PWA**: zum Homescreen hinzufügen und **offline** spielen.

![Icon](icons/alien-512.png)

> Zwei App-Icons liegen bei: das Alien-Gesicht (`icons/alien.svg`, Standard) und die Szene mit Schiff (`icons/icon.svg`).

## Spielen

- **Steuerung:** Finger auf den Bildschirm legen und ziehen – das Schiff folgt.
- **Schießen:** passiert automatisch.
- **Ziel:** so viele Aliens wie möglich abschießen, Wellen überstehen, Highscore knacken.

### Gegner & Extras

| Element | Beschreibung |
|---|---|
| 🟢 Standard-Alien | 1 Treffer, 10 Punkte |
| 🟩 Zickzack-Alien | 2 Treffer, bewegt sich seitlich, 15 Punkte |
| 🟣 Tank-Alien | 4 Treffer, langsam, 30 Punkte |
| ⭐ Powerup | Dreifach-Schuss für kurze Zeit |
| ❤️ Leben | 3 Leben, Highscore wird lokal gespeichert |

Die Wellen werden mit jeder Runde schwerer (mehr Gegner, schnelleres Tempo).

## Am Handy installieren

1. Seite im mobilen Browser öffnen (siehe *Live-Demo* unten).
2. Browser-Menü → **„Zum Startbildschirm hinzufügen"**.
3. Über das App-Icon starten – läuft im Vollbild und offline.

## Lokal starten

Weil ein Service Worker verwendet wird, sollte die Seite über einen lokalen Server laufen (nicht per `file://`):

```bash
# Python
python3 -m http.server 8080
# dann http://localhost:8080 öffnen
```

Oder einfach `index.html` direkt im Browser öffnen – das Spiel läuft auch so, nur der Offline-Cache greift dann nicht.

## Auf GitHub Pages veröffentlichen

Es liegt ein fertiger Workflow unter `.github/workflows/deploy.yml`. Nach dem Push:

1. Im Repo auf **Settings → Pages** gehen.
2. Bei **Build and deployment → Source** die Option **GitHub Actions** wählen.
3. Fertig – bei jedem Push auf `main` wird automatisch deployt.

Die Live-Demo liegt dann unter:
`https://<dein-username>.github.io/nebula-blaster/`

## Projektstruktur

```
nebula-blaster/
├── index.html              # das komplette Spiel (Canvas + Logik)
├── manifest.webmanifest    # PWA-Manifest
├── sw.js                   # Service Worker (Offline-Cache)
├── icons/                  # App-Icons (SVG + PNG)
└── .github/workflows/      # Auto-Deploy nach GitHub Pages
```

## Technik

- Reines HTML5 `<canvas>`, keine Abhängigkeiten.
- Touch- und Maussteuerung.
- `requestAnimationFrame`-Game-Loop mit Partikeleffekten.
- DPR-Scaling für scharfe Darstellung auf Retina-/Handy-Displays.
- Highscore via `localStorage`.

## Lizenz

MIT – siehe [LICENSE](LICENSE).
