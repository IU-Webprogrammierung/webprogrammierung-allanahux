# Portfolio „Photography & UX Design“ – Allanah Diederichsen

Dieses Projekt ist im Modul Web-Programmierung (DLBUXPWP01) an der IU Internationale Hochschule entstanden. Es handelt sich um einen persönlichen Webauftritt meiner Fotografie- und UX-Projekte. Ziel war die Entwicklung einer ästhetisch reduzierten, barrierearmen Website, die vollständig ohne JavaScript auskommt und ausschließlich mit HTML und CSS umgesetzt wurde.

## Projektüberblick

- One-Page-Portfolio
- Schwerpunkte:
  - ruhige, klare Gestaltung, die meinen persönlichen Stil transportiert
  - hohe Barrierefreiheit nur mit HTML & CSS
  - Responsivität von 360px - 1920px
- Entwicklungs- und Testumgebung:
  - Google Chrome
  - getestet auf MacBook Pro 2020

**Navigationsstruktur**

Header
├─ About
├─ Photography Portfolio
├─ UX Projects
├─ Inspirations
├─ Say Hi (Contact)
└─ Footer (Legal (404-Website), Social Media, Copyright)

---

## Errungenschaften

**HTML-Struktur**

- Semantische Elemente: header, nav, section, article, footer, figure, figcaption
- picture-Element für responsive Bilder (ally.webp)
- Navigation über Sprungmarken (#about, #photo, #ux, #inspo, #sayhi)

**Entscheidung gegen ein CSS-Framework**

- Grund: individuelles, reduziertes Design mit eigener Ästhetik entwickelt
- Frameworks würden Gestaltung, Farben und Layoutlogik einschränken

**Layout**

- Kombination aus CSS Grid und Flexbox; z.B.:
  - Photography-Galerie: `grid-template-columns: repeat(auto-fit, minmax(150px, 1fr))`
  - UX-Tabs: Flexbox für horizontale Anordnung & Wrap-Verhalten
  - Inspirationsgalerie: komplexe Grid-Positionierung mit `nth-of-type`
- Media Queries für mehrere Breakpoints:
  - Mobile-First
  - `min-width: 640px` – Tablet hochkant
  - `min-width: 1024px` – Tablet/kleiner Desktop
  - `min-width: 1200px` – Desktop
  - `min-width: 1600px` – Large Desktop / TV
- Nutzung von clamp() für responsive Abstände:
  - z. B.: `padding-inline: clamp(1.5rem, 5vw, 4rem)`
- Nutzung von clamp() für Schriftgrößen:
  - z. B.: `font-size: clamp(3.5rem, 9vw, 7rem)` für das „&“-Zeichen

**CSS-Techniken**

- CSS Variablen (Custom Properties)
  - Abstände: `--space-x`, `--space-y`
  - Schriftgrößen: `--size-sm`, `--size-md`, `--size-lg`
  - Farben: `--color-bg`, `--color-text`, `--color-accent`, `--color-marker`
  - Maximalbreiten: `--maxw-md`, `--maxw-lg`
- CSS Nesting für bessere Lesbarkeit (z. B. header & h1)
- Website-Hintergrund:
  - Papiertextur: `background-image: linear-gradient(...), url(paper3.webp)`
  - Blur-Effekte: `backdrop-filter: blur(12px)`
- CSS Tabs (ohne JS):
  - Über Radio-Buttons realisiert (`input[type=radio]`)
  - Umschalten der Sichtbarkeit mit :has() bei Photography Portfolio Tabs:
    - `:has(#tab1:checked) .tab-images #panel1 { display: grid }`
  - UX-Projects Tabs nutzen Geschwister-Selektoren:
    - `#uxtab1:checked ~ .tab-images #uxpanel1 { display: grid }`
- Fehlerfeedback im Formular:
  - Nutzung von :invalid, :valid, :placeholder-shown
  - z. B.: `input:not(:placeholder-shown):invalid { border: 2px solid red }`
- Nutzung von max(), min(), clamp() zur Layoutstabilität

**Responsive Design**

- Schriftgrößen über CSS-Variablen je Breakpoint angepasst:
  - Desktop: `--size-md: 1.25rem`
  - Large Desktop: `--size-md: 1.3rem`
- Layoutwechsel:
  - Header wechselt von 1-Spalten-Grid (Mobile/Tablet) zu 2-Spalten-Grid (Desktop)
  - Inspirationsgalerie nutzt auf kleinen Geräten ein flexibles Auto-Fit-Grid und erhält auf Tablet/Desktop eine komplexere Grid-Struktur mit nth-of-type-Positionierungen
  - UX-Projekte wechseln von 1-Spalten (Mobile) zu 2-Spalten Grid (Tablet/Desktop)
- Scroll-Snap für klare Scrollbereiche:
  - `scroll-snap-type: y proximity`
- overflow-x Schutz gegen horizontales Scrollen:
  - `html, body { overflow-x: hidden; }`

**Zusätzliche Seiten**

- Eigene 404-Seite (404.html), die über den Footer-Link „Legal“ erreichbar ist

---

## Barrierefreiheit (Accessibility)

**Semantik und Landmark-Rollen**

- aria-label zur eindeutigen Benennung der Navigationen für Screenreader
- aria-labelledby zur logischen Zuordnung von Sections zu ihren Überschriften
- role="note" für ergänzende, beschreibende Texte

**ARIA in interaktiven Komponenten**

- UX-Projects-Tabs nutzen vollständiges Rollenmodell (role="tablist", "tab", "tabpanel")
- aria-controls und aria-labelledby zur logischen Verknüpfung von Tabs und Panels
- tabindex="0" stellt Tastaturzugänglichkeit sicher

**Buttons und Icons**

- Back-to-top Button mit aria-label zur Funktionsbeschreibung
- Social Icons (Instagram/LinkedIn) mit eindeutigen aria-labels
- Formularbutton nutzt aria-live="polite" für den Zustandswechsel („Send“ → „Done“)

**Formular**

- Pflichtfelder über required und aria-required
- Eingaberegeln über minlength, maxlength und type="email"
- Fehlertexte werden erst nach Interaktion sichtbar
- CSS-Validierungsfarben über :invalid, :valid
- Absende-Logik über Checkbox (ohne JavaScript)

**Tastaturbedienung**

- Focus-Stile über :focus-visible
- Interaktive Elemente (Tabs, Buttons, Links) vollständig per Tastatur erreichbar
- Wichtige Interaktionen wie Buttons, Back-to-top und Footer-Links halten die empfohlene Mindest-Zielgröße von ca. 44px ein

**Lighthouse Audit**

- Mobile: ≥89 Performance (schwankt leicht), 100 Accessibility, 100 Best Practices, 100 SEO
- Desktop: 100 Performance, 100 Accessibility, 100 Best Practices, 100 SEO

**Performanceoptimierungen**

- WebP-Bilder (< 100 KB)
- Lazy Loading für alle Inhalte außer Hero-Bild
- definierte width/height: verhindert Layout Shift
- fetchpriority="high" für das Hero-Bild
- Preload der WOFF2-Fonts im Head
- SVG-Favicon als Data-URL
- Reduzierung intensiver Box-Shadows zur Verbesserung der Renderingzeit

---

## Dark Mode

- Aktiviert über prefers-color-scheme: dark
- Variablen wechseln automatisch:
  - z. B.: `--color-bg: #111315`, `--color-text: #ffffffee`
- Anpassung von:
  - Navigation und Markerfarben
  - Formularhintergrund
  - Icons (invertiert über filter)
  - Bilder (leicht mit brightness/contrast gefiltert)
- Kein eigenes Toggle nötig

---

## Git-Workflow

- Projektstruktur über Phasen-Branches:
  - `Projekt-Phase-1-Konzeptionsphase`
  - `Projekt-Phase-2-Erarbeitungsphase`
  - `Projekt-Phase-3-Finalisierungsphase`
  - Zusammenführung aller Phasen in den `main-Branch`
- einheitliche, englische Commit-Messages nach dem Muster  
   „Bereich: kurze Beschreibung“ z. B. `Say Hi: Optimized form with form validation` oder `404 Page: Added an error page, linked to the Legal page`

---

## Herausforderungen im Projekt

**Header**

- Komplexe Positionierung von Bild, Titel und Navigation über mehrere Breakpoints
- h1 musste je Breakpoint neu gesetzt werden (z. B. `top: 8vh`, `left: 20vw`, `top: 18vh`, `left: 54vw`)
- Herausforderung: h1 verschiebt sich je Breakpoint und läuft teilweise in Bildbereiche hinein: Buchstaben verlieren den nötigen Kontrast und sind schlecht lesbar
- Layout: Header rutscht auf manchen Bildschirmgrößen zu weit nach rechts
- clamp() genutzt, um Bildhöhen dynamisch zu halten, dennoch unterschiedlich wirkende Proportionen je Gerät
- Perfekte Ausrichtung auf allen Geräten gleichzeitig schwer zu erzielen

**Responsives Verhalten**

- Probleme bei Bildschirmen die vertikal sehr hoch sind (z. B. Tablet hochkant):
  - Kontaktformular und Footer wurden teilweise abgeschnitten
  - Scroll-Snap rastet früher ein, bevor der letzte Bereich komplett im Viewport ist
- Anpassungen:

  - scroll-snap für Kontaktformular und Footer deaktiviert (`scroll-snap-align: none`)
  - zusätzlicher Abstand unter dem Footer nötig, um abgeschnittene Inhalte zu vermeiden (führt bei manchen Breakpoints zu größerem als gewünschtem Leerraum)

**About Me / Seitenübergang**

- Schwierigkeit: Abstand zwischen Header und About me je Breakpoint unterschiedlich groß
- Besonders auf Tablet-Hochkant entsteht ein zu großer vertikaler Abstand
- Herausforderung: denselben „Seitenübergang“ auf allen Bildschirmgrößen herzustellen

**Inspirations-Galerie**

- Asymmetrisches, magazinartiges Layout nur über CSS Grid
- Unterschiedliche Positionen der Bilder je Breakpoint über viele nth-of-type-Regeln
- Hoher Aufwand, Layout-Stabilität bei allen Bildschirmgrößen zu halten

**Kontaktformular**

- Umsetzung des „Send → Done“-Zustands ausschließlich mit CSS (Checkbox-Technik)
- Herausforderung: „Done“ sollte nur erscheinen, wenn alle Felder gültig sind
- Schwierigkeit: Validitätsprüfung rein über CSS, ohne JS-Logik
- Lösung: Kombination aus :valid / :invalid / :placeholder-shown + deaktivierter Checkbox, solange das Formular nicht gültig ist

**Performance**

- Komplette Optimierung der Bilder als WebP, Ziel < 100 KB
- Bildqualität (alle geschossen mit einer spiegellosen Kamera) leidet durch die Komprimierung
- Herausforderung: trotz vieler großflächiger Bilder eine Lighthouse-Performance <90% zu erreichen

---

## Learnings

- Umsetzung interaktiver UI-Komponenten ohne JavaScript
- Vertieftes Verständnis für die Komplexität und Wichtigkeit von Barrierefreiheit im Web
- Erfahrungen mit Multi-Breakpoint-Layouts (360px–1920px) und deren unterschiedlichen Anforderungen
- Optimierung großer Bildateien für bessere Performance (WebP, Lazy Loading, Preload)
- Git-Workflow in Projektphasen mit klar strukturierten Commits

---

## Fazit

- Modul fachlich wie persönlich bereichernd
- Sehr zufrieden mit finalem Ergebnis und dem erarbeiteten Wissen
- Die verpflichtende Barrierefreiheit anfangs herausfordernd, jedoch wertvolle Erkenntnisse gewonnen
- Modul war besonders hilfreich, da Portfolio für den realen Einsatz einsatzbereit
- Einbringung des persönlichen Designstils und gleichzeitig praktische Sicherheit im Umgang mit modernen Webtechniken gewonnen
