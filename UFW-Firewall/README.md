sudo apt install ufw -y

sudo ufw allow 80/tcp

sudo ufw allow from 10.0.2.2 to any port 22

ufw --force enable