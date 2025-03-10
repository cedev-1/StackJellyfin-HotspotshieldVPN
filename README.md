# StackJellyfin-HotspotshieldVPN

Jellyfin media stack on docker for hotspotshield VPN


To create your hown media server with this stack you have to :
- clone this repos on your server
- edit the .env file with your config
- add your .ovpn file
- edit your credentials on the file
- run the docker-compose.yml
- configure in app

---


```bash
clone the repot
bash folder.sh
cp .env.example .env
nano .env
docker-compose up -d

# to see qbittorrent password you have to look on the logs of the container
docker logs qbittorrent
```

## Accessible Ports

The following services are accessible via the specified ports. You can access their web interfaces using the paths indicated:

- **qBittorrent**:
  - Port 8080: Web Interface (`http://<your_server>:8080`)
  - Port 8999: TCP
  - Port 8999/udp: UDP

- **Sonarr**:
  - Port 8989 (`http://<your_server>:8989`)

- **Radarr**:
  - Port 7878 (`http://<your_server>:7878`)

- **Jellyseerr**:
  - Port 5055 (`http://<your_server>:5055`)

- **Jellyfin**:
  - Port 8096: Web Interface (`http://<your_server>:8096`)
  - Port 8920: SSL (`https://<your_server>:8920`)
  - Port 7359/udp
  - Port 1900/udp

- **Prowlarr**:
  - Port 9696 (`http://<your_server>:9696`)

- **FlareSolverr**:
  - Port 8191 (`http://<your_server>:8191`)

Replace `<your_server>` with the IP address or domain name of your server. These paths allow you to access the web interfaces of the various services configured in your Docker stack. Ensure these ports are not blocked by your firewall or Internet Service Provider.

---

FOLDER AND FILE ARCHITECTURE

```yml
/
├── docker-compose.yml
├── .env
├── config.ovpn
├── credentials
├── jellyfin
├── radarr
├── sonarr
├── configs/
│   ├── qbittorrent/
│   ├── prowlarr/
│   ├── sonarr/
│   ├── radarr/
│   ├── jellyfin/
│   ├── jellyseerr/
│
└── nas/
    ├── Downloads/
    ├── Series/
    └── Movies/
    └── Other/
```

---
### HELP

maybe it could be doesn't works because of ovpn config shure you have this lines

    auth-user-pass /etc/openvpn/credentials
    OR
    remote 8.8.8.8 822

sur of the path of the files or the remote add (not domaine)

