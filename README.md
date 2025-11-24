# docker-komodo
Komodo is a web app to provide structure for managing your servers, builds, deployments, and automated procedures.

Use:

1. Copy mongo.compose.yaml and compose.env to your host:
```bash
rm -fr ~/appdata/docker_files/komodo
git clone https://github.com/FinchTechSoCal/docker-komodo.git ~/appdata/docker_files/komodo
```

2. Edit the variables in komodo/compose.env.

3. Deploy 1 of the 2 below:

Full (core, periphery/agent, db):
```bash
docker compose -p komodo -f ~/appdata/docker_files/komodo/mongo.compose.yaml --env-file ~/appdata/docker_files/komodo/compose.env up -d
```

Periphery (agent):
```bash
docker compose -p komodo -f ~/appdata/docker_files/komodo/periphery.compose.yaml --env-file ~/appdata/docker_files/komodo/compose.env up -d
```