{% extends "recapture-content.tmpl" %}
{% block primary %}

Aktionsfolge skripten
=====================

___
![Warning](../../icons/warning.png) Achtung: Folgendes Feature ist nur im Power-User-Mode verfügbar!
___

Das Skripten einer Aktionsfolge erlaubt zusätzlich zu dem [Editieren einer Aktionsfolge](aktionsfolge-bearbeiten.md), dass einzelne Aktionen direkt verändert werden können. Dabei lassen sich die Werte der Aktion (Aktionsattribute) oder sogar die Ziele der Aktion (Identifikationsattribute) verändern.

Es können hier die Variablenname für das [Skripten von Suites](suite-skripten.md) definiert werden, um dynamisch beim Umwandeln der Suite mehrere *execsuites* für den gleichen Ablauf zu generieren.

### Aktionsattribute

Die Aktionsattribute definieren, was eine Aktion ausführt. So lässt sich über die Aktionsattribute der Text verändern, der in ein Textfeld eingetragen wird oder anstatt eine andere Datei beim Datei-Dialog auswählen.

### Identifikationsattribute

Die Identifikationsattribute definieren das Ziel der Aktion. So lässt sich durch Verändern der Attribute ein anderes Ziel (z.B. das darunterliegende Textfeld) ausgewählt werden.

Da retest alle Attribute nutzt, um das entsprechede Ziel zu finden, reicht es meist nicht, dass man nur den Text einer Schaltfäche ändert. Will man jedoch nur das Ziel ändern, ist es meist genauer, eine Aktion auf dem neuen Ziel aufzuzeichnen. Das kann auch verwendet werden, um die zugehörigen Attribute des Ziels für die Variablennamen herauszufinden und diese dann auf die gewüschte Aktion zu übertragen.

### Variablen

Mit Variablennamen wird ein Attribut identifizierbar. Der Name kann für das [Skripten von Suites](suite-skripten.md) verwendet werden, um andere Werte beim Umwandeln in die Attribute zu füllen, damit das oben beschriebene Verhalten erzielt wird. Mehr Informationen beim [Skripten von Suites](suite-skripten.md).

### Bearbeiten der Aktion

Nach dem Öffnen einer Aktion kann man im Tab Aktionsdetails die Werte und Variablennamen der Aktion ändern bzw. setzen.

Um ein Wert oder einen Variablenname zu ändern, einfach in die Tabelle auf das entsprechende Feld klicken und editieren. Ist das Feld nicht editierbar, so wird das Ändern des Werts bzw. Setzen des Variablennamens nicht unterstützt.

Das setzen eines Variablennamens hat für sich alleine keine Auswirkung auf das Abspielen einer Aktion. Diese werden beim [Scripten von Suites](suite-skripten.md) verwendet.

Nach durchgeführten Änderungen, muss die Aktion abgespeichert werden.

## Achtung

Das starke Verändern einer Aktion kann den Ablauf der Aktionsfolge beeinflussen. Diese Änderungen müssen entweder manuell durch das Einfügen zusätzlicher Aktionen korrigiert werden oder im [Adaptionsregeln](../replay/adaptions-regeln.md)

{% endblock primary}