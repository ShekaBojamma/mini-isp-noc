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

                    ┌──────────────────────────┐
                    │   Cisco Packet Tracer    │
                    │      ISP Topology        │
                    │                          │
                    │ Routers / Switches /     │
                    │ Network Nodes            │
                    └────────────┬─────────────┘
                                 │
                                 │ Network Monitoring
                                 ▼
                    ┌──────────────────────────┐
                    │       Ubuntu Linux VM    │
                    │                          │
                    │  Prometheus              │
                    │  Node Exporter           │
                    │  Blackbox Exporter       │
                    │  Grafana                 │
                    │  Loki                    │
                    │  Grafana Alloy           │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │       Grafana NOC         │
                    │        Dashboards         │
                    │                          │
                    │ Infrastructure           │
                    │ Internet & Services       │
                    │ Logs                      │
                    │ NOC Command Center        │
                    └──────────────────────────┘


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

## Screenshots

### NOC Command Center

![NOC Command Center](screenshots/noc-command-center.png)

### NOC Monitoring Dashboard

![NOC Monitoring](screenshots/noc-monitoring.png)

### Internet & Service Monitoring

![Internet Service Monitoring](screenshots/internet-service-monitoring.png)

### Logs Dashboard

![Logs Dashboard](screenshots/logs-dashboard.png)


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
