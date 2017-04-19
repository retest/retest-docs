{% extends "de_docs-content.tmpl" %} {% block primary %}

Dateien und Verzeichnisse in ReTest
===================================

**Achtung:** Dies ist ein noch unvollständiger Entwurf!

ReTest-Installationsverzeichnis
-------------------------------

Dieser Ordner sollte eine *unberührte* ReTest-Installation beinhalten, genau so wie sie durch das Entpacken der
ReTest-Datei von https://updates.retest.de/ entsteht.

Beim Starten versucht ReTest diesen Ordner zu finden. Wenn das start-Skript (`retest-gui.bat` (Windows) oder
`retest-gui.sh` (Linux/Mac)) aus dem ReTest-Installationsverzeichnis heraus kopiert wurde, muss der Pfad zu diesem
Verzeichnis mittels dem Parameter `de.retest.Dir` gesetzt werden.

Um ReTest zu aktualisieren, ersetzen Sie diesen Ordner komplett mit dem Inhalt der neuen ZIP-Datei. Beim automatischen
Update werden ältere Versionen mit dem Suffix `_old_$DATE_OF_REPLACEMENT` versehen.

![Warning](../../icons/warning.png) **Achtung:** Sie sollten *niemals* Dateien in diesem Ordner editieren! Sämtliche
Änderungen können beim nächsten Update überschrieben werden.

ReTest-Workspace
----------------

Dieser Ordner enthält alle veränderlichen Dateien einer ReTest-Installation, wie die
[Konfigurationsdatei](konfigurationsdatei.md), die [Lizenzdatei](lizenz.md) und weitere operationale Dateien.

Standardmäßig befindet sich das Verzeichnis `retest-workspace` auf der gleichen Ebene wie das
ReTest-Installationsverzeichnis. Wenn die System-Property `de.retest.configFile` gesetzt ist, dann wird standardmäßig
der Elternordner dieser Datei als Workspace genutzt. Der ReTest-Workspace kann mit der System-Property
`de.retest.workDirectory` und einer absoluten Pfadangabe gesetzt werden.

SUT-Verzeichnis
---------------

Dieser Ordner enthält alle Dateien die benötig werden, um die [SUT](../testprozess/was-ist-die-sut.md) zu starten.
Standardmäßig (z. B. für die [Demo](https://update.retest.de/demo)) befindet sich dieses Verzeichnis neben dem
ReTest-Installationsverzeichnis unter dem Namen `system-under-test`. Sollte es sich bei Ihrer Anwendung um eine
Web-Start-Anwendung handeln, so wird dieser Ordner erstellt und alle JAR-Dateien werden dorthin abgespeichert. Name und
Pfad können mit der System-Property `de.retest.sut.applicationPath` angepasst werden.

ReTest-Ausführungsverzeichnis
-----------------------------

Aus diesem Verzeichnis heraus wir die SUT gestartet. Derzeit muss dies auch das ReTest-Ausführungsverzeichnis von ReTest
selbst sein. Standardmäßig ist dies das SUT-Verzeichnis. Name und Pfad können mit der System-Property
`de.retest.sut.executionDirectory` angepasst werden.

{% endblock primary %}
