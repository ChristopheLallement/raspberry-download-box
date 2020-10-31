# Rapsberry download box powered by Docker

| Service     | Images                    | webUI                            |
|-------------|---------------------------|----------------------------------|
| nordvpn     | bubuntux/nordvpn          |                                  |
| deluge      | linuxserver/deluge        | http://{ip}:8112                 |
| jellyfin    | jellyfin/jellyfin         | http://{ip}:8096                 |
| ubooquity   | linuxserver/ubooquity     | http://{ip}:2203/ubooquity/admin |
| ubooquity   | linuxserver/ubooquity     | http://{ip}:2202/ubooquity |




# Install Docker and docker compose for 32-bit raspberry pi

For raspberry pi arm32, should Install using the convenience script. 
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

For 64 bit raspberry  see doker doc.

## Add permission to Pi User to run Docker Commands
```
sudo usermod -aG docker pi
```


## update
```
sudo apt-get update
sudo apt-get upgrade
```


## Test Docker installation
```
docker run hello-world
```

## Docker-compose 

### Install proper dependencies
```
sudo apt-get install libffi-dev libssl-dev
sudo apt-get install -y python3 python3-pip
sudo apt-get remove python-configparser
```

### Install Docker Compose
```
sudo pip3 install docker-compose 
```

## Configure downloadbox

Edit `.env` 
```
TZ= time zone value (for instance Europe/Paris)
PUID= user PUID 
PGID= user PGID
CONFIG= path where to store service configurations
DOWNLOADS= landing folder for torrent client (deluge)
MOVIES= movies library for plex
TV= tv library for plex
NORDVPN_USER= nordvpn user name
NORDVPN_PASS= nordvpn password
PIHOLE_ADMIN_PASS= pihole admin password
```

## Starting download-box
```
docker-compose up -d
```

## Stopping download-box
```
docker-compose down
```

## Upgrading 
```
docker-compose pull && docker-compose up -d --remove-orphans  && docker image prune
```

## Firewall
```
sudo ufw enable
sudo ufw status verbose
sudo ufw status numbered

#deluge
sudo ufw allow from 192.168.1.0/24 to 192.168.1.82 port 8112/tcp

#jellyfin
sudo ufw allow from 192.168.1.0/24 to 192.168.1.82 port 8096/tcp  # HTTP traffic
sudo ufw allow from 192.168.1.0/24 to 192.168.1.82 port 1900/udp  # for service auto-discovery/DLNA
sudo ufw allow from 192.168.1.0/24 to 192.168.1.82 port 7359/udp  # for service auto-discovery/DLNA
```