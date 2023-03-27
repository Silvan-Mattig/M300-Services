M300 - 35 Container-Sicherheit
=== 

Inhaltsverzeichnis
===

[Protokollieren & Überwachen](https://github.com/Silvan-Mattig/M300-Services/tree/main/35%20Container-Sicherheit#protokollieren--%C3%BCberwachen)

[Container sichern & beschränken](https://github.com/Silvan-Mattig/M300-Services/tree/main/35%20Container-Sicherheit#container-sichern--beschr%C3%A4nken)

[Kontinuierliche Integration](https://github.com/Silvan-Mattig/M300-Services/tree/main/35%20Container-Sicherheit#kontinuierliche-integration)

Protokollieren & Überwachen
===

In der Informatik ist die Sicherheit immer an der ersten Stelle. Darum sollte man ebenfalls bei den Container auf die Sicherheit achten. Bei Komplexen Systemen zb. (Wenn mehrere Container mit eineinander verbunden sind.)  ist es natürlich noch wichtiger, dass die Systeme reibbungslos laufen. 

Für die Sicherheit der Container ist das protokollieren einer der Wichtigsten Punkten. Wenn man keine Logging-Software angegeben hat, protokolliert Docker nur das was an STDOUT STDERR geschickt wird.

Wenn du eine Anwendung in einem Docker-Container startest, kannst du das Verhalten der Anwendung überwachen, indem du die Ausgabe auf die Standardausgabe (STDOUT) oder die Standardfehlerausgabe (STDERR) sendest. STDOUT und STDERR sind Kanäle, über die Anwendungen mit der Umgebung kommunizieren. STDOUT wird normalerweise für die normale Ausgabe von Anwendungen verwendet, während STDERR für Fehlermeldungen und Warnungen verwendet wird.

Docker protokolliert standardmäßig alles, was an STDOUT oder STDERR geschickt wird, und speichert die Ausgabe in einem Container-Log-File. Dieses Log-File kann dann verwendet werden, um das Verhalten der Anwendung zu überwachen oder Probleme zu erkennen.

Sinnvoll ist natürlich, dass man diese Logs dann auch anschauen kann. Dazu muss man folgenden Behfel eingeben:

```
docker logs
```

| Logging-Methode | Beschreibung                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------|
| json-file       | Diese Methode schreibt die Container-Logs als JSON-Datei auf die Festplatte des Host-Systems.   |
| syslog          | Diese Methode schickt die Logs an das System-Logging-Tool (syslog) des Host-Systems.           |
| journald        | Diese Methode schickt die Logs an das System-Logging-Tool (journald) des Host-Systems.         |
| splunk          | Diese Methode schickt die Logs an eine Splunk-Instanz. Splunk ist eine Software zur Analyse von Maschinendaten. |
| awslogs         | Diese Methode schickt die Logs an Amazon CloudWatch Logs. CloudWatch Logs ist ein verwalteter Log-Service von Amazon Web Services. |



Container sichern & beschränken
===

Kontinuierliche Integration
===



