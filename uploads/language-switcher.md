# Language Switcher Component — Pari Jazz Commerce

## COMPONENT: Header Language Switcher (Flag Dropdown)

Add a language switcher to the global header, positioned between the navigation links and the CTA button.

---

## VISUAL DESIGN

```
Default state (closed):
┌─────────────────┐
│ 🇩🇪  DE    ▾   │
└─────────────────┘

Hover/open state (dropdown expands below):
┌─────────────────┐
│ 🇩🇪  DE    ▾   │
└─────────────────┘
        │
┌───────────────────┐
│ 🇩🇪  Deutsch    ● │  ← active (bold + gold dot)
│ 🇺🇸  English      │
│ 🇨🇳  中文          │
│ 🇫🇷  Français      │
│ 🇪🇸  Español       │
│ 🇵🇹  Português     │
└───────────────────┘
```

---

## TRIGGER BUTTON STYLES

```css
/* Closed pill button */
background:     transparent
border:         1.5px solid #C9A96E  (gold)
border-radius:  999px
padding:        10px 18px
font-family:    Inter
font-size:      14px
font-weight:    600
color:          #1A1A1A  (dark text on cream bg)
                #FFFFFF  (white text when over dark/hero sections)
display:        flex
align-items:    center
gap:            8px
cursor:         pointer

/* Flag emoji size */
font-size:      18px

/* Language code */
font-size:      14px
font-weight:    600
letter-spacing: 0.5px
text-transform: uppercase

/* Dropdown arrow ▾ */
font-size:      12px
color:          #C9A96E  (gold)
transition:     transform 200ms ease
/* Rotates to ▴ when open */
transform:      rotate(180deg) when open
```

---

## DROPDOWN PANEL STYLES

```css
/* Dropdown card */
position:         absolute
top:              calc(100% + 8px)
right:            0
background:       #FFFFFF
border:           1px solid #EAD7A1  (gold light)
border-radius:    16px
padding:          8px
min-width:        180px
box-shadow:       0 8px 32px rgba(25, 70, 189, 0.12)
z-index:          1000

/* Open animation */
animation:        fadeSlideDown 200ms ease forwards

@keyframes fadeSlideDown {
  from {
    opacity: 0;
    transform: translateY(-8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Each language option row */
padding:          10px 14px
border-radius:    10px
display:          flex
align-items:      center
gap:              10px
cursor:           pointer
transition:       background 150ms ease

/* Hover state */
background:       #F7F4EE  (cream)

/* Active/selected language */
font-weight:      700
color:            #1946BD  (royal blue)

/* Active gold dot indicator */
width:            6px
height:           6px
border-radius:    50%
background:       #C9A96E
margin-left:      auto
```

---

## LANGUAGE OPTIONS (in order)

| Flag | Code | Full Name | Default |
|------|------|-----------|---------|
| 🇩🇪 | DE | Deutsch | ✅ YES |
| 🇺🇸 | EN | English | |
| 🇨🇳 | CN | 中文 | |
| 🇫🇷 | FR | Français | |
| 🇪🇸 | ES | Español | |
| 🇵🇹 | PT | Português | |

---

## HEADER PLACEMENT

```
HEADER LAYOUT (left → right):
┌────────────────────────────────────────────────────────────────────┐
│  [LOGO]    [Nav: E-Commerce · Sourcing · Network · Contact]   [🇩🇪 DE ▾]   [Erstgespräch vereinbaren →]  │
└────────────────────────────────────────────────────────────────────┘

Spacing between language switcher and CTA button: 16px
Spacing between nav and language switcher: 32px
```

---

## HEADER BEHAVIOR STATES

### State 1 — Over Hero (transparent header)
```
Logo:               white version or gold phoenix only
Nav links:          white, hover: gold underline
Language button:    border: 1.5px solid rgba(255,255,255,0.5)
                    text: white
                    flag: visible
                    arrow ▾: white/gold
CTA button:         royal blue pill (stays same)
```

### State 2 — Scrolled (solid cream header)
```
Background:         #F7F4EE with subtle bottom border: 1px solid #EAD7A1
Logo:               full color phoenix logo
Nav links:          #1A1A1A, hover: royal blue
Language button:    border: 1.5px solid #C9A96E
                    text: #1A1A1A
                    arrow ▾: #C9A96E gold
CTA button:         royal blue pill (same)
```

### State 3 — Mobile (hamburger menu)
```
Language switcher:  moves INSIDE the mobile menu drawer
                    displayed as full-width row of flag buttons
                    ┌──────────────────────────────────┐
                    │ 🇩🇪  🇺🇸  🇨🇳  🇫🇷  🇪🇸  🇵🇹        │
                    └──────────────────────────────────┘
                    Active flag: gold border ring around it
```

---

## JAVASCRIPT BEHAVIOR

```javascript
// On language select:
1. Update trigger button to show selected flag + code
2. Close dropdown with fade-out animation
3. Add smooth content transition:
   - Fade page content to 80% opacity (150ms)
   - Swap all text content to selected language
   - Fade back to 100% opacity (150ms)
4. Store selection in localStorage('pj-language')
5. On page load: read localStorage and apply saved language

// Accessibility:
- role="combobox" on trigger button
- role="listbox" on dropdown
- role="option" on each language item
- aria-expanded on trigger
- aria-selected on active language
- Keyboard: Enter/Space opens, Arrow keys navigate, Escape closes
```

---

## CONTENT TRANSLATION NOTES

When EN is selected, key UI strings change:
```
DE: "Erstgespräch vereinbaren"  →  EN: "Schedule Consultation"
DE: "Programme"                  →  EN: "Programs"
DE: "Netzwerk & Partner"        →  EN: "Network & Partners"
DE: "Kontakt"                    →  EN: "Contact"
DE: "Sourcing"                   →  EN: "Sourcing" (same)
```

When 🇨🇳 CN selected:
```
EN: "Schedule Consultation"  →  CN: "预约咨询"
EN: "Programs"               →  CN: "项目"
EN: "Network & Partners"     →  CN: "网络与合作伙伴"
EN: "Contact"                →  CN: "联系我们"
```

---

## INTEGRATION NOTE

This component is part of the **sticky global header** that appears on ALL pages of the Pari Jazz Commerce website. The header is always visible (position: sticky, top: 0, z-index: 999) and the language selection persists across all page navigations.
