---
title: 'Stuckateurbetrieb Kreutzer GmbH'
description: 'Corporate Webseite für den Stuckateurbetrieb Kreutzer GmbH, entwickelt mit dem Astro Webframework'
heroImage: '/stuckateur-kreutzer.png'
---

🌐 Webseite: [https://stuckateur-kreutzer.netlify.app/](https://stuckateur-kreutzer.netlify.app/) <br />
📁 GitHub: [Source-Code](https://github.com/kreutzermaik/stuckateur-kreutzer)
## 💻 Tech Stack
- Die Basis bildet das Web-Framework [Astro](https://astro.build/)
- Die Komponenten werden entsprechend mit JavaScript und HTML umgesetzt
- Die Styles werden in CSS geschrieben

<br />

## 🗂️ Übersicht über die Komponenten
- Die Komponenten befinden sich im Ordner `./src/components/`
- Diese werden in der Datei `./src/pages/index.astro` eingebunden
- Als Wrapper für die Hauptseite dient das Layout `./src/layouts/Layout.astro`
- Verwendete Icons werden als SVG-Tags im Ordner `./src/icons/` abgelegt
- Der Ordner `utils` enthält die Datei `CustomStyles.astro`, welches als Template-Klasse für Tailwind dient sowie die Datei `BasicScripts.astro`, die die Navbar stylisch anpasst, sobald im Browser gescrollt wird

<br />

## ⌘ Commands

| Command                   | Action                                             |
| :------------------------ |:---------------------------------------------------|
| `npm install`             | Abhängigkeiten installieren                        |
| `npm run dev`             | Startet lokalen Server `localhost:3000`            |
| `npm run build`           | Bauprozess für die Produktion zum Ordner `./dist/` |
| `npm run preview`         | Vorschau der gebauten App vor Deploy               |

<br />

## 🚀 Deployment
- Die Webseite wird mit dem Tool [Netlify](https://www.netlify.com/) deployed
- Das GitHub-Repository der Webseite ist mit einem Netlify-Konto verknüpft
- Wird ein neuer Commit auf den `master`-Branch gepusht, wird die Webseite automatisch neu gebaut und deployed

<br />

## 📈 Performance Score
Mit dem Tool Lighthouse von Google wurde die Performance der Webseite gemessen: 
<img src="/lighthouse-score.png" style="margin-top: 20px;">

<br />

## 📝 Lizenz
[MIT](https://choosealicense.com/licenses/mit/)
