M300 - 30 Container
===

Inhaltsverzeichnis
===

Container
===
Ein Container ist ein Konzept der Informatik, das hilfreich ist, um Anwendungen in einer Umgebung auszuführen, die isoliert und unabhängig von anderen Anwendungen und dem Betriebssystem des Computers ist.

Ein Vorteil von Containern ist, dass sie portabel sind und auf verschiedenen Betriebssystemen und Servern ausgeführt werden können, solange sie die Container-Software unterstützen. Durch die Verwendung von Containern können Anwendungen schneller bereitgestellt und skaliert werden, da sie unabhängig von der zugrunde liegenden Infrastruktur sind und somit schneller und einfacher bereitgestellt werden können.

Docker
===

### Wichtige Befehle für Docker ###

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

# Anleitung zur Installation von Docker Desktop auf Windows und Aktivierung von WSL2

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

Volumes
===

Image-Bereitstellung
===

LB3
===

