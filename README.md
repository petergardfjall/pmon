# About
A self-contained monitoring environment for processes running on `localhost`
that is quick to bring up and easy to dispose.

It runs [process-exporter](https://github.com/ncabatoff/process-exporter) to
collect fine-grained metrics about processes running on the host,
[prometheus](https://prometheus.io/) to scrape those metrics, and
[grafana](https://github.com/grafana/grafana) to visualize them (with a few
bundled dashboards).

Data is not persistent outside the lifetime of the containers (between `stack
up` and `stack down`).



## Bring up

    ./stack up
    ./stack logs [component]

Configuration can be set via environment variables:
- `PROMETHEUS_PORT`: host port to publish prometheus api port on. Default:
  `9090`.
- `GRAFANA_PORT`: host port to publish Grafan UI on. Default: `3000`.
- `GRAFANA_PASSWORD`: Grafana admin password. Default: `password`.
- `PROCESS_EXPORTER_PORT`: host port where
  [process-exporter](https://github.com/ncabatoff/process-exporter) publishes
  its `/metrics` endpoint. Default: `9236`.

## Use
Navigate your web browser to the Grafana instance at
`http://localhost:${GRAFANA_PORT}`.

## Tear down
Remove all traces of the monitoring stack.

    ./stack down
