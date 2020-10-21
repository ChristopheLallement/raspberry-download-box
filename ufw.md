

/etc/ufw/applications.d/plexmediaserver

[plexmediaserver]
title=Plex Media Server (Standard)
description=The Plex Media Server
ports=32400/tcp|3005/tcp|5353/udp|8324/tcp|32410:32414/udp

[plexmediaserver-dlna]
title=Plex Media Server (DLNA)
description=The Plex Media Server (additional DLNA capability only)
ports=1900/udp|32469/tcp

[plexmediaserver-all]
title=Plex Media Server (Standard + DLNA)
description=The Plex Media Server (with additional DLNA capability)
ports=32400/tcp|3005/tcp|5353/udp|8324/tcp|32410:32414/udp|1900/udp|32469/tcp

Once you have defined your application file tell ufw to reload the application definitions with:

ufw app update plexmediaserver

Use it with:

ufw allow plexmediaserver-all



```
# for access to the Plex Media Server
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32400 proto tcp

#UDP: 1900 (for access to the Plex DLNA Server)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 1900 proto udp

#TCP: 32469 (for access to the Plex DLNA Server)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32469 proto tcp

#TCP: 3005 (for controlling Plex Home Theater via Plex Companion)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 3005 proto udp

#UDP: 5353 (for older Bonjour/Avahi network discovery)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 5353 proto udp

#TCP: 8324 (for controlling Plex for Roku via Plex Companion)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 8324 proto tcp

#UDP: 32410, 32412, 32413, 32414 (for current GDM network discovery)
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32410 proto udp
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32412 proto udp
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32413 proto udp
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 32414 proto UDP




#deluge
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 8112/tcp
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 58846/tcp
ufw allow from 192.168.1.0/24 to 192.168.1.82 port 58946

 
 ```
