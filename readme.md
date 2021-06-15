# Disclaimer
Tento projekt slouží pouze k názorné ukázce fungování docker a docker-compose, konfigurace není ve všech směrech optimální. Projekt není určen pro produkční nasazení.

# Předpoklady
Aktualizovaný systém Debian 10 s SSH serverem.  

# Instalace Dockeru
Instalace potřebných závislostí:  
`
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release sudo 
`

Přidání klíče docker repozitáře do systému  
`curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg  
`

Přidání repozitáře do systému (amd64)  
`echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
`

Instalace dockeru a docker compose
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo apt-get install docker-compose
```
# Kontrola a nastavení oprávnění
Kontrola, povolení a zapnutí dockeru
```
sudo systemctl enable docker
sudo systemctl start docker
sudo systemctl status docker
```

Přidání uživatele do skupiny docker  
`
sudo usermod -a -G docker uzivatel
`

# Stažení repozitáře
Instalace git balíčku  
`sudo apt-get install git`

Klonování git repozitáře a přesun do jeho hlavní složky  
```
git clone https://github.com/eretl/docker-wordpress.git
cd docker-wordpress
```

# Spuštění kontejnerů
V hlavní složce naklonovaného projektu spustit docker-compose  
`docker-compose up`  
případně jako deamon  
`docker-compose up -d`

**První spouštění trvá déle, inicializují se jednotlivé kontejnéry, webová stránka s konfigurací wordpressu může ukázat chybu připojení databáze. Proto počkejte 1-2min na dokončení a aktualizujte stránku.**

# Zobrazení webové stránky
Webová stránka je dostupná na
`http://localhost:8080`

# Popis složek a souborů v projektu
## conf
### nginx.conf
Konfigurace nginxu, důležité je nastavení php, které je nasměrováno na wordpress kontejner
## logs
### nginx
Log soubory z nginx kontejneru
## docker-compose.yml
Hlavní soubor projektu, který určuje strukturu docker kontejnerů.
Detailnejší popis přímo v něm.

# Ostatní příkazy dockeru
Zobrazení běžících kontejnerů  
`docker ps`

Spuštění shell v kontejneru  
`docker run -it nazev_kontejneru bash`

Zobrazení spuštěných procesů v kontejneru  
`docker top nazev_kontejneru`

Restart/zastavení/spuštění/zabití kontejneru  
```
docker restart nazev_kontejneru
docker stop nazev_kontejneru
docker start nazev_kontejneru
docker kill nazev_kontejneru
```

Vypnutí kontejnerů z docker compose (je nutné spustit ve složce se souborem docker-compose.yml)  
`docker-compose down`

