{% extends "review-content.tmpl" %} {% block primary %}

Unterschiede
============

Werden beim Vergleich der Attribute der Elemente Unterschiede festgestellt, so werden diese Unterschiede in der
Detailansicht angezeigt.

![GUI-Screenshot von ReView mit Unterschieden](ergebnisse-unterschiede-1.png)

Die Unterschiede werden pro Aktion angezeigt (1), sind in der Baumstruktur aber auch nochmal nach Struktur gruppiert
(2). In der Detailansicht wird ein Screenshot der Maske mit deren Zustand während der Umwandlung angezeigt, alle
Unterschiede sind hierbei im Screenshot rot markiert (3). Daneben wird der Zustand der Maske beim Abspielen angezeigt.
Die Markierungen aus dem erwarteten Zustand werden dargestellt, um zu verdeutlichen, wo die Elemente erwartet worden
wären (4).

In der Tabelle darunter hat man die Möglichkeit, die gewollten Unterschiede einzeln mit einem Haken zu markieren (5).
Optional kann man auch alle Unterschiede durch einen Klick auf "Alle annehmen" im Tabellen-Header auf einmal annehmen
(6). Nach dem Annehmen werden die Elemente in der Baumstruktur, bei denen alle Unterschiede angenommen wurden,
entsprechend grün markiert (7). Wurden alle Unterschiede in der Aktion angenommen, wird auch die Aktion grün markiert.
Wurden alle Unterschiede in allen Aktionen angenommen, so wird der Test grün markiert. Und wurden alle Unterschiede in
allen Tests angenommen, so wird die Suite grün markiert.

![GUI-Screenshot von ReView mit Unterschieden](ergebnisse-unterschiede-2.png)

Um die solchermaßen bestätigten Unterschiede dauerhaft zu speicher und damit gleich die Suites zu pflegen, muss man nun
noch auf "Änderungen anwenden" (8) klicken. Verwendet man ein
[Versionskontrollsystem](../testprozess/prozess-mit-ci-server.md), so muss man in diesem die aktualisierten Suites noch
kommitten.

Es besteht auch die Möglichkeit [Unterschiede dauerhaft zu ignorieren](ui-elemente-ignorieren.md).

{% endblock primary %}
