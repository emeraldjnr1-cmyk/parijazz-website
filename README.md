# parijazz.de — Site-Export

Dieser Ordner enthält den vollständigen Inhalts-Export der Website **https://parijazz.de/**.

```
.
├── README.md                       ← diese Datei
├── pages/                          ← Texte aller Seiten als Markdown
│   ├── startseite.md
│   ├── sourcing.md
│   ├── operatingsystem.md
│   ├── chinareise.md
│   ├── markteintritt-hersteller.md
│   ├── netzwerk-and-partner.md
│   ├── ecommerce.md                ← Pari Jazz Commerce Network
│   ├── kontakt.md
│   ├── cooming-soon.md             ← alter Menüpunkt „E-Commerce" (Coming-Soon-Platzhalter)
│   └── rechtsdokumentddd.md        ← Datenschutz-URL (leer beim Abruf)
└── assets/
    └── images/                     ← alle Bilder von onecdn.io (Original-Größe „/lg")
```

## Seiten-Inventar

| Seite | URL | Datei |
|---|---|---|
| Startseite | https://parijazz.de/startseite | `pages/startseite.md` |
| Sourcing | https://parijazz.de/sourcing | `pages/sourcing.md` |
| Operating System | https://parijazz.de/operatingsystem | `pages/operatingsystem.md` |
| China Reise | https://parijazz.de/chinareise | `pages/chinareise.md` |
| Markteintritt für Hersteller | https://parijazz.de/markteintritt-hersteller | `pages/markteintritt-hersteller.md` |
| Netzwerk & Partner | https://parijazz.de/netzwerk-and-partner | `pages/netzwerk-and-partner.md` |
| **E-Commerce (Pari Jazz Commerce)** | **https://parijazz.de/ecommerce** | **`pages/ecommerce.md`** |
| Kontakt | https://parijazz.de/kontakt | `pages/kontakt.md` |
| E-Commerce (alt, Coming Soon) | https://parijazz.de/cooming-soon | `pages/cooming-soon.md` |
| Datenschutz | https://parijazz.de/rechtsdokumentddd | `pages/rechtsdokumentddd.md` (leer) |

## Bilder

Alle Bilder wurden in voller Auflösung (`/lg`-Variante von onecdn.io) heruntergeladen
und liegen unter `assets/images/{uuid}.{ext}`. Die jeweilige Markdown-Datei
referenziert die Bilder per relativem Pfad, sodass die Zuordnung Seite ↔ Bild direkt
sichtbar ist.

Insgesamt **94 Bilder** in den Formaten PNG, JPG, SVG und WebP (inkl. 4 Unsplash-Phasenbilder unter `unsplash-*.jpg`).

## Social

- Instagram: https://www.instagram.com/parijazz_
- YouTube:   https://www.youtube.com/@PariJazzz
- TikTok:    https://www.tiktok.com/@pari.jazz

## Hinweise

- Texte sind sinngemäß 1:1 aus dem CMS übernommen (inkl. originaler Tippfehler wie
  „Cooming Soon").
- Reine Layout-Wiederholungen (Header / Footer auf jeder Seite) sind nicht pro Seite
  dupliziert, sondern unter „Footer" in `startseite.md` zentral hinterlegt.
- Formulare wurden als Feldliste exportiert (kein HTML-Markup, da die Form-Endpoints
  nicht öffentlich sind).
- Die Datenschutz-URL `rechtsdokumentddd` liefert beim direkten Abruf den
  Startseiten-Inhalt zurück — der eigentliche Datenschutz-Inhalt war im Quelltext nicht
  abrufbar.
