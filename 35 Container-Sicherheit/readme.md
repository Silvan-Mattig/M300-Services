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

Diese Liste ist nicht vollständig und es gibt noch weitere Logging-Methoden, die man über --log-driver auswählen kann. Man kann auch eigene Logging-Methoden implementieren, indem man ein Docker-Plugin erstellt.

### Wichtige Behfehle für Standard-Logging ###

| Befehl                                | Beschreibung                                                                                                                                                                      |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `$ docker run --name logtest ubuntu bash -c 'echo "stdout"; echo "stderr" >>2'` | Startet einen neuen Container `logtest` auf Basis des `ubuntu`-Images. Der Befehl gibt "stdout" auf STDOUT aus und gibt "stderr" auf STDERR aus. |
| `$ docker logs logtest`               | Zeigt die Logs des Containers `logtest` an.                                                                                                                                        |
| `$ docker rm logtest`                 | Entfernt den Container `logtest`.                                                                                                                                                  |
| `$ docker run -d --name streamtest ubuntu bash -c 'while true; do echo "tick"; sleep 1; done;'` | Startet einen neuen Container `streamtest` auf Basis des `ubuntu`-Images. Der Befehl gibt alle Sekunde "tick" aus. |
| `$ docker logs streamtest`            | Zeigt die Logs des Containers `streamtest` an.                                                                                                                                     |
| `$ docker logs streamtest \| wc -l`   | Zählt die Anzahl der Zeilen in den Logs des Containers `streamtest`.                                                                                                              |
| `$ docker rm streamtest`              | Entfernt den Container `streamtest`.                                                                                                                                                |

Protokollierung System-Log des Hosts:
```
    docker run -d --log-driver=syslog ubuntu bash -c 'i=0; while true; do i=$((i+1)); echo "docker $i"; sleep 1; done;'
```
```
    $ tail -f /var/log/syslog
```

### Überwachen und Benachrichtigen ###

Wenn man als System Administrator bei einem Microservices-System arbeitet, ist man um jede Hilfe froh. Deswegen werden in solchen grossen unternehmen immer Benachrichtungen integriert. Damit man eine Benachrichtung bekommt, wenn ein System schiefläuft. Damit man nicht Hunderte oder Tausende Container aufeinmal im überblick haben muss, gibt es zum beispiel "Container Advisor". Dieses Tool von Google ermöglicht es alle Systeme auf einen Blick zu sehen. Somit ist die Warscheindlichkeit kleiner, dass ein System den Geist aufgibt.

 Da cAdvisor selbst als Container zur Verfügung steht, können wir das Tool in kürzester Zeit zum Laufen bringen. Gestartet wird der cAdvisor-Container mit folgenden Argumenten:

    $ docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080


 
Container sichern & beschränken
===


## Sicherheitsprobleme ##



## Berechtigungs-Verteilung ##


## Container absichern ## 

## Weitere Sicherheitstipps ## 

Kontinuierliche Integration
===



