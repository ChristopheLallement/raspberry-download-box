# Rapsberry dowload box

| Service     | Images                    | webUI                            |
|-------------|---------------------------|----------------------------------|
| nordvpn     | bubuntux/nordvpn          |                                  |
| deluge      | linuxserver/deluge        | http://{ip}:8112                 |
| jackett     | linuxserver/jackett       | http://{ip}:9117                 |
| sonarr      |                           |                                  |
| radarr      | linuxserver/sonarr        | http://{ip}:8989                 |
| bazarr      | linuxserver/bazarr        | http://{ip}:7878                 |
| plex        | linuxserver/plex          | http://{ip}:32400                |
| rpi-monitor | michaelmiklis/rpi-monitor | http://{ip}:8888                 |
| pihole      | linuxserver/pihole        | http://{ip}:2280/admin/index.php |


## Configuring

###  Environment variables
Edit .env with :
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


## Starting services

```
docker-compose up -d
```

## Stopping services
```
docker-compose down
```

## Upgrading services
```
docker-compose pull
docker-compose up -d --remove-orphans
docker image prune
```
