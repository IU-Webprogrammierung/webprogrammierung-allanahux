**Portfolio „Photography & UX Design“ – Allanah Diederichsen**

## Projektüberblick

- One Page Portfolio
- Fokus auf:
  - ruhige Ästhetik
  - hohe Barrierefreiheit nur mit HTML & CSS
  - Responsivität von 360px - 1920px

---

**Technologien und Methoden**

## HTML-Struktur

- Semantische Elemente: header, nav, section, article, footer, figure, figcaption
- picture-Element für responsive Bilder (ally.webp)
- Interne Navigation über Sprungmarken (#about, #photo, #ux, #inspo, #sayhi)

## Layout

- Kombination aus CSS Grid und Flexbox

  - Beispiele:
  - Grid im Header: `grid-template-columns: minmax(460px, 52vw) 1fr`
  - Photography-Galerie: `grid-template-columns: repeat(auto-fit, minmax(150px, 1fr))`
  - Inspirationsgalerie: komplexe `nth-of-type`-Positionierung
  - Navigation: flexbox-basiertes Zentrieren

- Media Queries für mehrere Breakpoints:

  - Mobile-First
  - `min-width: 640px` – Tablet hochkant
  - `min-width: 1024px` – Tablet/kleiner Desktop
  - `min-width: 1200px` – Desktop
  - `min-width: 1600px` – Large Desktop / TV

- Nutzung von clamp() für responsive Abstände:
  - Beispiel: `padding-inline: clamp(1.5rem, 5vw, 4rem)`
- Nutzung von clamp() für Schriftgrößen:
  - Beispiel: `font-size: clamp(3.5rem, 9vw, 7rem)` für das „&“-Zeichen

## CSS-Techniken

- CSS Variablen (Custom Properties)
  - Beispielabstände: `--space-x`, `--space-y`
  - Schriftgrößen: `--size-sm`, `--size-md`, `--size-lg`
  - Farben: `--color-bg`, `--color-text`, `--color-accent`, `--color-marker`
  - Maximalbreiten: `--maxw-md`, `--maxw-lg`
- CSS Nesting für bessere Lesbarkeit (z. B. header & h1)
- Hintergrund:
  - Papiertextur: `background-image: linear-gradient(...), url(paper3.webp)`
  - Blur-Effekte: `backdrop-filter: blur(12px)`
- CSS-only Tabs:
  - Über radio-Buttons (`input[type=radio]`)
  - Umschalten der Sichtbarkeit mit :has() bei Photography:
    - `:has(#tab1:checked) .tab-images #panel1 { display: grid }`
  - UX-Tabs über Geschwister-Selektoren:
    - `#uxtab1:checked ~ .tab-images #uxpanel1 { display: grid }`
- Fehlerfeedback im Formular:
  - Nutzung von :invalid, :valid, :placeholder-shown
  - Beispiel: `input:not(:placeholder-shown):invalid { border: 2px solid red }`
- Nutzung von max(), min(), clamp() zur Layoutstabilität

## Responsive Design

- Schriftgrößen über Variablen angepasst:
  - Desktop: `--size-md: 1.25rem`
  - Large Desktop: `--size-md: 1.3rem`
- Layoutwechsel:
  - Header wechselt von 1-Spalten-Grid zu 2-Spalten-Grid
  - Inspirationsgalerie erhält komplett neue Struktur je Breakpoint
  - UX-Projekte wechseln von 1-Spalten zu 2-Spalten Grid
- Scroll-Snap für klare Scrollbereiche:
  - `scroll-snap-type: y proximity`
- overflow-x Schutz gegen horizontales Scrollen:
  - `html, body { overflow-x: hidden; }`

## Zusätzliche Seiten

- Eigene 404-Seite (404.html), die über den Footer-Link „Legal“ erreichbar ist

**Barrierefreiheit (Accessibility)**

## Semantik und Landmark-Rollen

- aria-label auf Navigationen
  - `nav aria-label="Main navigation"`
  - `nav aria-label="Footer Navigation"`
- role="contentinfo" auf Footer
- aria-labelledby für logische Zuordnung:
  - Beispiel: `section id="inspo" aria-labelledby="inspo-title"`
- role="note" für erklärende Texte in Inspiration

## ARIA in interaktiven Komponenten

- UX-Tabs
  - role="tablist", role="tab", role="tabpanel"
  - aria-controls und aria-labelledby
  - tabindex="0" für Tastaturzugänglichkeit
- Photography-Tabs
  - aria-label="Portfolio Kategorien"
  - aria-controls für Panels
  - aria-labelledby für Verbindung von Label + Panel
  - Steuerung ohne Rollen, jedoch über ARIA-Kopplung

## Buttons und Icons

- Back-to-top: aria-label="Nach oben scrollen"
- Social Icons: aria-label bei Instagram/LinkedIn
- Formularbutton: aria-live="polite" für Statuswechsel

## Formular

- required + aria-required
- minlength, maxlength, type="email"
- Fehlertexte werden erst nach Interaktion sichtbar
- CSS-Validierungsfarben über :invalid, :valid
- Absende-Logik über Checkbox (ohne JavaScript)

## Tastaturbedienung

- Focus-Stile über :focus-visible
- Alle Tabs, Buttons, Links erreichbar
- Ausreichende Zielgrößen (mind. 44px)

**Dark Mode**

- Aktiviert über prefers-color-scheme: dark
- Variablen wechseln automatisch:
  - Beispiel: `--color-bg: #111315`, `--color-text: #ffffffee`
- Anpassung von:
  - Navigation und Markerfarben
  - Formularhintergrund
  - Icons (invertiert über filter)
  - Bilder (leicht mit brightness/contrast gefiltert)
- Kein eigenes Toggle nötig

**Performanceoptimierungen**

- WebP-Bilder (< 100 KB)
- Lazy Loading für alle Inhalte außer Hero-Bild
- definierte width/height: verhindert Layout Shift
- fetchpriority="high" für das Hero-Bild
- Preload der WOFF2-Fonts im Head
- SVG-Favicon als Data-URL
- Reduzierung intensiver Box-Shadows zur Verbesserung der Renderingzeit

**Git-Workflow**

- Struktur über Phasen-Branches
- Klar strukturierte Commits mit Überschriften

---

**Herausforderungen im Projekt**

## Header

- Komplexe Positionierung von Bild, Titel und Navigation über mehrere Breakpoints
- h1 musste je Breakpoint neu gesetzt werden (z. B. `top: 8vh`, `left: 20vw`, `top: 18vh`, `left: 54vw`)
- Herausforderung: h1 verschiebt sich je Breakpoint und läuft teilweise in Bildbereiche hinein: Buchstaben verlieren den nötigen Kontrast und sind schlecht lesbar
- Layout-Drift: Header rutscht auf manchen Bildschirmgrößen zu weit nach rechts
- clamp() genutzt, um Bildhöhen dynamisch zu halten, dennoch unterschiedlich wirkende Proportionen je Gerät
- Perfekte Ausrichtung auf allen Geräten gleichzeitig schwer zu erzielen

## Responsives Verhalten

- Probleme bei Bildschirmen die vertikal sehr hoch sind (z.B. Tablet hochkant):
  - Kontaktformular und Footer wurden teilweise abgeschnitten
  - Scroll-Snap rastet früher ein, bevor der letzte Bereich komplett im Viewport ist
- Anpassungen:

  - scroll-snap für Kontaktformular und Footer deaktiviert (`scroll-snap-align: none`)
  - zusätzlicher Abstand unter dem Footer nötig, um abgeschnittene Inhalte zu vermeiden (führt bei manchen Breakpoints zu größerem als gewünschtem Leerraum)

  ## About Me / Seitenübergang

- Schwierigkeit: Abstand zwischen Header und About me je Breakpoint unterschiedlich groß
- Besonders auf Tablet-Hochkant entsteht ein zu großer vertikaler Abstand
- Herausforderung: denselben „Seitenübergang“ auf allen Bildschirmgrößen herzustellen

  ## Inspirations-Galerie

- Asymmetrisches, magazinartiges Layout nur über CSS Grid
- Unterschiedliche Positionen der Bilder je Breakpoint über viele nth-of-type-Regeln
- Hoher Aufwand, Layout-Stabilität bei allen Bildschirmgrößen zu halten

## Kontaktformular

- Umsetzung des „Send → Done“-Zustands ausschließlich mit CSS (Checkbox-Technik)
- Herausforderung: „Done“ sollte nur erscheinen, wenn alle Felder gültig sind
- Schwierigkeit: Validitätsprüfung rein über CSS, ohne JS-Logik
- Lösung: Kombination aus :valid / :invalid / :placeholder-shown + deaktivierter Checkbox, solange das Formular nicht gültig ist

## Performance

- Komplette Optimierung der Bilder als WebP, Ziel < 100 KB
- Bildqualität (alle geschossen mit einer spiegellosen Kamera) leidet durch die Komprimierung
- Herausforderung: trotz vieler großflächiger Bilder eine Lighthouse-Performance <90% zu erreichen

---

**Learnings**

- Git-Workflow in Projektphasen mit klar strukturierten Commits
- Umsetzung komplexer Interaktionen ohne JavaScript (z.B. interaktiver Komponenten (Tabs, Formularstatus))
- Größeres Verständnis für die Komplexität und Wichtigkeit von Barrierefreiheit im Web
- Erfahrungen mit Multi-Breakpoint-Layouts (360px–1920px) und deren unterschiedlichen Anforderungen
- Optimierung großer Bildmengen für bessere Performance (WebP, Lazy Loading, Preload)
