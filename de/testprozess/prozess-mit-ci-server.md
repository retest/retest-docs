{% extends "de_docs-content.tmpl" %}
{% block primary %}

Der Testprozess mit einem CI-Server
===================================

[Versionsverwaltungssysteme](https://de.wikipedia.org/wiki/Versionsverwaltung) (eng. Version Control System - VCS) und 
[CI-Server](https://de.wikipedia.org/wiki/Kontinuierliche_Integration) gehören heute zum Standardrepertoire an Tools die man bei der Softwareentwicklung einsetzen sollte.

Setzt man beides ein, so ist es besonders einfach ReTest mit diesen zu integrieren.
Dabei sollten die ReTest-Artefakte im Repository des Versionsverwaltungssystems liegen.

Dann gestaltet sich der Testprozess wie folgt:

![Testprozess mit CI-Server und VCS](testprozess-ci.png)

1. Die Tests werden vor deren Ausführung aus dem Versionsverwaltung (VCS) aktualisiert.
2. Der CI-Server führt die Tests jede Nacht aus und erzeugt dabei die `result.replay`-Datei.
3. Der Benutzer kann den Status mit dem HTML-Report und der TAP-Integration direkt online prüfen. Zum Aktualisieren der Tests lädt er die `result.replay`-Datei herunter.
4. Der Benutzer prüft die Testergebnisse und verwirft die Änderungen (wenn es sich um Fehler handelt) oder nutzt ReTest um [mit wenigen Klicks](https://www.retest.de/product/features.html) die Änderungen anzunehmen und die Tests zu pflegen. 
5. Danach committed er die aktualisierten Tests im Versionsverwaltungssystem. Solchermaßen wird auch dokumentiert und nachvollziehbar, wer welche Änderung akzeptiert hat.
6. Entspricht 1.: Beim nächsten Ausführen der Tests aktualisiert der CI-Server die Tests wieder mittels dem Versionsverwaltungssystem.  

{% endblock primary %}