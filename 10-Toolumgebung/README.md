# M300-Services

## GitHub Account
### SSH-Key erstellen
Folgende Befehle im Bash ausführen:
1. Account E-Mail von Github eingeben
    ```
    ssh-keygen -t rsa -b 4096 -C "beispiel@beispiel.com"
    ```
2. SSH-Key wird erstellt
    ```
    Generating public/private rsa key pair.
    ```
3. Namensabfrage für den Schlüssel
   ```
   Enter a file in which to save the key (~/.ssh/id_rsa): 
   ```
4. Passwort setzten (Im ideal Fall hinterlegt man das gerade beim SSH-Agent)
    ```
    Enter passphrase (empty for no passphrase): [Passwort]
    Enter same passphrase again: [Passwort wiederholen]
    ``` 

### SSH-Key dem SSH-Agent hinzufügen

1. Man muss den Key bei seinem Account unter den Einstellungen hinterlegen:

![GitHub Konto SSH Keys](Screenshot/Screenshot%202023-03-13%20143259.png)

## Git Client
### Client installieren

Den Git Client braucht man um Dateien auf Github Hoch und runter zuladen. [Git Download](https://git-scm.com/downloads)

### Client konfigurieren
1. Zunächst muss man zwei Befehle im Bash eingeben.

```
  git config --global user.name "<username>"
  
  git config --global user.email "<e-mail>"
```
### Repository klonen
1. Als nächstes wollen wir ein Repository klonen, dies machen wir im Bash.

```
git clone https://gitlab.com/ch-tbz-it/Stud/m300/
```
2. Damit das funktioniert, muss man ins richtige Verzeichnis wechseln.
```
cd M300
```
3. Damit das Repository aktualisiert wird, muss man zunächst den Folgenden Befehl eingeben.

```
git pull
```

4. Um den Status anzuzeigen, kann man den folgenden Befehl eingeben.

```
git status
```
### Repository herunterladen & aktualisieren

1. Zunächst wollen wir ein Ordner im gewünschten Verzeichnis wählen.

```
cd Wohin/auch/immer

mkdir MeinLokalesRepository
```
2. Repository mit SSH klonen

```
git clone git@github.com:<Ihr Name>/my_M300.git
```

3.Jetzt machen wir wieder das gleiche wie bei der letzten Aufgabe. Somit aktualisiert und prüft man den Status.

```
git pull
```

### Repository hochladen

1. Zum Verzeichnis wechseln

```
cd Pfad/zu/meinem/Repository
```
2. Die Daten hinzufügen, damit es beim Upload funktioniert

```
git add -A .
```
3. Die Bestätigung geben.

```
git commit -m "Mein Kommentar"
```
4. Upload pushen

```
git push
```

## VirtualBox

### Software herunterladen & installieren

Damit wir fortfahren können, müssen wir VirtualBox herunterladen. 
[VirtualBox download](https://www.virtualbox.org/)

### ISO-Datei herunterladen


Damit unsere VM später funktioniert, brauchen wir logischerweise eine ISO, am besten verwendet man gerade diese: [Ubuntu-ISO](https://ubuntu.com/#download)

Damit die ISO-Datei Reproduzierbar ist, muss man es im gewünschten Verzeichnis ablegen. Hierzu muss man achten, dass es auf dem lokalen PC abgespeichert ist.

### VM erstellen

Die Schwirigkeit beim erstellen der VM lag bei der Dateigrösse... Ich hatte 10GB laut Anleitung genommen, das hat aber leider nicht funktioniert, da die VM immer wieder abstürzte... Also habe ich mich dazu entschieden 25GB zu nehmen, dannch hat es funktioniert. Wichtig ist ebenfalls dass man das richtige Medium ausgewählt hat. Die ISO Datei muss logischer Weise vorhanden sein.

### VM einrichten

Wichtig ist, dass die VM läuft, dannch muss man sich beim Bash anmelden. Paketliste muss nei eingelesen werden und die Pakete Aktualisiert. Dafür braucht man die Befehle:

```
sudo apt-get update   

#Paketlisten des Paketmanagement-Systems "APT" neu einlesen

sudo apt-get upgrade   

#Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

sudo reboot           #System-Neustart durchführen
```

### Synaptic installieren

1. Synaptic ist zur Verwaltung von Debian-Paketen gemacht, kann aber auch mit RPM-Paketen umgehen. Darum müssen wir das herunterladen.
```
 sudo apt-get install synaptic
```
2. Synaptic öffnen und apache installieren

```
sudo reboot
```

Damit wir testen können, ob das ganze funktoniert hat, muss man prüfen, ob der Standard-Content des Webservers localhost erreichbar ist.


## Vagrant

Was ist Vagrant eigentlich?

Ein Vagrant-file ist für die Automatisierung oder für die Reproduzierbarkeit. Somit kann man mit einer einfachen ausführung Virtuelle Maschienen erstellen lassen. Man kann nicht nur Virtuelle Maschienen erstellen sondern auch verwalten.


### Software herunterladen & installieren

1. Vagrant kann man unter dieser Internetseite herunterladen [Vagrant-Download](https://www.vagrantup.com/)
2. Für die Installation muss man nichts beachten. Wenn man den Download abgeschlossen hat, kann man mit dem Erstellen der Virtuellen Maschienen anfangen.

### Virtuelle Maschine erstellen

1. Damit wir ein sogennantes Vagrant-file erstellen können, müssen wir in ein gewünschtes Verzeichnis wechseln und dort einen Ordner erstellen. Nach dem erstellen des Ordners muss man auch gerade dort hin Navigieren.

```
cd Wohin/auch/immer
mkdir MeineVagrantVM
cd MeineVagrantVM
```

2. Vagrantfile erzeugen, VM erstellen und entsprechend starten:

```
vagrant init ubuntu/xenial64        
vagrant up --provider virtualbox    
```




