---
title: 'Maven Archetypes'
description: 'Tutorial für die Erstellung und Verwendung von Archetypes in Maven'
pubDate: 'Jul 10 2023'
heroImage: '/maven-archetypes.png'
---

## Allgemein

- Projekt-Template, von dem andere Projekte erstellt werden können
- Maven Projekte können mitt dem *maven-archetype-plugin* generiert werden

## Archetype erstellen

- Mit `mvn archetype:create-from-project` kann ein Maven Archetype von einem bestehenden Projekt erstellt werden
- Das neue Projekt ist dann unter `target/generated-sources/archetype` zu finden

## Archetype bauen

- Packaging der *pom.xml* im root-Verzeichnis aus pom setzen: <br>
  `<packaging>maven-archetype</packaging>`
- distributionManagement für den deploy hinzufügen:

```xml
<distributionManagement>
        <repository>
            ...
        </repository>
        <snapshotRepository>
            ...
        </snapshotRepository>
    </distributionManagement>
```

- `mvn clean install` im root Verzeichnis des Archetypes
- `mvn deploy` im root Verzeichnis des Archetypes zum Veröffentlichen ins Artifactory

## Projekt generieren

### 1) Kommandozeile

- Root-Verzeichnis des Projektes öffnen
- `mvn archetype:generate`
- Danach eine Nummer auswählen → Die Nummer mit der entsprechenden groupId und artifactId
- Dann die einzelnen Parameter eingeben
- Das Projekt ist anschließend im gleichen Ordner zu finden

### 2) Eclipse

- Neues Maven-Projekt anlegen
- Archetype auswählen
- `groupId` und `artifactId` eingeben
- Das Projekt ist anschließend im gleichen Ordner zu finden


## Referenz
- https://github.com/ikos23/maven-archetype-sample
