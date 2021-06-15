Zkontrolovat zda bezi docker sluzba
systemctl status docker
systemctl enable docker
systemctl start docker

Spustit docker-compose v teto slozce
docker-compose up

Pripadne jako deamon
docker-compose up -d

Webserver bezi na
localhost:8080
(Pri prvnim spusteni chvili trva inicializace mysql, proto muze wordpress hlasit chybu databaze, staci po cca 1-2min F5)

Zobrazeni spustenych kontejneru
docker ps

Spusteni shell v kontejneru
docker run -it nazev_kontejneru bash

Vypnuti vsech kontejneru
docker-compose down
