# LaTeX-Vorlage für Bachelorarbeiten an der IU Internationalen Hochschule

Dieses Repository enthält eine moderne, bereinigte \LaTeX-Vorlage für wissenschaftliche Arbeiten – speziell optimiert für **Bachelorarbeiten** (sowie Seminararbeiten und Masterarbeiten) an der [IU Internationalen Hochschule](https://www.iu.de/).

Die Vorlage setzt die offiziellen Vorgaben der **IU-Richtlinien zur Gestaltung wissenschaftlicher Arbeiten (Stand: 01.10.2025)** präzise um.

---

## Einhaltung der IU-Richtlinien (Stand: 01.10.2025)

| Vorgabe | IU-Richtlinie | Umsetzung im Template |
| :--- | :--- | :--- |
| **Schriftart** | Arial (oder serifenlos wie Calibri), einheitlich schwarz | `fontspec` mit `Arial` (Fallback: Liberation Sans / TeX Gyre Heros) |
| **Schriftgröße** | 11 Pt. im Fließtext, 10 Pt. in Fußnoten | `\documentclass[11pt]{article}`, `\footnotesize` auf 10 Pt. gesetzt |
| **Zeilenabstand** | 1,5-zeilig im Fließtext, einzeilig in Fußnoten | `\setstretch{1.5}` via `setspace` |
| **Seitenränder** | Exakt 2,00 cm für alle Ränder | `geometry` mit 2,0 cm oben, unten, links, rechts |
| **Absatzabstand** | Kein Erstzeileneinzug, 6 Pt. Abstand nach Absatz | `\usepackage[skip=6pt]{parskip}` |
| **Überschriften** | 1. Stufe: 16 Pt. (12 Pt. vor / 12 Pt. nach)<br>2. Stufe: 14 Pt. (12 Pt. vor / 6 Pt. nach)<br>3. Stufe: 11 Pt. (12 Pt. vor / 6 Pt. nach) | Exakt über `titlesec` konfiguriert |
| **Inhaltsverzeichnis** | Nur 1. Ebene fett, Verzeichnisse linksbündig | Durchgehende Punktlinien, Unterebenen normal |
| **Seitennummerierung** | Römisch vor Textteil (Titelblatt = I, nicht gedruckt, Start bei II), arabisch ab Einleitung (1) durchgehend zentriert am Seitenende | `fancyhdr` mit `\cfoot{\thepage}`, `\setcounter{page}{2}` im Vorspann |
| **Zitierstil** | APA 7th Edition, 1,27 cm hängender Einzug | `biblatex-apa` mit Biber-Backend |
| **Bestandteile BA** | Titelblatt, Danksagung, Gender-Disclaimer, Abstract, TOC, Abb.-/Tab.-Verzeichnis, Abk.-Verzeichnis, Text, Literatur, Anhangsverzeichnis, Anhänge, Ehrenwörtliche Erklärung | Vollständig strukturiert und vorkonfiguriert |

---

## Voraussetzungen

- **LuaLaTeX**: Für native UTF-8-Unterstützung und `fontspec` zur Einbindung von OpenType-Schriftarten (Arial).
- **Biber**: Für die APA-7-Bibliografieverarbeitung (`biblatex-apa`).

> **Tipp für Overleaf-Nutzer**: In den Menüeinstellungen links oben den Compiler von *pdfLaTeX* auf **LuaLaTeX** umstellen.

---

## Kompilierung

```bash
# 1. Erster Durchlauf
lualatex main

# 2. Bibliographie verarbeiten
biber main

# 3. Zwei Durchläufe für Verzeichnisse und Querverweise
lualatex main
lualatex main
```

---

## Projektstruktur

```text
├── main.tex                 % Hauptdokument (Layout, Pakete, Dokumentstruktur)
├── references.bib           % BibLaTeX-Literaturdatenbank (APA 7)
├── chapters/                % Inhaltliche Kapitel
│   ├── introduction.tex     % Kapitel 1: Einleitung (Beginn arabische Zählung)
│   ├── mainpart.tex         % Kapitel 2: Hauptteil (Zitate, Abbildungen, Tabellen, Code)
│   └── conclusion.tex       % Kapitel 3: Fazit und Ausblick
├── pages/                   % Formale Seiten & Verzeichnisse
│   ├── cover.tex            % Titelseite (IU-konform für Bachelorarbeit)
│   ├── acknowledgements.tex % Danksagung (freiwillig)
│   ├── gender_disclaimer.tex% Gender-Disclaimer (optional, offizieller IU-Wortlaut)
│   ├── appendix.tex         % Anhangsverzeichnis & Anhänge (Anhang A, B, etc.)
│   └── declaration.tex      % Ehrenwörtliche Erklärung (Pflicht bei Abschlussarbeiten)
└── logos/                   % IU-Logos
```

---

## Anpassung für Deine Bachelorarbeit

1. **Titelseite ([pages/cover.tex](pages/cover.tex))**: Titel, Studiengang, Name, Matrikelnummer, Erst- und Zweitprüfer/in sowie Abgabedatum eintragen.
2. **Abstract ([main.tex](main.tex))**: Kurzfassung der Bachelorarbeit im Abstract-Block einfügen.
3. **Optionale Seiten**: Danksagung und Gender-Disclaimer können in `main.tex` bei Bedarf einkommentiert werden.
4. **Abbildungs- und Tabellenverzeichnis**: Laut IU-Richtlinien erst ab jeweils 3 Abbildungen bzw. 3 Tabellen verpflichtend. Falls weniger vorhanden sind, können `\listoffigures` bzw. `\listoftables` in `main.tex` einfach auskommentiert werden.
5. **Literatur ([references.bib](references.bib))**: Quellen im BibLaTeX-Format pflegen und mit `\parencite{key}` oder `\textcite{key}` zitieren.
6. **Quellenangaben unter Bildern/Tabellen**: Nutzen Sie das vordefinierte Makro `\quelle{...}`, um die geforderte 10-Pt.-Schriftgröße einzuhalten.

---

## Lizenz

Diese Vorlage steht unter der [MIT License](LICENSE) zur freien Verfügung.

