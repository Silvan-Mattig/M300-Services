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

Den Git Client braucht man um Dateien auf Github Hoch und runter zuladen. [Git Download](https://git-scm.com/downloads)
