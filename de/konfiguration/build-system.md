{% extends "de_docs-content.tmpl" %}
{% block primary %}

Integration in ein Build-System
===============================

Wird ReTest bspw. in ein Build-System integriert, so sollte die Ausführung nicht über die GUI erfolgen.
Generell ist es sinnvoll, ReTest dauerhaft in Ihr Build-System zu integrieren. 
Dazu gibt es derzeit drei Möglichkeiten:

1. Ausführung direkt über die [Kommandozeile](https://de.wikipedia.org/wiki/Kommandozeile).
2. Ausführung über [Ant](http://ant.apache.org).
3. Ausführung über [Maven](https://maven.apache.org).

Durch die Möglichkeit der Ausführung über die Kommandozeile, ist die Integration in gängige Build-Systeme problemlos möglich.
Falls Sie hierbei Unterstützung benötigen, so sprechen Sie uns gerne an.
Haben Sie eine Integration durchgeführt, so lassen Sie es uns wissen, damit wir dies hier dokumentieren können.

Bei allen drei Schnittstellen stehen Ihnen folgende Befehle zur Verfügung:

1. Konvertieren von Suites
2. Generieren von Suites
3. Abspielen von Suites
4. Automatisches Updaten von ReTest 
5. Migrieren von Dateien nach einem ReTest-Update

## Ausführung über die Kommandozeile

Die Ausführung über die Kommandozeile erfolgt über den `java`-Befehl, bspw. aus aus dem Verzeichnis Ihrer Anwendung:

```
java -Dde.retest.workDirectory=<Pfad zum retest-workspace> -Dde.retest.Dir=<Pfad-zu-ReTest> -Xmx512M -noverify -server -XX:+UseParallelGC -cp <Pfad-zu-ReTest>/retest.jar <ReTest-Main-Klasse> execsuites/Meine_Suite.execsuite
```

Bei der Ausführung über die Kommandozeile benutzen Sie bitte entsprechend die folgenden Klassen beim Aufruf:

1. `de.retest.TestConvert` zum Konvertieren von Suites.
2. `de.retest.TestGenerator` zum Generieren von Tests und zum Monkey Testing.
3. `de.retest.TestReplayer` zum Abspielen von Suites.
4. `de.retest.UpdateReTest` zum Aktualisieren von ReTest.
5. `de.retest.TestMigrator` zum Migrieren von ReTest-Dateien nach einem Update.

In den Fällen 1, 2 und 3 wird als Argument eine Liste Suites (1) bzw. ExecSuites (2 und 3), getrennt durch Semikolon, erwartet. Wird kein Argument übergeben, so werden alle Suites bzw. ExecSuites verwendet. Zur Migration können beliebige Dateien (Actions, Tests und ExecSuites), ebenfalls getrennt durch Semikolon, übergeben werden. Wird hierbei kein Argument mitgeliefert, dann werden alle Actions, Tests und ExecSuites migriert. Im Falle eines Updates (5) ist kein Argument notwendig.

## Ausführung über Ant

ReTest kann ebenfalls via Ant ausgeführt werden. 
Hierfür stehen für die o. g. Aufgaben (Aufnehmen, Abspielen, Generieren etc.) vorgefertigte Tasks zur Verfügung. 
Ein entsprechendes funktionierendes Beispiel findet sich in der ReTest-Demo (https://update.retest.de/demo) in der `build.xml` (im ReTest-Workspace), welche Sie für Ihre eigenen Zwecke adaptieren können.

Die Tasks zum Konvertieren, Abspielen und Generieren können mit [Ant-FileSets](https://ant.apache.org/manual/Types/fileset.html) sehr flexibel konfiguriert werden.

## Ausführung über Maven

*TODO*

{% endblock primary %}
