---
title: 'Rendering Strategien'
description: 'Wie werden Webanwendungen in der modernen Webentwicklung gerendert?'
pubDate: 'Sep 07 2023'
heroImage: '/assets/Rendering_Strategien.png'
---

Bei jedem Aufruf einer Webseite rendert der Browser die Seite, damit sie dem Nutzer angezeigt werden kann und eine 
entsprechende Interaktivität bietet. Dabei gibt es verschiedene Strategien, wie Webseiten gerendert werden können.
Am Wichtigsten sind hierbei Client Side Rendering (CSR) und Server Side Rendering (SSR)[^Ionos].

## Server Side Rendering
SSR kommt bei der Entwicklung von Webseiten mit dynamischen Elementen zum Einsatz. Dabei wird die Seite auf dem Server
gerendert und anschließend an den Client gesendet. Dieser erhält also eine vollständige HTML-Seite, die er direkt
anzeigen kann[^Ionos]. Die Seite ist also bereits vollständig gerendert, bevor sie angezeigt wird. Dies hat den Vorteil, dass
die Seite auch ohne JavaScript funktioniert. Insbesondere für statische Webseiten mit vielen Bildern und Elementen
eignet sich der SSR-Ansatz dank der optimierten Ladegeschwindigkeit sehr gut[^Ionos]. Außerdem wirkt sich das schnelle
Laden der Seite positiv auf die Bewertung der Seite durch Suchmaschinen aus, da der Webcrawler die Seite schneller erfassen kann.
Der Nachteil ist, dass die Seite bei jedem Aufruf neu gerendert werden muss, was zu einer schlechteren Performance führt.
Hinzu kommt eine starke Auslastung der Serverkapazitäten, wenn der Client viele Anfragen an den Webserver sendet[^Ionos].

## Client Side Rendering
CSR wird bei der Entwicklung vorrangig für dynamische Inhalte verwendet. Dabei wird die Seite zunächst ohne Inhalte
gerendert und anschließend wird die Seite vom Browser mithilfe von JavaScript mit Inhalten gefüllt[^Ionos].
Dieser Ansatz ist vor allem für Webanwendungen mit vielen dynamischen Inhalten geeignet, da die Inhalte erst beim Aufruf der Seite geladen werden.
Im Gegenteil zum SSR bietet sich dieser Ansatz für Webanwendungen an, die viele Anfragen an den Server senden, da die
Serverkapazitäten geschont werden. Außerdem ist der Ansatz für Webanwendungen mit vielen dynamischen Inhalten geeignet,
da die Inhalte erst beim Aufruf der Seite geladen werden. Der Nachteil ist, dass die Seite ohne JavaScript nicht funktioniert.
Zudem ist die Suchmaschinenoptimierung (SEO) bei diesem Ansatz schwieriger, da der Webcrawler die Seite nicht
vollständig erfassen kann[^Ionos].


## Literatur
[^Ionos]: Redaktion, Ionos. Client-, Server-Side-Rendering und Static-Site-Generation im Vergleich 
https://www.ionos.de/digitalguide/websites/web-entwicklung/server-side-und-client-side-scripting-die-unterschiede/

[^Rendering]: Miller, Jason. Rendering on the Web https://web.dev/rendering-on-the-web/