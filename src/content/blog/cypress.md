---
title: 'Cypress'
description: 'Lorem ipsum dolor sit amet'
pubDate: 'Sep 01 2023'
heroImage: '/cypress.png'
---

## Einleitung

### Arten von Tests

- End-to-end Tests
- Component Tests
- Unit Tests
- Integration Tests
- Visual Regression Tests (?)

### Struktur

- Die Tests liegen im Ordner cypress/e2e

## Entwicklung eines Tests

- Um bestimmte Patterns zu erkennen, werden Regex-Ausdrücke benötgt
- Dazu gibt es die Klasse `RegexHelper`

## Konfiguration

- Die Konfiguration wird in der `cypress.config.ts` vorgenommen
- Dort kann z.B. die baseUrl angegeben werden
- Video und Screenshot Aufnahmen können ebenfalls deaktiviert werden

## Guidelines

- Naming: viewname-test.cy.ts
- Bei component-Tests: Datei in den Ordner legen

## Automatisierung

- Damit Cypress Tests automatisiert durchgeführt werden können, muss die package.json angepasst werden:

```json
"test": "npx cypress run --browser edge"

```

Mit dieser Konfiguration lassen sich die Tests mit `npm run test` ausführen und dabei wird der headless Edge-Browser verwendet.

## Proxy Einstellungen

- Quelle: https://angular.io/guide/build#proxying-to-a-backend-server
- Damit die Anwendung auch innerhalb von Cypress auf das Backend zugreifen kann, müssen die Proxy-Einstellungen angepasst werden
- Für **Angular** gilt folgende Anleitung:

Im root-Verzeichnis muss die Datei `proxy.conf.json` erstellt werden:

```json
{
   "/efficlient_backend/*": {
       "target": "<https://samdev01>",
       "secure": false,
       "changeOrigin": false
   }
}

```

`/efficlient_backend/` ist dabei der Pfad zum Backend und im `target` steht die URL.
Anschließend muss der `start` Befehl in der package.json erweitert werden:

```json
"start": "ng serve --proxy-config proxy.conf.json",

```

Im Http-Service kann nun ganz einfach über die URL `/efficlient_backend/` auf das Backend zugegriffen werden, **ohne** die Angabe von `https://samdev01`.

## Continuous Integration

- Voraussetzung: Proxy-Einstellungen
- Die `package.json` muss angepasst werden:

```json
"ci:start-server": "npm run start",
"ci:cy-run": "start-server-and-test ci:start-server <http://localhost:4200> cy:run"

```

- Das `gitlab-ci.yml` Skript muss um eine `test` Stage erweitert werden:

```
test:
  stage: test
  script:
    - nvm use 14.20.0
    - npm ci
    - npm run ci:cy-run

```

## Literatur

https://www.udemy.com/course/cypress-end-to-end-testing-getting-started