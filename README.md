# Zabbix Infrastructure Monitoring

Infrastructure monitoring project built around **Zabbix**, **SNMP**, **Linux** and **Grafana**.

The goal of this project was to design and operate a centralized monitoring environment capable of providing visibility into servers, network equipment and infrastructure health while applying basic security and access-control principles.

> This repository is a sanitized reconstruction of a real-world environment.  
> All IP addresses, hostnames, credentials and infrastructure details are fictional or anonymized.

## Objectives

- Centralize infrastructure monitoring
- Monitor Linux and network devices
- Collect metrics using Zabbix Agent and SNMP
- Detect availability and performance problems
- Build infrastructure dashboards
- Restrict access to monitoring services
- Document troubleshooting procedures

## Technologies

- Zabbix
- Linux
- SNMP
- Grafana
- MySQL / MariaDB
- Nginx
- UFW
- Fail2ban
- TLS / HTTPS

## Architecture

```text
                         ┌──────────────────┐
                         │      Grafana     │
                         │   Visualization  │
                         └────────┬─────────┘
                                  │
                         ┌────────▼─────────┐
                         │      Zabbix      │
                         │      Server      │
                         └───────┬─┬────────┘
                                 │ │
                    Zabbix Agent │ │ SNMP
                                 │ │
                    ┌────────────┘ └─────────────┐
                    │                            │
             ┌──────▼──────┐             ┌──────▼──────┐
             │ Linux Hosts │             │   Network   │
             │             │             │   Devices   │
             └─────────────┘             └─────────────┘
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

## Security

Security considerations included:

- HTTPS/TLS for web access
- Firewall rules limiting exposed services
- Restricted management access
- SNMP access control
- Least-privilege considerations
- Fail2ban for exposed authentication services
- Separation between monitoring and monitored systems

## Troubleshooting

Some of the issues explored during implementation included:

- SNMP timeouts
- SNMP authorization errors
- Firewall connectivity
- Zabbix Agent communication
- Incorrect SNMP credentials
- Network reachability
- Host availability problems

More detailed troubleshooting documentation will be available in the `docs/` directory.

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
## Disclaimer

This repository contains a sanitized reconstruction created for educational and portfolio purposes.

No confidential company information, production credentials, customer data or internal network information is included.

## Documentation Plan

This repository will be expanded with additional technical documentation and sanitized examples, including:

docs/architecture.md
docs/security.md
docs/troubleshooting.md
examples/snmp/
examples/agent/

Only technologies, configurations and security measures that were actually implemented, tested or evaluated will be documented.

Planned or proposed improvements will be clearly identified as such rather than presented as completed implementations.
