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

Give permissions to the grafana and prometheus data folders.

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

Output

```sh
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS          PORTS                                       NAMES
1c06e22c1dc9   prom/blackbox-exporter         "/bin/blackbox_expor…"   22 minutes ago   Up 19 minutes   0.0.0.0:9115->9115/tcp, :::9115->9115/tcp   blackbox
3bce202e1c30   prom/prometheus:v2.32.1        "/bin/prometheus --c…"   22 minutes ago   Up 19 minutes   0.0.0.0:9090->9090/tcp, :::9090->9090/tcp   prometheus
7c60638f7229   grafana/grafana:latest         "/run.sh"                22 minutes ago   Up 19 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   grafana
52e78a7f85fa   prom/node-exporter:v1.3.1      "/bin/node_exporter …"   22 minutes ago   Up 19 minutes   0.0.0.0:9100->9100/tcp, :::9100->9100/tcp   nodeexporter
bf168cd51bda   benjojo/alertmanager-discord   "/go/bin/alertmanage…"   22 minutes ago   Up 19 minutes   9094/tcp                                    discord-alerts
c9e16fffbfe3   prom/alertmanager:v0.21.0      "/bin/alertmanager -…"   22 minutes ago   Up 19 minutes   0.0.0.0:9093->9093/tcp, :::9093->9093/tcp   alertmanager
```




The dashboards and discord image come from the community directly. Credit to them.


I made some adjustments to my environment.