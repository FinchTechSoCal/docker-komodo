# docker-komodo
Komodo is a web app to provide structure for managing your servers, builds, deployments, and automated procedures.

Use:

1. Copy mongo.compose.yaml and compose.env to your host:
```bash
rm -fr ~/appdata/docker_files/komodo
git clone https://github.com/FinchTechSoCal/docker-komodo.git ~/appdata/docker_files/komodo
```

2. Edit the variables in komodo/compose.env or use this command:
```bash
VLOCVOL1="/path/to/appdata/"
VKOMODO_DB_USERNAME="admin"
VKOMODO_DB_PASSWORD="admin"
VKOMODO_PASSKEY="a_random_passkey"
VKOMODO_WEBHOOK_SECRET="a_random_secret"
VKOMODO_JWT_SECRET="a_random_jwt_secret"

sed -i 's|LOCVOL1=/path/to/appdata/|LOCVOL1='$VLOCVOL1'|gI' appdata/docker_files/komodo/compose.env
sed -i 's/KOMODO_DB_USERNAME=admin/KOMODO_DB_USERNAME='$VKOMODO_DB_USERNAME'/gI' appdata/docker_files/komodo/compose.env
sed -i 's/KOMODO_DB_PASSWORD=admin/KOMODO_DB_PASSWORD='$VKOMODO_DB_PASSWORD'/gI' appdata/docker_files/komodo/compose.env
sed -i 's/KOMODO_PASSKEY=a_random_passkey/KOMODO_PASSKEY='$VKOMODO_PASSKEY'/gI' appdata/docker_files/komodo/compose.env
sed -i 's/KOMODO_WEBHOOK_SECRET=a_random_secret/KOMODO_WEBHOOK_SECRET='$VKOMODO_WEBHOOK_SECRET'/gI' appdata/docker_files/komodo/compose.env
sed -i 's/KOMODO_JWT_SECRET=a_random_jwt_secret/KOMODO_JWT_SECRET='$VKOMODO_JWT_SECRET'/gI' appdata/docker_files/komodo/compose.env

```

3. Deploy 1 of the 2 below:

Full (core, periphery/agent, db):
```bash
docker compose -p komodo -f ~/appdata/docker_files/komodo/mongo.compose.yaml --env-file ~/appdata/docker_files/komodo/compose.env up -d
```

Periphery (agent):
```bash
docker compose -p komodo -f ~/appdata/docker_files/komodo/periphery.compose.yaml --env-file ~/appdata/docker_files/komodo/compose.env up -d
```