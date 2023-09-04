---
title: 'Masterthesis'
description: 'Ein Performance-Vergleich verschiedener JavaScript Meta-Frameworks im Kontext einer Echtzeit-Applikation'
heroImage: '/masterthesis.png'
---

Die zunehmende Verwendung von JavaScript in Anwendungen hat dazu geführt, dass in
den letzten zehn Jahren einige Bibliotheken und Frameworks veröffentlicht wurden. Im Laufe
dieses Zeitraums haben sich auch die Eigenschaften solcher Softwarepakete entsprechend
an den aktuellen Stand der Zeit angepasst. Wo es vor mehreren Jahren noch darum ging,
ob der Single-Page- oder Multi-Page-Ansatz besser zur Entwicklung von Webanwendungen
geeignet ist, gibt es aktuell eine andere Diskussion rund um Meta-Frameworks. Diese sind
Ergänzungen zu den bisher bekannten Frameworks bzw. Bibliotheken und bieten in der
Regel einige moderne Features an, wie beispielsweise Routing oder serverseitige
Funktionen. Mittlerweile gibt es ein solches Meta-Framework für alle bekannten Bibliotheken
oder Frameworks. React hat NextJs, VueJs hat NuxtJs, Angular hat NestJs, um die drei
Größten zu nennen. Das Problem dabei ist, dass diese Meta-Frameworks im Gesamten erst
wenig untersucht wurden und so ein Vergleich untereinander nur sehr schwierig möglich ist.

Im Kontext von Energiesparmaßnahmen sowie allgemeiner Benutzerzufriedenheit wird
Software in Hinsicht auf ihre Performance und weitere Gesichtspunkte zunehmend häufiger
untersucht. Es gibt demnach auch mehrere Studien, die einen Vergleich von
Frontend-Frameworks untereinander ziehen. Im Bereich der Meta-Frameworks gibt es
aktuell allerdings relativ wenig Ergebnisse, was unter anderem daran liegt, dass viele
Softwarepakete erst vor zwei Jahren veröffentlicht wurden.

Für diese Masterabeit sollen insgesamt die drei Meta-Frameworks für React, SolidJs und Svelte getestet werden,
sprich NextJs, SolidStart und SvelteKit. Als Basis für die Entwicklung dient eine
Echtzeit-Anwendung, die für die späteren Messungen eine hohe Last erzeugen soll. Dabei
handelt es sich um eine Progressive-Web-App (PWA) namens SaarClimb. Die Applikation
richtet sich speziell an Kletterer und Boulderer, die ihren sportlichen Fortschritt tracken
wollen. So lassen sich ganze Trainingspläne erstellen und bestimmte Kletterrouten
eintragen, sodass man seinen persönlichen Fortschritt jederzeit verfolgen kann.
Entsprechend werden Statistiken erstellt und auch andere grundlegende Features wie eine
Bestenliste, ein Profil und so weiter. Zu Beginn des Projektes müssen demnach erst alle
Anforderungen bestimmt werden. Anschließend wird mit Hilfe von Mockups das komplette
Design der Anwendung festgelegt. Daraufhin muss die App in den drei genannten
Frameworks bzw. Meta-Frameworks implementiert werden. Im letzten Schritt erfolgt eine
Performance-Messung für jede App, sodass die Werte der Frameworks und wie diese
abschneiden miteinander verglichen werden können.

## Planung und Design

<br />

### Features

- Kalenderübersicht
- Wochenplaner
- Fortschritt
- Bestenliste
- Profil
- Authentifizierung mit Email und Passwort

### Mockups

Für die bessere Planung wurde für jede der Hauptansichten jeweils ein Mockups erstellt.
Die Designs wurden mit Hilfe der Grafikdesign-Plattform [Canva](https://canva.com/) erstellt.

<div class="mockups" style="text-align:center;display:flex;justify-content:space-between">
    <img src="/projects/mockup-1.png" alt="Mockup 1 - Dashboard" width="250">
    <img src="/projects/mockup-2.png" alt="Mockup 2 - Planer" width="250">
    <img src="/projects/mockup-3.png" alt="Mockup 3 - Fortschritt" width="250">
    <img src="/projects/mockup-4.png" alt="Mockup 4 - Bestenliste" width="250">
</div>

<br />

## Klassendiagramm
<div class="img-hover-zoom" style="box-shadow: var(--box-shadow--light);margin-inline:auto;border-radius:2%;padding:2%;">
    <a href="/projects/class-diagram.png">
        <img src="/projects/class-diagram.png" alt="Klassendiagramm">
    </a>
</div>

<style>
    p {
        text-align: justify;
    }
    .img-hover-zoom img {
        transition: transform .5s ease;
    }
    .img-hover-zoom:hover img {
        transform: scale(1.02);
    }
    @media (max-width: 1100px) {
        div {
            flex-wrap: wrap;
            justify-content: center;
        }
    }
    @media (max-width: 600px) {
        .mockups img {
            width: 50%;
        }
}
</style>
