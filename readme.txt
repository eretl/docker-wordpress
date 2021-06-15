Zkontrolovat zda bezi docker sluzba
systemctl status docker
systemctl enable docker
systemctl start docker

Spustit docker-compose v teto slozce
docker-compose up

Pripadne jako deamon
docker-compose up -d

Zobrazeni spustenych kontejneru
docker ps

Spusteni shell v kontejneru
docker run -it nazev_kontejneru bash

Vypnuti vsech kontejneru
docker-compose down
