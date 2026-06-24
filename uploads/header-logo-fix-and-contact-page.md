# Pari Jazz Commerce — Header Logo Fix + Contact Page

---

## PART 1: HEADER LOGO FIX

### What the current header looks like
From the screenshot, the header currently shows:
- Logo (PARI JAZZ phoenix) — too small, has a visible **white box/background** around it that needs to be removed
- A gold vertical divider line, then "COMMERCE" text in gold next to the logo
- Center nav: The System · Network · About Pari · Phases · Programs
- Right side: Language toggle (flag + EN + dropdown arrow, gold outline pill) + "Schedule Consultation" blue pill button

### Fix Instructions — Logo Only
- The logo file (`Black_and_Gold_Classy_and_Elegant_Phoenix_Company_Logo.png`) has a white background baked in
- Fix it by wrapping the `<img>` tag with `mix-blend-mode: multiply` so the white disappears on the cream header background
- CSS to apply to the logo `<img>` element:
  ```css
  .header-logo img {
    mix-blend-mode: multiply;
    height: 56px;        /* increase from current ~36px */
    width: auto;
    object-fit: contain;
  }
  ```
- On dark/navy sections where the header is transparent over the hero, switch to:
  ```css
  .header-logo img {
    mix-blend-mode: normal;
    filter: brightness(0) invert(1); /* makes logo white on dark bg */
  }
  ```
- **Do not change anything else in the header** — the nav links, language toggle, and Schedule Consultation button are already correct

### Header Layout Reference (keep exactly as is, only fix the logo)
```
[ PARI JAZZ LOGO 56px — transparent bg ]  |  COMMERCE    The System · Network · About Pari · Phases · Programs    [ 🇺🇸 EN ▾ ]  [ Schedule Consultation ]
```

---

## PART 2: CONTACT PAGE — Full Spec

### Page Path: `/contact`

This page exists on the live site but was not captured in the scraped project files. Build it following the brand system exactly.

---

### SECTION 1: HERO BANNER (slim, not full viewport)
- Background: Deep Navy `#0A1628`
- Centered content:
  - Small gold eyebrow caption (uppercase, tracked): "GET IN TOUCH"
  - H1 Playfair Display white: "Let's talk about your vision."
  - Subhead Inter `#94A3B8` (20px): "Not sure where to start? We'll help you find the right path."
- Height: `320px` desktop, `240px` mobile

---

### SECTION 2: CONTACT SPLIT LAYOUT (cream `#F7F4EE` background)

Two-column layout, 50/50 split on desktop, stacked on mobile.

#### LEFT COLUMN — Photo + Intro Text
- Image: Pari Jazz portrait (woman with curly hair, laptop, high-rise window background)
- Image style: full column width, `border-radius: 12px`, soft shadow
- Below image:
  - H3 Playfair `#1A1A1A`: "Get in touch with us"
  - Body Inter `#475569` (16px, line-height 1.7):
    > "Do you have a specific vision or request that goes beyond our services? You've come to the right place. Use this form for your individual inquiries. We'll carefully review your details and get back to you promptly."

#### RIGHT COLUMN — Contact Form
- Form title H2 Playfair `#0A1628`: "Contact request"
- All fields: `border-radius: 8px`, border `1px solid #E2E8F0`, focus state border `#1946BD`

**Fields in order:**
1. Salutation radio buttons (inline): `○ Mister` &nbsp; `○ Woman.` — selected state fills Royal Blue `#1946BD`
2. First name (half width) + Last name (half width) — side by side
3. Company name (full width) — placeholder: "Enter your official company name"
4. E-mail (full width) — placeholder: "example@gmx.de"
5. Describe your request (textarea, full width, min-height 120px) — placeholder: "Briefly describe the topic of your request."

**Submit button** (full width):
- Background: Royal Blue `#1946BD`
- Text: "Submit a request" — white, Inter, uppercase, letter-spacing 0.5px
- `border-radius: 8px`
- Hover: `#1438A0`, scale `1.01`
- **On submit, form data sends to: `info@parijazz.de`** (general contact inquiries)

**Terms checkbox** below button:
- `☐ By submitting this form, I agree` **`to the terms of use.`** `*`
- "to the terms of use." = gold underlined link `#C9A96E`
- Field gap: `24px` between all fields

---

### SECTION 3: ALTERNATIVE CONTACT OPTIONS (cream bg, centered)
- Gold eyebrow: "OTHER WAYS TO REACH US"
- 3-card row, white cards, `border-radius: 12px`, soft shadow:

  | Icon | Label | Clickable Detail |
  |------|-------|-----------------|
  | 📧 | General Inquiries | `info@parijazz.de` — clicking opens mail client |
  | 📦 | Sourcing Requests | `sourcing@parijazz.de` — clicking opens mail client |
  | 📍 | Location | Hamburg, Germany |

- Both email addresses must be real `mailto:` links:
  - `<a href="mailto:info@parijazz.de">info@parijazz.de</a>`
  - `<a href="mailto:sourcing@parijazz.de">sourcing@parijazz.de</a>`
- Icon color: Gold `#C9A96E`
- Label text: Inter, `#475569`
- Email links: Royal Blue `#1946BD`, underline on hover

---

### SECTION 4: FOOTER
- Same global footer as all other pages (deep navy background, 4-column links, social icons, newsletter signup)

---

## BRAND REMINDER
- Royal Blue `#1946BD` | Gold `#C9A96E` | Cream `#F7F4EE` | Navy `#0A1628`
- Headings: Playfair Display | Body: Inter
- Primary CTA buttons: `border-radius: 999px` (pill) | Form submit: `border-radius: 8px`
