Dateien und Verzeichnisse in ReTest
===================================

**Dies ist ein Entwurf und wird erst mit RET-594 vollständig implementiert!**

ReTest Installations-Verzeichnis
--------------------------------

Dieser Ordner sollte eine **unberührte** ReTest-Installation beinhalten, 
genau so wie sie durch das entzippen der ReTest-Datei von [https://updates.retest.de/](https://updates.retest.de/) entsteht.

Beim Starten versucht ReTest diesen Ordner zu finden. 
Wenn das start-Skript (<code>retest-gui.bat</code> (Windows) oder <code>retest-gui.sh</code> (Linux/Mac)) 
aus dem ReTest Installations-Verzeichnis heraus kopiert wurde,
muss der Pfad zu diesem Verzeichnis mittels dem Parameter `de.retest.Dir` gesetzt werden.

Um ReTest zu aktualisieren, ersetzen Sie diesen Ordner komplett mit dem Inhalt einer Update.zip-Datei.
Beim automatischen Update werden ältere Versionen mit dem Suffix `_old_$DATE_OF_REPLACEMENT` kurzfristig aufgehobe.

![Warning](../../icons/warning.png) Achtung: Sie sollten *niemals* Dateien in diesem Ordner editieren! 
Sämtliche Änderungen können beim nächsten Update überschrieben werden.


ReTest Workspace
----------------

Dieser Ordner enthält alle veränderlichen Dateien einer ReTest-Installation,
wie die [Konfigurationsdatei](konfigurationsdatei.md), die [Lizenzdatei](lizenz.md) und weitere operationale Dateien.

Standardmäßig befindet sich das Verzeichnis `retest-workspace` auf der gleichen Ebene wie das ReTest Installations-Verzeichnis.
Wenn die System-Property `de.retest.configFile` gesetzt ist, dann wird standardmäßig der Elternordner dieser Datei als Workspace genutzt.
Das Workspace-Verzeichnis kann mit dem System-Property `de.retest.workDirectory` und einer absoluten Pfadangabe gesetzt werden.


System-under-test-Verzeichnis
---------------------------

Dieser Ordner enthält alle Dateien, die benötig werden um die [SUT](../testprozess/was-ist-die-sut.md) zu starten.
Standardmäßig (z.B. für die [Demo](https://update.retest.de/demo)) befindet sich dieses Verzeichnis neben der ReTest-Intallation unter dem Namen `system-under-test`. 
Sollte es sich bei Ihrer Anwendung um eine WebStart-Anwendung handeln, so wird dieser Ordner erstellt und alle `jar`-Dateien werden dorthin abgespeichert.
Name und Pfad können mit dem System-Property `de.retest.sut.applicationPath` angepasst werden.


Ausführungsverzeichnis
----------------------

Aus diesem Verzeichnis heraus wir die SUT gestartet. Derzeit muss dies auch das Ausführungsverzeichnis von ReTest selbst sein.
Standardmäßig ist dies das System-under-test-Verzeichnis. 
Name und Pfad können mit dem System-Property `de.retest.sut.executionDirectory` angepasst werden.

