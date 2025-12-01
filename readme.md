Projekt: Portfolio Photography & UX Design – Allanah Diederichsen

Eingesetzte Technologien 
• HTML & CSS

Responsivität & Breakpoints
• 4 Breakpoints:
- Mobile (bis 639px)
– Tablet (640–1023px)
– Tablet / Desktop klein (1024–1199px)
– Desktop (1200–1599px)
– Large Desktop / TV (ab 1600px)

Barrierefreiheit
• Einsatz von ARIA-Rollen
• Verwendung von aria-controls, aria-labelledby, aria-label
• Fokus-Styles für Tastaturbedienbarkeit
• Tastaturnavigation vollständig möglich
• Alt-Texte für alle Bilder
• Große interaktive Flächen und ausreichende Kontraste
• Formularfelder mit aria-required und nativer Validierung

Interaktionsmöglichkeiten
• voll funktionsfähige Tabs nur mit CSS, basierend auf Radio-Buttons
• Einsatz von Pseudoklassen wie :checked, :focus-visible, :has()
• Dynamische Anzeige/Verbergung von Inhaltspanels über CSS-Selektoren
• Back-to-top Button
• Visueller „Send / Done“-Zustand über Checkbox-Mechanismus bei Buttons
• Interaktive Hover-Effekte und Marker-Animationen über CSS Transitions

Bilder & Performanceoptimierung
• Alle Bilder in WEBP für reduzierte Dateigrößen (<100 KB angestrebt)
• Asynchrones Decoding (decoding="async")
• Priorisierung des Hero-Bildes (fetchpriority="high")
• Nutzung von SVG-Icons statt PNG (Footer Icons: LinkedIn, Instagram)
• Optimierte Rendering-Pipeline durch Reduktion von Overlays/Filtern

Dark Mode (ohne JavaScript)
• Automatische Erkennung via @media (prefers-color-scheme: dark)
• Dynamische Anpassung aller Designkomponenten:
– Navigation
– Bilder
– Formulare
– Buttons
– Tabellen / Listen / Tabs
• Nutzung von Farbvariablen für Light/Dark Switching

• Kontrastoptimierung im Dark Mode

Formular & Validierung
• HTML5-Validierung (required, type="email", minlength, maxlength)
• Visuelles Feedback (gültig/ungültig) über CSS Selektoren:
– :invalid:not(:placeholder-shown)
– :valid:not(:placeholder-shown)
• Fehlernachrichten über CSS gesteuert
• Barrierefreie Labels (for, id)
• Individueller Buttonmechanismus ohne JavaScript (Checkbox + CSS)

Scroll-Mechaniken
• Smooth Scrolling (scroll-behavior: smooth)
• Scroll Snap Layout für definierte Abschnittspunkte (scroll-snap-type, scroll-snap-align)
• Bereichsspezifisches Snap-Verhalten für unterschiedliche Sektionen
• Back-to-top Button mit Fokusmarkierungen

Struktur & Codequalität
• Strikte Trennung von Struktur (HTML) und Styling (CSS)
• Konsistente Einrückung und Abschnittskommentare
• Übersichtliche CSS-Architektur durch logische Sektionen
• Reduktion redundanter Regeln durch Variablen und Komponentenstruktur
• Semantische Nutzung von Listen, Heading-Hierarchien, Tabellen (wo vorhanden)

Git-Workflow & Projektstruktur
• Regelmäßige Commits
• Phasen-Branches 
• Aufbau der Repository-Struktur nach Best Practices:
– assets/images 
– assets/vectors (SVG Icons)
– fonts
– style.css
– index.html + 404.html
• Klare Commit-Messages zur Rückverfolgung von Änderungen

Lernprozesse (Technisch)
• Verständnis, wie vollständig interaktive UI-Komponenten ohne JavaScript funktionieren
• Vertiefung in CSS Selektoren, Strukturselektoren und moderne Pseudoklassen
• Umgang mit komplexen responsiven Layouts und deren Fallstricken
• Bedeutung von Semantik und Barrierefreiheit in echten Projekten
• Performanceoptimierung durch bewusstes Medienmanagement
• Entwicklung eines konsistenten Designsystems mit CSS Variablen
• Erkennen der Grenzen und Möglichkeiten von CSS-only Interaktivität