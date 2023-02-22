# Monitoring and charting desing and alerts

## still in development

### Requirements:

* docker compose
* docker

- This project initially started with the intention of playing with grafana and prometheus. But I ended up adding more stuff and it's really fun to play with. I'm still validating with a Kubernetes cluster, there are already some settings.

- I'm currently using grafana to create dashboards, getting metrics with Prometheus, alerting everything with Alertmanager and notifying discord.

- Initially I was only monitoring my linux and my docker host, but I added website monitoring using the Blackbox exporter.

To download this project, type the command bellow.

```sh
git clone https://github.com/tallesemmanuel/playground-grafana-prometheus.git
```

Create the directories used by grafana and prometheus for storage.

```sh
mkdir grafana_data
```

and

```sh
mkdir prometheus_data
```

Copying and using a template from .env-example

```sh
cp .env-example .env
```

Edit the .env and add your variables.

```sh
cat .env
```

output

```sh
ADMIN_PASSWORD= 
ADMIN_USER = 
GRAFANA_VERSION = 
VAR_DISCORD_WEBHOOK =
```

After adding the variables, run docker compose.

```sh
docker compose up -d
```
