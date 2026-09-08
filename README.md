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
