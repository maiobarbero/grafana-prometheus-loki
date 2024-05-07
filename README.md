# Stack Monitoring Application
This application uses Grafana, Loki, Promtail, Prometheus, and Node Exporter to monitor logs and server performance. Grafana provides a user-friendly dashboard, Loki aggregates logs, Promtail scrapes logs, Prometheus collects metrics, and Node Exporter exposes host metrics.

## Components
- **Grafana**: An open-source platform for monitoring and observability. It allows you to query, visualize, alert on, and understand your metrics.
- **Loki**: A horizontally-scalable, highly-available, multi-tenant log aggregation system inspired by Prometheus.
- **Promtail**: An agent which ships the contents of local logs to a private Loki instance or Grafana Cloud.
- **Prometheus**: An open-source systems monitoring and alerting toolkit.
- **Node Exporter**: A Prometheus exporter for hardware and OS metrics with pluggable metric collectors.

## Running the Application
First of all edit `config/prometheus/prometheus.yml` and set the right ip address and eventually the right labels.
To run the application, use the following command: `USER_ID=$(id -u) docker compose up -d`
This command uses Docker Compose to start the application. It sets the USER_ID environment variable to your user ID, which is obtained by running id -u.
For the first access to your Grafana dashboard use *user=admin* and *password=admin*.


## Checking the Status of Services
You can check the status of the services by visiting the following URLs:

- `localhost:3100/metrics`: This page shows various metrics related to the application.
- `localhost:3100/ready`: This page indicates whether the application is ready. If it doesn't say "ready", try refreshing the page.
- `localhost:9090`: This page shows the Prometheus dashboard where you can query your metrics.
- `localhost:9100/metrics`: This page shows the metrics exposed by the Node Exporter.
- `localhost:3000`: Access Grafana

*Please note that these URLs assume that the application is running on your local machine. If you're running the application on a different machine, replace localhost with the IP address or hostname of that machine.*

## Prometheus Configuration
The Prometheus configuration is located in ./config/prometheus/prometheus.yml. This file tells Prometheus what services to scrape metrics from. By default, it is configured to scrape metrics from the Node Exporter.

## Node Exporter
The Node Exporter is a tool that collects information about the system including CPU, disk I/O, memory, network, and others. It exposes this information in a format that Prometheus can use.

## Create a new Dashboard
1) Create two new data sources. One for Prometheus with url `http://prometheus:9100` and the other for Loki with url `http://loki:3100`
2) Import a new dashboard for Prometheus monitoring like the one with id **1860** or create a new one.
3) Import a new dashboard for Loki monitoring like the one with id **13639** or create a new one
