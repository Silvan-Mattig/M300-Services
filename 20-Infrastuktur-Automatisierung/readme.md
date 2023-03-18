M300 - 20 Infrastruktur-Automatisierung
===

Vagrant
===

Packer
===

AWS
===
Verbindung mit AWS in Vagrant

Vagrant kann mit verschiedenen Cloud Providern verbunden werden, einschließlich AWS von Amazon. Um AWS mit Vagrant zu nutzen, müssen Sie das vagrant-aws Plugin installieren und die dummy Box lokal hinzufügen:

ruby
```
vagrant plugin install vagrant-aws
```

```
$ vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```
### **AWS vorbereiten**

Folgen Sie diesen Schritten, um AWS für Vagrant vorzubereiten:

1. Öffnen Sie die AWS-Website und erstellen Sie einen Amazon-Stammbenutzer, falls noch nicht vorhanden.

    
2. Ändern Sie den Rechenzentrum-Standort auf Frankfurt, um die schnellste Verbindung zu erhalten. Beachten Sie jedoch, dass sich dieser je nach Bedarf ändern kann.


3. Erstellen Sie einen AWS-Benutzer, auf den Vagrant auf "EC2" zugreifen kann.

4. Klicken Sie oben rechts auf Ihren Benutzernamen und dann auf "Sicherheitsanmeldeinformationen".

5. Klicken Sie auf "Benutzer" und erstellen Sie einen neuen Benutzer mit dem Namen "vagrant".

6. Weisen Sie diesem Benutzer die "Berechtigungsrichtlinie" "AmazonEC2FullAccess" zu.
    
7. Überprüfen Sie erneut, ob "Frankfurt" als Rechenzentrum ausgewählt ist.
        
8. Erstellen Sie eine Sicherheitsgruppe, die Datenverkehr über Port 22 und Port 80 an die VM zulässt.
        
9.  Erstellen Sie ein Schlüsselpaar und speichern Sie die .pem-Datei im Hauptverzeichnis des Vagrant-Projekts.
Wählen Sie "RSA" und ".pem" und laden Sie die Datei mit dem privaten Schlüssel herunter.
Achten Sie darauf, den Schlüssel nicht auf Github hochzuladen.

### **Konfiguration des Vagrantfiles**

Bearbeiten Sie das Vagrantfile und geben Sie die Zugriffsschlüssel, das .pem-Zertifikat und weitere Angaben zum Rechenzentrum-Standort und zum Instanztyp an:

ruby

```
Vagrant.configure("2") do |config|
    config.vm.box = "dummy"
  
    config.vm.provider :aws do |aws, override|
      aws.access_key_id = ""
      aws.secret_access_key = ""
      #aws.session_token = "SESSION TOKEN"
      aws.keypair_name = "vagrant"
      aws.region = "eu-central-1"
      aws.ami = "ami-0d1ddd83282187d18"
      aws.instance_type = "t2.micro"
      aws.security_groups = "vagrant"
      override.ssh.username = "ubuntu"
      override.ssh.private_key_path = "vagrant.pem"
    end
    config.vm.synced_folder "html/", "/var/www/html"
    config.vm.provision "shell", path: "scripts/apache.sh"
  end
```


LB2
===