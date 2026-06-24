# Level Popup System — Pari Jazz Commerce E-Commerce Page

## OVERVIEW

On the E-Commerce page, the **Commerce Launch** and **Commerce Growth** program cards each contain clickable Level buttons. When a user clicks any Level button, a **modal popup** opens showing the FULL curriculum detail for that level from the Lehrplan.

This is the most important interactive feature on the E-Commerce page.

---

## HOW IT WORKS (User Flow)

```
User lands on E-Commerce page
        ↓
Sees 4 program cards side by side
        ↓
Notices "Level 1 | Level 2 | Level 3 | Level 4" pill buttons
inside Commerce Launch or Commerce Growth card
        ↓
Clicks "Level 1"
        ↓
Dark overlay fades in over entire page
        ↓
Modal card scales + fades in from center
        ↓
Full Level 1 curriculum detail displayed inside modal
        ↓
User reads, scrolls inside modal if needed
        ↓
Clicks X button or clicks outside modal or presses Escape
        ↓
Modal fades + scales out, overlay fades out
        ↓
User is back on E-Commerce page
```

---

## LEVEL BUTTON DESIGN (inside program cards)

```
Section label above buttons:
"Inhalte nach Level:" (small, Inter, gray, 13px uppercase)

Button row:
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│  Level 1 │ │  Level 2 │ │  Level 3 │ │  Level 4 │
└──────────┘ └──────────┘ └──────────┘ └──────────┘

For Commerce Growth, add a 5th special button:
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐
│  Level 1 │ │  Level 2 │ │  Level 3 │ │  Level 4 │ │  ★ Level +   │
└──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────────┘
```

### Button CSS
```css
.level-btn {
  display:          inline-flex;
  align-items:      center;
  gap:              6px;
  padding:          8px 16px;
  border-radius:    999px;
  border:           1.5px solid #C9A96E;
  background:       transparent;
  color:            #1A1A1A;
  font-family:      Inter;
  font-size:        13px;
  font-weight:      600;
  letter-spacing:   0.3px;
  cursor:           pointer;
  transition:       all 200ms ease;
}

.level-btn:hover {
  background:       #1946BD;
  border-color:     #1946BD;
  color:            #FFFFFF;
  transform:        translateY(-2px);
  box-shadow:       0 4px 16px rgba(25, 70, 189, 0.25);
}

/* Special Level + button for Commerce Growth */
.level-btn.level-plus {
  background:       linear-gradient(135deg, #C9A96E, #EAD7A1);
  border-color:     #C9A96E;
  color:            #1A1A1A;
  font-weight:      700;
}

.level-btn.level-plus:hover {
  background:       linear-gradient(135deg, #1946BD, #0A1628);
  border-color:     #1946BD;
  color:            #FFFFFF;
}
```

---

## MODAL DESIGN

### Overlay
```css
.modal-overlay {
  position:         fixed;
  inset:            0;
  background:       rgba(10, 22, 40, 0.85);  /* deep navy at 85% */
  z-index:          1000;
  display:          flex;
  align-items:      center;
  justify-content:  center;
  padding:          24px;
  backdrop-filter:  blur(4px);
  animation:        overlayIn 250ms ease forwards;
}

@keyframes overlayIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

### Modal Card
```css
.modal-card {
  background:       #FFFFFF;
  border-radius:    24px;
  width:            100%;
  max-width:        680px;
  max-height:       85vh;
  overflow-y:       auto;
  padding:          48px;
  position:         relative;
  box-shadow:       0 32px 80px rgba(10, 22, 40, 0.4);
  animation:        modalIn 300ms cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
}

@keyframes modalIn {
  from {
    opacity:    0;
    transform:  scale(0.92) translateY(16px);
  }
  to {
    opacity:    1;
    transform:  scale(1) translateY(0);
  }
}

/* Custom scrollbar inside modal */
.modal-card::-webkit-scrollbar { width: 4px; }
.modal-card::-webkit-scrollbar-track { background: #F7F4EE; }
.modal-card::-webkit-scrollbar-thumb { background: #C9A96E; border-radius: 999px; }
```

### Modal Header
```
┌─────────────────────────────────────────────┐
│ COMMERCE LAUNCH · LEVEL 1          [  ✕  ] │  ← gold eyebrow + close btn
│                                             │
│ Unternehmerisches Fundament,                │  ← Playfair H3 title
│ Mindset, Markenaufbau &                     │
│ Profitable Produktideen                     │
│                                             │
│ ─────────────────────── (gold divider)      │
│                                             │
│ Ziel: Du entwickelst die Denkweise eines    │  ← objective paragraph
│ Markeninhabers...                           │
└─────────────────────────────────────────────┘
```

```css
/* Eyebrow */
.modal-eyebrow {
  font-family:      Inter;
  font-size:        12px;
  font-weight:      700;
  letter-spacing:   2px;
  text-transform:   uppercase;
  color:            #C9A96E;
  margin-bottom:    12px;
}

/* Level title */
.modal-title {
  font-family:      Playfair Display;
  font-size:        32px;
  font-weight:      500;
  color:            #1A1A1A;
  line-height:      1.3;
  margin-bottom:    24px;
}

/* Gold divider */
.modal-divider {
  height:           2px;
  background:       linear-gradient(90deg, #C9A96E, transparent);
  margin-bottom:    24px;
  border-radius:    999px;
}

/* Objective text */
.modal-objective {
  font-family:      Inter;
  font-size:        16px;
  color:            #475569;
  line-height:      1.7;
  margin-bottom:    32px;
  padding:          16px 20px;
  background:       #F7F4EE;
  border-left:      3px solid #C9A96E;
  border-radius:    0 8px 8px 0;
}

/* Close button */
.modal-close {
  position:         absolute;
  top:              24px;
  right:            24px;
  width:            40px;
  height:           40px;
  border-radius:    50%;
  border:           1.5px solid #EAD7A1;
  background:       #F7F4EE;
  color:            #1A1A1A;
  font-size:        18px;
  cursor:           pointer;
  display:          flex;
  align-items:      center;
  justify-content:  center;
  transition:       all 200ms ease;
}

.modal-close:hover {
  background:       #1946BD;
  border-color:     #1946BD;
  color:            #FFFFFF;
}
```

### Modal Body — Content Sections
```
Each topic group inside the modal:

┌─────────────────────────────────────────┐
│ 📌 FOKUS MINDSET                        │  ← section heading
│                                         │
│  ✓  Unternehmerisches Denken statt      │  ← checkmark bullets
│     "Seller-Hopping"                    │
│  ✓  Aufbau einer klaren 12-Monats-      │
│     Routine                             │
│  ✓  Fokus- und Umsetzungsstrategien     │
│  ✓  Risikomanagement im E-Commerce      │
└─────────────────────────────────────────┘
```

```css
/* Section heading inside modal */
.modal-section-heading {
  font-family:      Inter;
  font-size:        11px;
  font-weight:      700;
  letter-spacing:   2px;
  text-transform:   uppercase;
  color:            #1946BD;
  margin:           24px 0 12px 0;
  display:          flex;
  align-items:      center;
  gap:              8px;
}

/* Bullet item */
.modal-bullet {
  display:          flex;
  align-items:      flex-start;
  gap:              10px;
  font-family:      Inter;
  font-size:        15px;
  color:            #1A1A1A;
  line-height:      1.6;
  padding:          6px 0;
  border-bottom:    1px solid #F7F4EE;
}

/* Gold checkmark */
.modal-bullet::before {
  content:          "✓";
  color:            #C9A96E;
  font-weight:      700;
  font-size:        14px;
  margin-top:       2px;
  flex-shrink:      0;
}
```

### Modal — Included Extras Box
```
┌─────────────────────────────────────────────┐
│  DU ERHÄLTST ZUSÄTZLICH                     │  ← gold bg box
│                                             │
│  📄 Fokus- & Prioritäten-Planer             │
│  📄 Zielgruppen-Avatar-Workbook             │
│  📄 Wettbewerbsanalyse-Templates           │
│  📄 Plattform-Vergleichsmatrix             │
└─────────────────────────────────────────────┘
```

```css
.modal-extras-box {
  background:       linear-gradient(135deg, #EAD7A1 0%, #F7F4EE 100%);
  border:           1.5px solid #C9A96E;
  border-radius:    16px;
  padding:          20px 24px;
  margin:           24px 0;
}

.modal-extras-title {
  font-family:      Inter;
  font-size:        11px;
  font-weight:      700;
  letter-spacing:   2px;
  text-transform:   uppercase;
  color:            #1946BD;
  margin-bottom:    12px;
}

.modal-extras-item {
  font-family:      Inter;
  font-size:        14px;
  color:            #1A1A1A;
  padding:          4px 0;
  display:          flex;
  align-items:      center;
  gap:              8px;
}
```

### Modal — Ergebnis (Result) Summary Box
```
┌─────────────────────────────────────────────┐
│  ERGEBNIS                                   │  ← always last item
│                                             │
│  "Du weißt exakt, welche Produkte           │
│  wirtschaftlich Sinn ergeben, welche        │
│  Plattform geeignet ist und was es          │
│  bedeutet, eine echte Marke aufzubauen."    │
└─────────────────────────────────────────────┘
```

```css
.modal-result-box {
  background:       #1946BD;
  border-radius:    16px;
  padding:          24px 28px;
  margin-top:       32px;
}

.modal-result-label {
  font-family:      Inter;
  font-size:        11px;
  font-weight:      700;
  letter-spacing:   2px;
  text-transform:   uppercase;
  color:            #C9A96E;
  margin-bottom:    10px;
}

.modal-result-text {
  font-family:      Playfair Display;
  font-size:        18px;
  font-style:       italic;
  color:            #FFFFFF;
  line-height:      1.6;
}
```

---

## FULL CONTENT FOR EVERY LEVEL POPUP

### ═══════════════════════════════════════
### COMMERCE LAUNCH — LEVEL 1
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE LAUNCH · LEVEL 1
**Title:** Unternehmerisches Fundament, Mindset, Markenaufbau & Profitable Produktideen
**Objective:** Du entwickelst die Denkweise eines Markeninhabers, verstehst die wichtigsten E-Commerce-Plattformen, baust dein Markenverständnis auf und lernst, welche Produkte sich wirklich für den Markt eignen.

**Section — FOKUS MINDSET**
- Unternehmerisches Denken statt „Seller-Hopping"
- Aufbau einer klaren 12-Monats-Routine
- Fokus- und Umsetzungsstrategien
- Risikomanagement im E-Commerce

**Section — MARKTVERSTÄNDNIS & PRODUKTIDEEN**
- Analyse von Amazon, Otto, Kaufland und eBay
- Verständnis von Marktplatz-Algorithmen
- Einführung in TikTok Shop & Social Commerce
- Verkaufspsychologie und Kaufverhalten
- Zielgruppenanalyse & Positionierung
- Wirtschaftlichkeitsprüfung von Produkten
- Margen-, Cashflow- und Preisberechnung

**Section — MARKENAUFBAU — WAS EINE MARKE IST**
- Was ist eine Marke & warum sie entscheidend ist
- Markenpositionierung: Werte, USP & Zielgruppe definieren
- Vom Produkt zur Marke — strategischer Aufbau
- Markenname, Logo & erste Markenpräsenz aufbauen

**Section — MARKENAUFBAU PRAXISERFAHRUNG (EXPERTE)**
- Wie Dilan ihre Marke aufgebaut hat — Learnings
- Brand-Identität: Logo, Farben, Packaging — wie starten
- Community & Social Media Präsenz als Marke aufbauen

**Section — STEUERLICHE GRUNDLAGEN (EXPERTE)**
- Kleinunternehmerregelung vs. Regelbesteuerung
- GmbH vs. UG vs. Einzelunternehmen
- Umsatzsteuer beim Import & EU-Erwerb
- Steuernummer, USt-ID & Gewerbeanmeldung
- Typische Steuerfehler von E-Commerce-Einsteigern

**Section — BUCHHALTUNG & STRUKTUR (EXPERTE)**
- Buchhaltungs-Setup für Amazon-Seller
- Bankkonten & Cashflow-Struktur aufbauen
- Jahresabschluss & Steuererklärung — Überblick

**Extras Box:**
- Fokus- & Prioritäten-Planer
- Zielgruppen-Avatar-Workbook
- Wettbewerbsanalyse-Templates
- Plattform-Vergleichsmatrix
- Unternehmensstruktur-Entscheidungsmatrix

**Ergebnis:** Du weißt exakt, welche Produkte wirtschaftlich Sinn ergeben, welche Plattform geeignet ist und was es bedeutet, eine echte Marke aufzubauen.

---

### ═══════════════════════════════════════
### COMMERCE LAUNCH — LEVEL 2
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE LAUNCH · LEVEL 2
**Title:** Produktentwicklung, Rechtssicherheit & Herstellersourcing
**Objective:** Du entwickelst ein marktfähiges Produkt, sicherst dich rechtlich ab und baust eine geprüfte Lieferkette mit verlässlichem Hersteller auf.

**Section — PRODUKTENTWICKLUNG & SOURCING**
- Softwaregestützte Produkt- und Nischenanalyse
- Suchvolumen-, Trend- und Wettbewerbsanalysen
- Produktoptimierung statt Produktkopie
- Musterbestellungen professionell durchführen
- Herstellerrecherche in China
- Fabriken von Trading Companies unterscheiden
- Preisverhandlungen und MOQ-Verhandlungen
- Übersicht Kalkulation & Reverse-Sourcing

**Section — COMPLIANCE & PRODUKTSICHERHEIT (EXPERTE)**
- CE-Kennzeichnung, REACH, RoHS & Produktsicherheit
- LUCID, ElektroG und Importeurspflichten
- Qualitätskontrollen und Produktionsüberwachung

**Section — MARKENANMELDUNG & PATENTRECHT (EXPERTE)**
- Markenanmeldung Schritt für Schritt (EUIPO/DPMA)
- Patentrecherche — was darf ich, was nicht
- Amazon Brand Registry einrichten
- Markenschutz & Abmahnungen vermeiden
- Internationale Markenrechte verstehen

**Section — PRODUKTHAFTPFLICHT & VERSICHERUNGEN (EXPERTE)**
- Produkthaftung und Risikominimierung
- Die richtige Produkthaftpflichtversicherung wählen
- Importeurspflichten & Haftungsrisiken
- Versicherungs-Checkliste für dein Produkt

**Section — VERTRAGSRECHT (EXPERTE)**
- Lieferantenverträge mit China richtig aufsetzen
- AGB, Impressum & Datenschutz für Amazon-Seller
- NDA & Exklusivitätsvereinbarungen mit Herstellern
- Haftungsklauseln & Rückgaberecht im B2C

**Section — QUALITY INSPECTION CHINA (EXPERTE)**
- Was ist Quality Inspection & warum vor Import Pflicht
- Wie eine Vor-Ort-Prüfung in China abläuft
- Checkliste: Maße, Material, Funktion, Verpackung
- Was tun wenn die Ware nicht passt

**Section — PAYMENT & ZAHLUNGEN NACH CHINA (EXPERTE)**
- Was ist WorldFirst & warum für Seller relevant
- Vorteile: Wechselkurs, Gebühren, Geschwindigkeit
- Account einrichten & Amazon-Zahlungen empfangen
- Lieferantenrechnung sicher & günstig bezahlen

**Extras Box:**
- Nischenanalyse-Blueprints
- Compliance-Checklisten
- RFQ-Anfragevorlagen (Deutsch, Englisch & Chinesisch)
- Qualitätsprüfungs-Vorlagen
- Dokumenten-Guides für PI, CI und Packlisten
- Quality Inspection Protokoll
- WorldFirst Zugang & Onboarding

**Exklusiver Zugang:**
- Herstellerzugang (geprüftes Netzwerk)
- Versicherungs-Partner & Markenrechts-Kanzleien
- Lokale Qualitätsprüfer in China

**Ergebnis:** Du verfügst über ein rechtssicheres Produkt, einen verlässlichen Hersteller, geprüfte Lieferkette und sichere Zahlungsstruktur.

---

### ═══════════════════════════════════════
### COMMERCE LAUNCH — LEVEL 3
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE LAUNCH · LEVEL 3
**Title:** Import, Logistik & Professioneller Produkt-Launch
**Objective:** Du bringst dein Produkt sicher nach Europa und startest mit professionellem Listing, Grafiken und ersten Werbekampagnen.

**Section — IMPORT & LOGISTIK (EXPERTEN)**
- Importprozesse und Zollabwicklung
- EORI-Nummer & Verzollung
- Incoterms verständlich erklärt
- Auswahl der richtigen Versandart
- Lager- und Fulfillment-Strukturen
- Amazon FBA vs. externe Logistik
- Liquiditäts- und Nachbestellplanung

**Section — SEO & LISTING-OPTIMIERUNG**
- Keyword-Recherche und SEO — Strategie & Vorgehen
- Listing-Optimierung: Titel, Bullets, Beschreibung
- Erstellung verkaufsstarker Bilder und Texte
- Algorithmus-Launch für die ersten 14 Tage
- Bewertungsstrategie aufbauen

**Section — SEO MIT TOOLS & PPC EINSTIEG (EXPERTE)**
- Keyword-Recherche mit Tool-Stack live erklärt
- Amazon SEO: wie der Algorithmus Keywords bewertet
- Amazon PPC Grundlagen — Kampagnentypen
- Erste Sponsored Products Kampagne aufsetzen
- Auto vs. Manuelle Kampagnen — wann was
- ACoS & RoAS verstehen und richtig nutzen

**Section — LISTING-GRAFIKEN & CREATIVE (EXPERTE)**
- Workflow: vom Briefing zur fertigen Grafik
- Infografiken, Lifestyle-Bilder & A+ Content

**Extras Box:**
- Incoterm-Spickzettel
- Zoll-Leitfäden
- SEO-Templates
- Foto- & Video-Briefings
- Launch-Tag-Checkliste
- Kampagnen-Templates

**Exklusive Infrastruktur:**
- Zugang zu Import-, Logistik- und Fulfillment-Netzwerk
- Sonderkonditionen für Logistiklösungen
- Kontakte zu geprüften Freight Forwardern
- Direktzugang Zoll

**Ergebnis:** Dein Produkt ist am Markt, professionell positioniert und mit einer funktionierenden Werbe- und Logistikstruktur ausgestattet.

---

### ═══════════════════════════════════════
### COMMERCE LAUNCH — LEVEL 4
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE LAUNCH · LEVEL 4
**Title:** Advertising, Optimierung & Nachhaltige Skalierung
**Objective:** Du lernst, Werbebudgets profitabel einzusetzen, dein Geschäft mit Daten zu steuern und langfristig zu stabilisieren.

**Section — INHALTE**
- Auswertung von Werbedaten & KPI-Reporting
- Identifikation profitabler Keywords
- Budgetkontrolle und Margenschutz
- Angebotsoptimierung
- Nachbestellung Planung
- Vermeidung von Out-of-Stock-Situationen
- Vorbereitung auf die nächste Wachstumsphase

**Section — PPC-OPTIMIERUNG & MASTERY (EXPERTE)**
- PPC-Optimierung deep dive
- Negative Keywords strategisch einsetzen
- Skalierung erfolgreicher Kampagnen
- Halo Tracker — TACoS & Halo-Effekt verstehen
- Search-Term Miner — profitable Begriffe finden
- Reach Pilot — Skalierungspotenziale erkennen
- Daypart Pilot — stärkste Tagessegmente nutzen
- Spend-Leak-Scanner — Wasted Spend aufdecken
- Bid Pilot — Gebote per RoAS-Korridor optimieren
- ASIN Cleaner & Review Scanner

**Tools Included:**
- Halo Tracker — TACoS & Halo-Effekt pro ASIN
- Search-Term Miner — profitable Suchbegriffe finden
- Reach Pilot — Skalierungspotenziale erkennen
- Negative Builder — Strategische Negatives
- Daypart Pilot — Bid-Boost-Empfehlungen
- Spend-Leak-Scanner — Wasted Spend aufdecken
- ASIN Cleaner — Unterperformende ASINs pausieren
- Review Scanner — Removal-Requests erstellen
- Bid Pilot — Gebote per RoAS-Korridor optimieren

**Ergebnis:** Du verfügst über ein profitables System zur Umsatzsteigerung und kannst datenbasiert skalieren.

---

### ═══════════════════════════════════════
### COMMERCE GROWTH — LEVEL 1
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE GROWTH · LEVEL 1
**Title:** Advanced Analytics, Controlling & Profitabilität
**Objective:** Mehr Gewinn aus bestehenden Umsätzen erzielen durch tiefgehende Datenanalyse und Cashflow-Optimierung.

**Section — INHALTE**
- Tiefgehende Profitabilitätsanalysen
- TACoS-Steuerung
- Cashflow-Optimierung & versteckte Kosten eliminieren
- Conversion-Optimierung live am Produkt
- Produkterweiterung / Produktverbesserung
- Controlling-Dashboard einrichten & täglich nutzen

**Section — ADS-EXPERTE**
- TACoS-Steuerung verstehen & anwenden
- Professionelle Split-Testing-Prozesse
- Halo Tracker Advanced — Parent/Child-ASIN Analyse
- ASIN Cleaner — unterperformende ASINs

**Tools Included:**
- Halo Tracker — TACoS-Steuerung & Halo-Effekt auf ASIN-Ebene
- ASIN Cleaner — Unterperformende ASINs per Bulk-Sheet pausieren
- Premium Dashboard — Vollständige Profitabilitätsübersicht in Echtzeit
- CRO-Protokolle — Strukturierte Split-Testing-Prozesse für Listings

**Ergebnis:** Mehr Gewinn bei gleichem Umsatz durch datenbasierte Optimierung.

---

### ═══════════════════════════════════════
### COMMERCE GROWTH — LEVEL 2
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE GROWTH · LEVEL 2
**Title:** High-End Advertising & Omnichannel Marketing
**Objective:** Werbekampagnen profitabel und kontrolliert über alle Kanäle skalieren.

**Section — ADVANCED AMAZON PPC (EXPERTE)**
- Advanced Amazon PPC — Kampagnenstrukturen für Profis
- Bulk-Sheet-Automatisierungen meistern
- Plattformübergreifende Budgetsteuerung
- Attribution & Reporting über alle Kanäle

**Section — GOOGLE ADS FÜR E-COMMERCE (EXPERTE)**
- Google Shopping — Setup & Strategie
- Performance Max aufsetzen & optimieren
- Search Campaigns für Marken-Traffic
- Google Analytics & Conversion-Tracking
- Google Ads Reporting & Optimierung

**Section — META ADS FÜR MARKEN (EXPERTIN)**
- Meta Ads für E-Commerce-Marken — Setup & Strategie
- Creative-Strategie: Facebook & Instagram
- Retargeting-Funnels aufbauen
- Lookalike Audiences & Skalierung
- Meta Ads Reporting & Budget-Kontrolle

**Tools Included:**
- PPC Audit — Multi-Section-Performance-Report
- Bid Pilot — RoAS-Korridor-Optimierung
- Spend-Leak-Scanner — Wasted Spend aufdecken
- Search-Term Miner — Profitable Suchbegriffe
- Reach Pilot — Skalierungspotenziale
- Daypart Pilot — Bid-Boosts nach Tageszeit

**Ergebnis:** Höhere Reichweite, mehr Umsatz und maximale Kontrolle über Werbebudgets.

---

### ═══════════════════════════════════════
### COMMERCE GROWTH — LEVEL 3
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE GROWTH · LEVEL 3
**Title:** Multichannel Expansion, Automatisierung & Kundensupport
**Objective:** Unabhängigkeit von einer Plattform durch Expansion, automatisierte Prozesse und skalierbaren Kundensupport.

**Section — MULTICHANNEL EXPANSION**
- Expansion auf Otto, Kaufland und eBay
- ERP-Systeme professionell aufsetzen
- Automatisierte Prozesse — Bestellung bis Versand
- Cross-Selling-Strategien
- Erhöhung des Customer Lifetime Value
- Schnittstellen-Architektur & System-Integration

**Section — KUNDENSUPPORT-AUTOMATISIERUNG (EXPERTE)**
- Vorstellung des Kundensupport-Tools
- Setup & Integration mit Amazon, Otto, Kaufland
- Automatisierte Antworten & Ticket-Management live
- Praxisbeispiel: von 500 auf 5.000 Bestellungen/Monat

**Section — HANDEL & STATIONÄRER HANDEL (EXPERTE)**
- Von Online zu Offline — wann der Schritt Sinn ergibt
- Großhandel & Handelsvertreter — Modell & Umsetzung
- Listung bei Handelsketten — Anforderungen & Prozesse
- POS-Material, Verpackung & Handelskonditionen

**Extras Box:**
- Schnittstellen-Architektur-Blueprint
- Automatisierungs-Workflows
- Nico Felsch Tool-Zugang (Kundensupport)

**Ergebnis:** Ein skalierbares Unternehmen mit mehreren Umsatzkanälen und automatisiertem Kundensupport.

---

### ═══════════════════════════════════════
### COMMERCE GROWTH — LEVEL 4
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE GROWTH · LEVEL 4
**Title:** Logistik-Skalierung, Container-Import & Sortimentserweiterung
**Objective:** Lieferketten für hohe Umsätze absichern und das Produktsortiment ohne Eigenkapital erweitern.

**Section — CONTAINER-IMPORT & LOGISTIK**
- Container-Import: FCL vs. LCL — wann was
- Frachtkostenoptimierung & Konsolidierung von Lieferungen
- Pre-Fulfillment-Strukturen für hohes Volumen
- Vermeidung von Out-of-Stock-Situationen
- Großvolumige Importstrategien
- Strategien zur Cashflow-Optimierung
- Lager-Tour Hamburg — On-Site-Video

**Section — LOGISTIK-SKALIERUNG (EXPERTE)**
- Großvolumige Importstrategien live erklärt
- Out-of-Stock bei hohen Umsätzen verhindern
- Fulfillment-Lager Hamburg — Konditionen & Setup
- Lieferantenbewertung & Lieferkette absichern

**Section — SORTIMENT ERWEITERN OHNE EIGENKAPITAL**
- Die Methode erklärt — was sie bedeutet & für wen
- Welche Produkte sich eignen & wie man sie findet
- Lieferanten-Finanzierung & Zahlungsziel-Strategien
- Factoring, Kontokorrent & Amazon Lending einsetzen
- Praxisbeispiel: von 1 auf 5 Produkte ohne Bankkredit

**Exklusiver Vorteil:**
- 12.000 qm Fulfillment-Lager Hamburg — VIP-Konditionen
- Direktzugang zu Cashflow-Optimierungs-Experten
- Datax: Jahresabschluss & Steueroptimierung bei Skalierung

**Ergebnis:** Stabile Lieferketten, bessere Margen — und Sortimentswachstum ohne Eigenkapitalbedarf.

---

### ═══════════════════════════════════════
### COMMERCE GROWTH — LEVEL + (SPECIAL)
### ═══════════════════════════════════════

**Eyebrow:** COMMERCE GROWTH · EXKLUSIV
**Title:** China-Reise, Fabrikbesuche & Exklusive Herstellerkontakte
**Objective:** Direkte Beziehungen zu Produzenten aufbauen und langfristige Wettbewerbsvorteile sichern.

**Special Badge:** Display a gold shimmer banner at top of this modal:
```
✈️  HIGHLIGHT — EXKLUSIVES ERLEBNIS  ✈️
```

**Section — INHALTE**
- Vorbereitung auf Fabrikmessen (Pari Jazz, 3 Videos)
- Begleitete China-Reise mit Fabrikbesuchen
- Direkte Fabrikbesuche & Produktionsbesichtigungen
- Verhandlungen mit Herstellern — Pari als Begleitung
- Exklusive Produktionsrechte entwickeln
- Sonderanfertigungen vom Konzept zum Prototyp
- Qualitätskontrollen vor Ort

**Extras Box:**
- Messe-Leitfaden
- Lieferanten-Bewertungsprotokolle
- Verhandlungsbegleitung durch Experten vor Ort

**Ergebnis:** Direkter Zugang zu Herstellern, bessere Einkaufskonditionen und langfristige Wettbewerbsvorteile durch exklusive Produktionsrechte.

---

## JAVASCRIPT IMPLEMENTATION

```javascript
// Data structure for all level popups
const levelData = {
  'launch-1': { eyebrow: 'COMMERCE LAUNCH · LEVEL 1', title: '...', ... },
  'launch-2': { eyebrow: 'COMMERCE LAUNCH · LEVEL 2', title: '...', ... },
  'launch-3': { eyebrow: 'COMMERCE LAUNCH · LEVEL 3', title: '...', ... },
  'launch-4': { eyebrow: 'COMMERCE LAUNCH · LEVEL 4', title: '...', ... },
  'growth-1': { eyebrow: 'COMMERCE GROWTH · LEVEL 1', title: '...', ... },
  'growth-2': { eyebrow: 'COMMERCE GROWTH · LEVEL 2', title: '...', ... },
  'growth-3': { eyebrow: 'COMMERCE GROWTH · LEVEL 3', title: '...', ... },
  'growth-4': { eyebrow: 'COMMERCE GROWTH · LEVEL 4', title: '...', ... },
  'growth-plus': { eyebrow: 'COMMERCE GROWTH · EXKLUSIV', title: '...', ... },
};

// Open modal
function openLevelModal(levelKey) {
  const data = levelData[levelKey];
  populateModal(data);
  document.querySelector('.modal-overlay').classList.add('active');
  document.body.style.overflow = 'hidden'; // prevent bg scroll
}

// Close modal
function closeLevelModal() {
  document.querySelector('.modal-overlay').classList.remove('active');
  document.body.style.overflow = '';
}

// Close on overlay click
document.querySelector('.modal-overlay').addEventListener('click', (e) => {
  if (e.target === e.currentTarget) closeLevelModal();
});

// Close on Escape key
document.addEventListener('keydown', (e) => {
  if (e.key === 'Escape') closeLevelModal();
});
```

---

## ACCESSIBILITY

```
- modal role="dialog"
- aria-modal="true"
- aria-labelledby pointing to modal title
- Focus trap inside modal when open
- Focus returns to trigger button on close
- Level buttons: aria-haspopup="dialog"
- aria-expanded on level buttons
- Escape key closes modal
- Close button: aria-label="Modal schließen"
```

---

## MOBILE BEHAVIOR

```
On screens < 768px:
- Modal takes full screen (100vw, 100vh)
- border-radius: 24px 24px 0 0 (bottom sheet style)
- Slides up from bottom instead of scaling from center
- Close button stays top-right
- Scrollable content inside
- Swipe down gesture to close (touch events)
```
