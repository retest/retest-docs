Wie man ReTest konfiguriert
===========================

Damit ReTest ihre SUT starten kann, muss man ein paar passende Werte in die [`retest.properties`-Datei](../konfiguration/konfigurationsdatei.md) eintragen.

Auf UNIX
--------

Auf einem UNIX-System kann man diese Werte am einfachsten bestimmen, indem Sie ihre übliche `.sh`-Datei, die Sie normalerweise zum Starten Ihrer Anwendung benutzen, 
mit `bash -x <your.sh>` ausführen. Mit diesem Parameter sieht man genau, welche Befehle (nach Auflösen aller Variablen) tatsächlich ausgeführt werden.

Der letztendlich ausgeführte Befehl sollte in etwa diese Form haben:
    
    exec java -DsomeParam=someValue <...some more params...> -cp <...some paths and .jar-files...> com.your.Main <...some program arguments...>
    
Jetzt müssen Sie folgendes tun:

- Die Konfigurationsparameter (dem Aussehen nach `-DsomeParam=someValue`) in die Datei `retest-gui.sh` hinter `javaArgs=` eintragen.
- Die Pfade und Dateien hinter dem `-cp` in die `retest.properties`-Datei als Parameter `de.retest.sut.dependenciesClassPath=` eintragen. Eventuell müssen Sie hier alle `;` mit `:` ersetzen.
- Die Main-Klasse in die in die `retest.properties`-Datei als Parameter `de.retest.sut.mainClass=` eintragen.
- Und Programm-Argumente (falls vorhanden) in die `retest.properties`-Datei als Parameter `de.retest.sut.mainArgs=` eintragen.

