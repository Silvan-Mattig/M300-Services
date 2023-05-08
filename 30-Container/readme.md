M300 - 30 Container
===

Inhaltsverzeichnis
===

[Container](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#container)

[Docker](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#docker)

[Docker Architecktur](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#docker-architecktur)

[Dockerfile](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#dockerfile)

[Image-Bereitstellung](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#image-bereitstellung)


Container
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Ein Container ist ein Konzept der Informatik, das hilfreich ist, um Anwendungen in einer Umgebung auszuführen, die isoliert und unabhängig von anderen Anwendungen und dem Betriebssystem des Computers ist.

Ein Vorteil von Containern ist, dass sie portabel sind und auf verschiedenen Betriebssystemen und Servern ausgeführt werden können, solange sie die Container-Software unterstützen. Durch die Verwendung von Containern können Anwendungen schneller bereitgestellt und skaliert werden, da sie unabhängig von der zugrunde liegenden Infrastruktur sind und somit schneller und einfacher bereitgestellt werden können.

Docker
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

## Wichtige Befehle für Docker ##

| Befehl | Beschreibung |
| --- | --- |
| `docker build` | Baut ein Docker-Image aus einem Dockerfile |
| `docker run` | Startet einen Docker-Container aus einem Docker-Image |
| `docker stop` | Stoppt einen laufenden Docker-Container |
| `docker rm` | Löscht einen Docker-Container |
| `docker rmi` | Löscht ein Docker-Image |
| `docker ps` | Zeigt eine Liste der laufenden Docker-Container an |
| `docker images` | Zeigt eine Liste der verfügbaren Docker-Images an |
| `docker exec` | Führt einen Befehl in einem laufenden Docker-Container aus |
| `docker-compose up` | Startet Docker-Container mit Docker Compose |
| `docker-compose down` | Stoppt Docker-Container mit Docker Compose und löscht sie |
| `docker save` | Speichert ein Docker-Image als Tar-Datei |
| `docker load` | Lädt ein Docker-Image aus einer Tar-Datei |
| `docker login` | Meldet sich bei Docker Hub oder einer anderen Docker-Registry an |
| `docker push` | Lädt ein Docker-Image auf Docker Hub oder eine andere Docker-Registry hoch |
| `docker pull` | Lädt ein Docker-Image von Docker Hub oder einer anderen Docker-Registry herunter |

# Installation Docker Desktop und Aktivierung von WSL2 #

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

1. Laden Sie Docker Desktop für Windows herunter. 

Dazu kann man direk auf diese Webseite gehen. [Docker-Desktop](https://www.docker.com/products/docker-desktop/)

2. Führen Sie den Installationsassistenten aus. 

Öffnen Sie die heruntergeladene Datei "DockerDesktopInstaller.exe" und folgen Sie den Anweisungen des Installationsassistenten.

3. Konfigurieren Sie Docker Desktop. 

Nach Abschluss der Installation startet Docker Desktop automatisch. Möglicherweise müssen Sie jedoch den Computer neu starten, um Docker Desktop ordnungsgemäß zu starten. In den Einstellungen sollten man die Option "Use the WSL 2 based engine" auswählen. Wenn Sie dies tun, wird Docker Desktop WSL2 als Engine verwenden.

4. Aktivieren Sie WSL2.

Öffnen Sie ein PowerShell-Fenster als Administrator und führen Sie den folgenden Befehl aus, um WSL2 als Standardversion von WSL zu aktivieren:

```
wsl --set-default-version 2
```

Wenn man den Befehl ausgeführt hat, sollte man die folgende Meldung bekommen:
![WSL2 aktivieren](../Screenshot/WSL2%20Command.png)

5. Installieren Sie eine Linux-Distribution.

Da Docker Desktop WSL2 als Engine verwendet, benötigen Sie eine Linux-Distribution, die auf Ihrem Computer ausgeführt werden kann. Ich empfehle Ubuntu 22.04.2 LTS:

![Ubuntu 22.04.2 LTS](../Screenshot/Ubuntu%2022.04.2%20LTS.png)


6. Überprüfen Sie die Installation.

Öffnen Sie ein PowerShell-Fenster und führen Sie den folgenden Befehl aus, um zu überprüfen, ob Docker Desktop ordnungsgemäß installiert und konfiguriert ist:
```
docker run hello-world
```
Wenn alles funktioniert hat, sollte es folgendermassen aussehen:
![Test Docker](../Screenshot/Test%20Docker.png)



Somit hat man Docker Desktop erfolgreich auf Windows installiert und WSL2 aktiviert.

Docker Architecktur
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

![Architecktur Docker](../Screenshot/Architecktur%20Docker.png)

## Docker Deamon ## 

* Erstellen, Ausführen und Überwachen der Container

* Bauen und Speichern von Images

## Docker Client ##

* Docker wird über die Kommandozeile (CLI) mittels des Docker Clients bedient

* Kommuniziert per HTTP REST mit dem Docker Daemon

## Images ##

* Images sind gebuildete Umgebungen welche als Container gestartet werden können

* Images sind nicht veränderbar, sondern können nur neu gebuildet werden.

## Container ## 

* Container sind die ausgeführten Images.

* Ein Image kann beliebig oft als Container ausgeführt werden.
  

## Docker Registry ## 

* In Docker Registries werden Images abgelegt und verteilt.

Dockerfile
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Ein Dockerfile ist ein Textdokument, das eine Abfolge von Anweisungen enthält, mit denen ein Docker-Image erstellt werden kann. Um ein Dockerfile zu erstellen, kann man zuerst ein neues Verzeichnis anlegen und darin eine Datei mit dem Namen "Dockerfile" erstellen.

Anschliessend kann das Image wie folgt gebuildet werden:
```
    $ docker build -t mysql .
```
Starten:
```
    $ docker run --rm -d --name mysql mysql
```
Funktionsfähigkeit überprüfen:
```
    $ docker exec -it mysql bash
```
Überprüfung im Container:
```
    $ ps -ef
    $ netstat -tulpen
```

Netzwerk-Anbindung
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Das wichtigste bei den Netzwerk Anbindungen ist, dass man weiss wie man Aussenstehenden Personen zugriff gebenkann. Das ganze funktioniert mit Ports. Dafür braucht man folgenden Behfel: -p oder -P.

Um eine Verbindung zu einem Docker-Container herzustellen, der eine Anwendung ausführt, die auf einen bestimmten Port hört, muss der Port an den Host oder das Netzwerk weitergeleitet werden. Dazu kann man im Dockerfile die Ports, die die Anwendung nutzt, über die Anweisung "EXPOSE" eintragen. Dies ermöglicht es, dass andere Container oder Anwendungen über das Netzwerk auf den Container zugreifen und mit der Anwendung kommunizieren können.

Volumes
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Bisher gingen alle Änderungen im Dateisystem verloren, wenn der Docker-Container gelöscht wurde. Um Daten auch über das Löschen des Containers hinaus zu erhalten, bietet Docker verschiedene Optionen:

* Daten auf dem Host ablegen: Man kann die Daten auf dem Hostsystem speichern, auf dem Docker läuft. Dadurch bleiben die Daten auch erhalten, wenn der Container gelöscht wird.

* Daten zwischen Containern teilen: Man kann Daten zwischen verschiedenen Containern teilen. Dadurch können mehrere Container auf dieselben Daten zugreifen und die Daten bleiben erhalten, auch wenn einer der Container gelöscht wird.

* Eigene Volumes erstellen: Man kann eigene Volumes erstellen, um Daten zu speichern. Diese Volumes sind unabhängig vom Container und können auch von anderen Containern genutzt werden. Dadurch bleiben die Daten erhalten, auch wenn der Container gelöscht wird.

Diese Optionen erlauben es, Daten auch über das Löschen eines Containers hinaus zu behalten und erleichtern die Verwaltung von Daten in Docker-Containern.

## Volume - Verzeichnis ##

Ein Volume ist ein spezielles Verzeichnis auf dem Hostsystem, in dem ein oder mehrere Docker-Container ihre Daten speichern können. Volumes bieten verschiedene nützliche Funktionen für die Verwaltung von persistenter oder gemeinsam genutzter Daten.

## Wie erstellt man ein neues Volume /data Verzeichnis? ##

Man muss den Folgenden Befehl einggeben, dass ein neues Docker Volume angelegt wird.

```
docker volume create data
```

Mit dem Folgenden Befehl kann man Überprüfen, ob der Befehl funktioniert hat. Somit werden alle verfügbaren Docker-Volumes aufgelistet.
```
docker volume ls
```

Damit man das Volume verwenden kann, muss man die folgenden Zeilen im Docker-Compose hinzufügen. Smoit wird "my-data" durch den gewünschten Namen des Volumes ersetzt.
```
volumes:
  my-data:
```

## Datencontainer ##

Wie starten man einen Container? Und wie kommen andere Personen darauf?

Um den Container zu starten, muss man den folgenden Befehl eingeben:
```
docker run
```
Um auf ein Container zugreifen zukönnen, muss man folgenden Behfel eingeben:
```
--volumes-from
```

## Named Volumes ##

Docker Volume ist seit Version 1.9 ein wichtiger Befehl, zur Verwaltung von Volumes auf einem Docker Host. Mit dem Befehl kann man ganz viele Sachen verwalten. Alle diese hier aufzuzählen macht aber keinen Sinn.


Image-Bereitstellung
===

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Es existieren zahlreiche Optionen, um Images bereitzustellen. Man kann sie durch das Erstellen von Dockerfiles erstellen, von einer Registry mit "docker pull" herunterladen oder mithilfe von "docker load" aus einer Archivdatei installieren.

## Namensgebung für Images ##

Images bestehen aus einem Namen und einer Version, wobei bei fehlender Angabe automatisch ":latest" hinzugefügt wird. Um Images bereitzustellen, sind präzise und beschreibende Namen und Tags von entscheidender Bedeutung. Die Namen und Tags werden entweder beim Bauen der Images oder durch den Befehl "docker tag" festgelegt.

Bei den Tag-Namen muss man auf ein Paar Sachen achten:

* Gross- und Kleinbuchstaben
* Zahlen
* Symbolen . und -
* nicht länger als 128 Zeichen
* erstes Zeichen kein . oder -

Bei der Entwicklung eines Workflows ist es äußerst wichtig, sinnvolle Namen für Repositories und Tags zu verwenden. Docker hat nur wenige Einschränkungen bezüglich der Namensgebung und erlaubt jederzeit die Erstellung oder Löschung von Namen. Es obliegt also dem Entwicklungsteam, ein angemessenes Namensschema zu entwerfen und anzuwenden

## Warnung vor dem latest-Tag ##

Wenn bei einem "docker run" oder "docker pull" Befehl kein spezifischer Tag angegeben wird, verwendet Docker standardmäßig das Image, das mit "latest" gekennzeichnet ist. Wenn kein solches Image vorhanden ist, wird eine Fehlermeldung ausgegeben.

# Docker Hub #

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)

Ein eigenes Images bereitzustellen ist am einfachsten, wenn man Dockers Hub verwendet.

Das Hub ist soweit kostenlos, man kann aber auch für Repositories von privaten Personen zahlen.

## Docker Hub einrichten ##

1. Zuerst muss man achten, dass man einen Docker Hub Account hat.
2. Image erstellen

```
docker tag mysql username/mysql
```

3. Um das Image hochzuladen, muss man den Befehl push mit verwenden.

```
docker push username/mysql
```

Dannach muss das Image noch beschrieben werden.

## Weitere Befehle ##

Nach einem Image kann man suchen mit folgendem Befehl:

```
docker search mysql
```
Um ein Image herunterzuladen, muss man den befehl pull verwenden:

```
docker pull ubuntu
```

# Export/Import von Container und Images #

Damit man Images zwischen zwei Hots hin und her verschieben kann, braucht man die Befehle docker export und docker import. Damit man Verzeichnisse hin und her kopieren kann, verwenden wir docker save und docker load.
```
docker export
```

```
docker import
```


Um seine eigenen Images sehen zu können, muss man folgenden Befehl ausführen:

```
/vagrant/mysql$ docker images
```
Wie kann ich mein Images wiederherstellen?

```
docker load
```


## TAR-Format ##

Das TAR-Format dient der Archivierung und Komprimierung von Dateien und Verzeichnissen und hat seinen Ursprung in der Sicherung von Daten auf Magnetbändern. Heutzutage wird es oft verwendet, um Dateien in einer einzelnen, komprimierten Datei für die Übertragung oder Speicherung zu archivieren. Um die Dateigröße weiter zu reduzieren, können TAR-Dateien mit verschiedenen Komprimierungsverfahren wie Gzip, bzip2 oder XZ komprimiert werden. Im Bereich von Docker-Images werden TAR-Dateien häufig als Archivdateien verwendet.

# Private Registry #

Es gibt verschiedene Möglichkeiten, Images neben dem Docker Hub bereitzustellen, aber die manuelle Erstellung oder der Export/Import von Images sind suboptimale Optionen. Das Erstellen von Images aus Dockerfiles auf jedem Host ist langsam und kann zu unterschiedlichen Images führen, während das Exportieren und Importieren von Images knifflig und fehleranfällig sein kann. Stattdessen wird empfohlen, eine andere Registry zu verwenden, die selbst gehostet oder von einem anderen Unternehmen betrieben wird.

[&uarr; nach oben](https://github.com/Silvan-Mattig/M300-Services/tree/main/30-Container#m300---30-container)




