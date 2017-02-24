{% extends "review-content.tmpl" %}
{% block primary %}

UI-Elemente dauerhaft ignorieren
================================

Man auch die Möglichkeit UI-Elemente dauerhaft zu ignorieren.

Grundsätzlich sollte man versuchen eine stabile Testumgebung aufzubauen.
Trotzdem gibt es dann immernoch volatile Elemente, wie das Tagesdatum oder die Build-Version.
Obwohl dies je nach Anwendung natürlich variiert, so sollte sich die Anzahl dieser Elemente unserer Erfahrung nach jedoch in Grenzen halten.

Um ein Element dauerhaft zu ignorieren kann man es direkt [in der Anwendung markieren](../replay/ui-elemente-ignorieren.md), 
oder es im Nachgang beim [Reviewen der Ergebnisse](index.md) markieren.

![GUI Screenshot UI Elemente ignorieren](ui-elemente-ignorieren-1.png)

Dazu muss man entweder in der Tabelle auf das Element klicken oder das Element in der Baumansicht auswählen.

![Warning](../../icons/warning.png) Achtung: Unterschiede in ignorierten UI-Elemente *und allen Kind-Elementen* werden beim Ausführen einer Suite nicht mehr überprüft!

Man kann sich sich auch jederzeit [anschauen](../replay/ui-elemente-ignorieren.md), welche Elemente derzeit ignoriert werden.

{% endblock primary %}