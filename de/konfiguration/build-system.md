{% extends "de_docs-content.tmpl" %}
{% block primary %}

Integration in ein Build-System
===============================

Z.B. bei der [Integration in einen CI-Server](ci.md) sollte ReTest nicht über die GUI ausgeführt werden.
Generell ist es sinnvoll ReTest dauerhaft in Ihr Build-System zu integrieren. 
Dazu gibt es derzeit 3 Möglichkeiten:

1. Ausführung direkt über die [Kommandozeile](https://de.wikipedia.org/wiki/Kommandozeile).
2. Ausführung über [Ant](http://ant.apache.org).
3. Ausführung über [Maven](https://maven.apache.org).

Durch die Möglichkeit der Ausführung über die Kommandozeile sollten Integrationen in weitere Build-Systeme problemlos möglich sein.
Falls Sie hierbei Unterstützung benötigen, so sprechen Sie uns gerne an.
Falls Sie eine Integration durchgeführt haben, so lassen Sie es uns wissen, dann können wir dies hier dokumentieren.

Bei allen drei Schnittstellen stehen Ihnen folgende Befehle zur Verfügung:

1. Konvertieren von Suites
2. Generieren von Suites
3. Abspielen von Suites
4. Automatisches Updaten von ReTest 
5. Migrieren von Dateien nach einem ReTest Update

## Ausführung über die Kommandozeile

Die Ausführung über die Kommandozeile funktioniert mittels einem installierten Java, bspw. aus dem Verzeichnis Ihrer Anwendung:

```
java -Dde.retest.workDirectory=<Pfad zum retest-workspace> -Dde.retest.Dir=<Pfad-zu-ReTest> -Xmx512M -noverify -server -ea -esa -XX:+UseParallelGC -cp <classpath> <ReTest-Main-Klasse> execsuites/Meine_Suite.execsuite
```

Bei der Ausführung über die Kommandozeile benutzen Sie bitte entsprechend die folgenden Klassen beim Aufruf:

1. `de.retest.TestConvert` zum Konvertieren von Suites. 
   Als Argument liefern Sie hier bitte einfach die zu konvertierenden Suites.
2. `de.retest.TestGenerator` zum Generieren von Tests und Monkey-Testen Ihrer Anwendung.
3. `de.retest.TestReplayer` zum Abspielen von Suites. 
   Als Argument liefern Sie hier bitte einfach die Suites die abgespielt werden sollen.
   Geben Sie kein Argument an, so werden _alle_ Suites abgespielt.
4. `de.retest.UpdateReTest` zum Aktualisieren von ReTest.
5. `de.retest.TestMigrator` zum Migrieren von ReTest-Dateien nach einem Update. 
   Als Argument liefern Sie hier bitte einfach die Suites die abgespielt werden sollen. 
   Geben Sie kein Argument an, so werden _alle_ Dateien migriert.

## Ausführung über Ant

ReTest kann über eigene Tasks in eine `build.xml` in Ant integriert werden.
Ein vorgefertigtes und funktionierendes Beispiel hierzu wird in der [ReTest-Demo](https://update.retest.de/demo) mitgeliefert (in `retest-workspace/build.xml`).
Es sollte relativ einfach sein, dieses Beispiel auf Ihre Zwecke zu adaptieren.

Die Tasks zum Konvertieren, Abspielen und Migrieren können mit [Ant-FileSets](https://ant.apache.org/manual/Types/fileset.html) sehr flexibel konfiguriert werden.

{% endblock primary %}