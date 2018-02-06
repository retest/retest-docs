Der TestContext
===============

Der `TestContext` wird für die gesamte [Interaktion zwischen ReTest und SUT](architektur.md) genutzt.

Welche `TestContext`-Klasse von ReTest verwendet wird kann mittels des Properties `de.retest.TestContextClass` zentral konfiguriert werden. 
Die konfigurierte Klasse muss sich im Klassenpfad oder im `extensions`-Verzeichnis im ReTest [`workspace`](../konfiguration/verzeichnisse.md) befinden. 

Der TestContext stellt mehrere Methoden bereit, die überschrieben werden können -- je nachdem, welche Funktionalität von ReTest benötigt wird.

Reine Zustandsprüfung
---------------------

Wird der zu prüfende Zustand extern herbeigeführt, und ReTest nur für die Prüfung eines Interfaces genutzt, so genügt es den `ReViewTestContext` bzw. die Methode `getSutInterfaces` zu implementieren.

	/** 
	 * Returns the state of all interfaces of the SUT, 
	 * that should be checked by ReTest. 
	 **/
    Collection<Interface> getSutInterfaces();

Diese Methode gibt eine [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) an `Interfaces` zurück.
Jedes Interface stellt eine Schnittstelle zur [SUT](../testprozess/was-ist-die-SUT.md) dar. 
Dies kann eine GUI sein wie z.B. eine Swing-Oberfläche, aber auch etwas triviales, wie z.B. eine Auflistung der vorhandenen Ausgabedateien in einem speziellen Ordner.

Jedes Interface implementiert die Methode

    /**
     * Returns the current state of this interface
     * in terms of InterfaceElements.
     */
    Collection<InterfaceElement> getInterfaceElements();


welche jeweils einen Baum von Elementen (vom Typ `Element`) beinhalten. Dieser Kontext wird z.B. implementiert um PDF-Dateien, XML-Dateien bzw. REST-Ergebnisse, etc. miteinander zu vergleichen.

Interaktion mit der SUT
-----------------------

Soll ReTest die SUT ebenfalls ansteuern können, so muss der `RePlayTestContext` implementiert werden. 
Dieser hat schon wesentlich mehr Funktionalität:

    /** Launches the SUT. Called before executing actions. **/
    void launchSut() throws Exception;

    /** Closes the SUT after ending a test case. **/ 
    void closeSut();

    /** 
     * Return a collection of StabilizationDetectors, 
     * each of which detects whether a certain part of the system has stabilized 
     * (i.e. is not loading or calculating anymore.). 
     **/
    Collection<StabilizationDetector> getStabilizationDetectors();
    
    /** 
     * Return a collection of ErrorDetectors, 
     * each of which detects whether an error occurred in the system
	 **/ 
    Collection<ErrorDetector> getErrorDetectors();
    
    /** Returns a collection of SystemExitDetectors
     * each of which detects whether a part of the system has exited.
     **/
    Collection<SystemExitDetector> getSystemExitDetectors();
    
Die Methoden `launchSut` und `closeSut` starten und stoppen die SUT.
Darüber hinaus gibt es je nach Scenario beliebig viele `StabilizationDetectors` 
welche die simple Methode `hasStabilized` implementieren, 
und detectieren ob sich ein Teil des Systems stabilisiert hat.
Erst wenn sich alle Teile des Systems stabilisiert haben wird die nächste Aktion ausgeführt.
Durch die Verwendung dieses Mechanismus kann auf das Warten auf GUI-Elemente verzichtet werden,
was die Verwendung von ReTest viel robuster und anwenderfreundlicher macht.

    /**
     * Returns true if the SUT has stabilized.
     */
    boolean hasStabilized();

Analog gibt es `ErrorDetectors`, welche prüfen ob es in einem Teil des Systems 
(bspw. in der Log-Ausgabe oder auf dem Web-Server) zu einem Fehler gekommen ist.
Und es gibt `SystemExitDetectors`, welche kontinuierlich prüfen, ob noch alle 
System laufen und ansprechbar sind. 

Außerdem wird erwartet, dass der `TestContext` mindestens ein `ExecutableInterface` zurückgibt, 
welches Ziel von Aktionen sein kann. Dazu implementiert es die Methode `execute`,
welche eine einzelne Aktion auf dem Interface der SUT ausführt.
 
     /** Executes a single action. **/
    void execute( Action action );

Aufzeichnen von Tests
---------------------

Damit das Aufzeichnen von Tests möglich ist, muss der `ReCaptureTestContext` implementiert werden.


