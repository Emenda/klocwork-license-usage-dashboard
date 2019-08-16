# Klocwork License Usage Dashboard
A Grafana-based dashboard for monitoring Klocwork license usage. Prometheus is used as the data provider. FlexLM Exporter periodically runs lmstat and sends data to Prometheus.

## Requirements
- NOTE: The FLexLM Exporter currently builds only on Linux. Windows builds are a WIP. You will need to modify the Makefile to build in Windows.
- Go - https://golang.org/
- FlexLM Exporter (Emenda Fork) - https://github.com/Emenda/flexlm_exporter 
- Prometheus - https://prometheus.io/
- Grafana - https://grafana.com/

## Installation
* Install Go (example instructions: https://golang.org/doc/install )
* Get and build the FlexLM Exporter (follow instructions: https://github.com/Emenda/flexlm_exporter/blob/master/README.md )
* Install Prometheus (example instructions: https://devopscube.com/install-configure-prometheus-linux/ )
* Install Grafana (example instructions: https://grafana.com/docs/installation/rpm/ )

## Configuration
Execute the FlexLM Exporter, providing the path to Klocwork's lmstat binary:
```
nohup ./flexlm_exporter --path.lmutil="/klocwork/server18.3/3rdparty/bin/lmstat" & 
```
Configure Prometheus to scrap the resulting FlexLM Exporter metrics page. See prometheus.yml for an example configuration.

Add Prometheus as a data source in Grafana. Import the Klocwork license monitor dashboard (klocwork-license-usage.json).