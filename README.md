# Mini ISP NOC Monitoring & Observability System
A lab-scale ISP Network Operations Center (NOC) monitoring and observability system designed to simulate real-world network monitoring, service health monitoring, centralized logging, dashboards, and alerting.

## Overview
This project demonstrates how an ISP-style network can be monitored from a centralized NOC using open-source monitoring and observability tools.
The network topology was designed and simulated using **Cisco Packet Tracer**, while monitoring and observability components were deployed on an **Ubuntu Linux VM**.

The system provides visibility into:

* Network and host resource utilization
* Service availability and reachability
* Network traffic
* CPU and memory usage
* Disk utilization
* System uptime
* Network latency
* DNS availability
* HTTP response time
* Centralized logs
* Monitoring alerts

## Architecture

                    ┌──────────────────────────────┐
                    │     Cisco Packet Tracer      │
                    │        ISP Topology          │
                    │                              │
                    │   Routers / Switches /       │
                    │      Network Nodes           │
                    └──────────────┬───────────────┘
                                   │
                     Network Reachability /
                       Service Monitoring
                                   │
                                   ▼
                    ┌──────────────────────────────┐
                    │        Ubuntu Linux VM       │
                    │                              │
                    │  ┌────────────────────────┐  │
                    │  │ Prometheus             │  │
                    │  │ Node Exporter          │  │
                    │  │ Blackbox Exporter      │  │
                    │  └────────────────────────┘  │
                    │                              │
                    │  ┌────────────────────────┐  │
                    │  │ Loki                   │  │
                    │  │ Grafana Alloy          │  │
                    │  └────────────────────────┘  │
                    │                              │
                    │              │               │
                    │              ▼               │
                    │       ┌─────────────┐        │
                    │       │   Grafana   │        │
                    │       └─────────────┘        │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                    ┌──────────────────────────────┐
                    │       NOC Dashboards         │
                    │                              │
                    │  • NOC Command Center        │
                    │  • Infrastructure Monitoring │
                    │  • Internet & Services       │
                    │  • Centralized Logs          │
                    └──────────────────────────────┘


## Technologies Used

### Networking
* Cisco Packet Tracer
* IP networking
* Routing and switching
* ISP-style network topology
* Network reachability testing

### Monitoring & Observability
* Prometheus
* Node Exporter
* Blackbox Exporter
* Grafana
* Loki
* Grafana Alloy
* Alerting rules

### Operating System
* Ubuntu Linux

### Version Control
* Git
* GitHub

## Monitoring Stack

### Prometheus
Prometheus is used as the primary metrics collection and monitoring system.
The configuration includes monitoring and alerting rules for infrastructure and service-level metrics.

### Node Exporter
Node Exporter provides system-level metrics such as:

* CPU utilization
* Memory utilization
* Disk utilization
* Network traffic
* System uptime
* Load average

### Blackbox Exporter
Blackbox Exporter is used for external service and endpoint monitoring.

The project monitors:

* Network reachability
* ICMP connectivity
* DNS availability
* HTTP availability
* Response latency

### Grafana
Grafana provides centralized NOC dashboards for visualizing monitoring data.

The project includes dashboards for:

1. **NOC Monitoring**
   * CPU usage
   * Memory usage
   * Disk usage
   * Network traffic
   * System uptime
   * Load average

2. **Internet & Service Monitoring**
   * Reachability
   * Latency
   * DNS response
   * HTTP response time

3. **Logs Dashboard**
   * Centralized log visualization

4. **NOC Command Center**
   * High-level operational monitoring view

### Loki & Grafana Alloy

Loki is used for centralized log storage and querying.

Grafana Alloy is used as part of the log collection and observability pipeline.

## Repository Structure

```text
mini-isp-noc/
│
├── alloy/
│   └── config.alloy
│
├── blackbox/
│   └── blackbox.yml
│
├── grafana/
│   ├── internet-service-monitoring-dashboard.json
│   ├── logs-dashboard.json
│   ├── noc-command-center-dashboard.json
│   └── noc-monitoring-dashboard.json
│
├── loki/
│   └── loki-config.yml
│
├── prometheus/
│   ├── prometheus.yml
│   └── alerts.yml
│
├── packet-tracer/
│   └── mini-isp-noc.pkt
│
├── screenshots/
│   ├── noc-command-center.png
│   ├── noc-monitoring.png
│   ├── internet-service-monitoring.png
│   └── logs-dashboard.png
│
├── docs/
│
├── .gitignore
└── README.md
```

## Key NOC Monitoring Metrics

| Category     | Metrics                             |
| ------------ | ----------------------------------- |
| CPU          | CPU utilization                     |
| Memory       | RAM utilization                     |
| Disk         | Disk usage                          |
| Network      | Receive and outbound traffic        |
| Availability | Reachability and uptime             |
| Latency      | Network response latency            |
| DNS          | DNS response/availability           |
| HTTP         | HTTP response time                  |
| Logs         | Centralized application/system logs |
| Alerts       | Threshold-based monitoring alerts   |

## Project Workflow

```text
Network / Services
        │
        ▼
Metrics & Availability Checks
        │
        ├── Node Exporter
        └── Blackbox Exporter
                │
                ▼
           Prometheus
                │
                ▼
             Grafana
                │
        ┌───────┼────────┐
        ▼       ▼        ▼
      NOC    Services    Logs
   Dashboard Dashboard Dashboard
```

## Screenshots

### NOC Command Center

![NOC Command Center - 01](screenshots/NOC%20Dashboard%20-%2001.png)

![NOC Command Center - 02](screenshots/NOC%20Dashboard%20-02.png)

![NOC Command Center - 03](screenshots/NOC%20Dashboard%20-03.png)

### NOC Monitoring Dashboard

![NOC Monitoring - 01](screenshots/NOC%20Monitoring%20-01.png)

![NOC Monitoring - 02](screenshots/NOC%20Monitoring-02.png)

### Internet & Service Monitoring

![Internet and Service Monitoring](screenshots/Internet%20and%20Service%20Monitoring.png)

### Logs Dashboard

![Logs Dashboard](screenshots/Logs%20Dashboard.png)


## How to Explore the Project

The repository contains the configuration files required to understand and reproduce the monitoring stack.

Start with:

1. `packet-tracer/` — network topology
2. `prometheus/` — metrics collection and alerting configuration
3. `blackbox/` — endpoint and service monitoring
4. `grafana/` — dashboard definitions
5. `loki/` — log storage configuration
6. `alloy/` — observability/log collection configuration
7. `screenshots/` — visual results

## Project Objectives

The main objectives of this project are to demonstrate:

* Practical network monitoring
* ISP/NOC operational concepts
* Infrastructure observability
* Service availability monitoring
* Centralized logging
* Dashboard development
* Monitoring alert configuration
* Linux-based monitoring infrastructure
* Integration of multiple observability components

## How to Run

This project can be reproduced using an Ubuntu Linux VM together with Cisco Packet Tracer.

### 1. Network Topology

Open the Packet Tracer project located in:

`packet-tracer/`

Start the ISP topology and verify connectivity between the configured network nodes.

### 2. Prometheus

Prometheus is configured using:

`prometheus/prometheus.yml`

Alerting rules are defined in:

`prometheus/alerts.yml`

Start Prometheus and verify that the configured targets are reachable.

### 3. Node Exporter

Node Exporter provides Linux system metrics including:

- CPU utilization
- Memory utilization
- Disk usage
- Network traffic
- System uptime
- Load average

Verify that Prometheus can scrape the Node Exporter endpoint.

### 4. Blackbox Exporter

Blackbox Exporter is configured using:

`blackbox/blackbox.yml`

It is used to monitor network reachability and service availability.

### 5. Loki and Grafana Alloy

Loki provides centralized log storage.

Grafana Alloy is configured using:

`alloy/config.alloy`

Loki configuration is stored in:

`loki/loki-config.yml`

### 6. Grafana

Import the dashboard JSON files from:

`grafana/`

Available dashboards include:

- NOC Command Center
- NOC Monitoring
- Internet & Service Monitoring
- Logs Dashboard

Configure the appropriate Prometheus and Loki data sources in Grafana.

### 7. Verify the Monitoring System

Once the services are running, verify:

- Prometheus targets are **UP**
- Node Exporter metrics are available
- Blackbox probes are returning results
- Grafana dashboards display metrics
- Loki is receiving logs
- Grafana can query Loki logs
- Alert rules are loaded successfully

## Configuration Files

| Component | Configuration |
|---|---|
| Prometheus | `prometheus/prometheus.yml` |
| Prometheus Alerts | `prometheus/alerts.yml` |
| Blackbox Exporter | `blackbox/blackbox.yml` |
| Grafana Alloy | `alloy/config.alloy` |
| Loki | `loki/loki-config.yml` |
| Grafana | `grafana/*.json` |

## Future Improvements

Potential future enhancements include:

* Automated deployment using Docker Compose
* SNMP-based network device monitoring
* Automated incident notifications
* Additional network device exporters
* SLA monitoring
* Automated configuration deployment
* Infrastructure-as-Code
* Integration with a ticketing or incident management system

## Author

**Sheka Bojamma**

GitHub: [@ShekaBojamma](https://github.com/ShekaBojamma)
