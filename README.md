# Zabbix Infrastructure Monitoring

Infrastructure monitoring environment built around **Zabbix**, **SNMP**, **Linux** and **Grafana**, with additional operational and telemetry data stored in **MariaDB**.

> **Work in progress** — documentation and sanitized examples are being added progressively.

The goal of this project was to design and operate a centralized monitoring environment capable of providing visibility into servers, network equipment and infrastructure health while applying security and access-control principles.

> This repository is a sanitized reconstruction of a real-world environment.  
> All IP addresses, hostnames, credentials and infrastructure details are fictional or anonymized.

## Objectives

- Centralize infrastructure monitoring
- Monitor Linux systems and network devices
- Collect metrics using Zabbix Agent and SNMP
- Detect availability and performance problems
- Build infrastructure dashboards
- Store and visualize operational telemetry from external systems
- Restrict access to monitoring services
- Document architecture, security decisions and troubleshooting procedures

## Technologies

- Zabbix
- Grafana
- Linux
- PostgreSQL
- MariaDB
- SNMP
- Nginx
- UFW
- Fail2ban
- TLS / HTTPS

## Architecture

```text
                                      ┌──────────────────┐
                                      │      Grafana     │
                                      │  Visualization   │
                                      └────────┬─────────┘
                                               │
                         ┌─────────────────────┴─────────────────────┐
                         │                                           │
                ┌────────▼────────┐                         ┌────────▼────────┐
                │     Zabbix      │                         │     MariaDB     │
                │     Server      │                         │ Operational /   │
                │                 │                         │ Telemetry Data  │
                └───────┬─────────┘                         └────────▲────────┘
                        │                                            │
            ┌───────────┴───────────┐                         Data ingestion
            │                       │                                │
     Zabbix Agent                  SNMP                      External systems /
            │                       │                            devices
     ┌──────▼──────┐        ┌──────▼──────┐
     │ Linux Hosts │        │   Network   │
     │             │        │   Devices   │
     └─────────────┘        └─────────────┘
                        │
                ┌───────▼────────┐
                │   PostgreSQL   │
                │ Zabbix Backend │
                └────────────────┘
```

## Monitoring

The environment was designed to monitor:

- Host availability
- CPU utilization
- Memory usage
- Disk usage
- Network interfaces
- Service availability
- Network device status
- SNMP metrics
- Infrastructure health

## Data Storage

- **PostgreSQL** — used as the Zabbix backend database.
- **MariaDB** — used to store operational and telemetry data collected from external systems and devices.

This separation keeps the Zabbix monitoring backend independent from application-specific and operational telemetry.

## Security

Security measures and considerations included:

- HTTPS/TLS for web access
- Nginx as the web/reverse-proxy layer
- UFW firewall rules limiting exposed services
- Restricted management access
- SNMP access control
- Least-privilege considerations
- Fail2ban to reduce brute-force exposure on authentication services
- Controlled access between monitoring services and monitored infrastructure
- No credentials or sensitive production data stored in this repository

## Troubleshooting

Some of the issues investigated during implementation included:

- SNMP timeouts
- SNMP authorization errors
- Firewall connectivity
- Zabbix Agent communication
- Incorrect SNMP credentials
- Network reachability
- Host availability problems
- Service and port accessibility

Troubleshooting procedures and sanitized examples will be documented in the `docs/` directory.

## Repository Structure

```text
.
├── README.md
├── docs/
│   ├── architecture.md
│   ├── security.md
│   └── troubleshooting.md
├── diagrams/
├── examples/
│   ├── agent/
│   └── snmp/
└── scripts/
```

## Documentation Plan

This repository will be expanded with additional technical documentation and sanitized examples, including:

```text
docs/architecture.md
docs/security.md
docs/troubleshooting.md
examples/snmp/
examples/agent/
```

Planned documentation will cover:

- Infrastructure design and data flow
- Zabbix Agent and SNMP monitoring
- PostgreSQL and MariaDB roles
- Network and service access controls
- TLS/HTTPS configuration
- Troubleshooting methodology
- Common SNMP and Zabbix connectivity issues
- Sanitized configuration examples

Only technologies, configurations and security measures that were actually implemented, tested or evaluated will be documented.

Planned or proposed improvements will be clearly identified as such rather than presented as completed implementations.

## Disclaimer

This repository contains a sanitized reconstruction created for educational and portfolio purposes.

No confidential company information, production credentials, customer data, internal network addresses or other sensitive infrastructure details are included.
