# Zabbix-monitoring

# Enterprise Monitoring Infrastructure with Zabbix

## Project Description
This project automates the deployment and integration of an enterprise-grade monitoring solution using **Zabbix Server** and **Zabbix Agents**. It extends the 5-tier local multi-VM environment by implementing active and passive telemetry collection, automated process discovery, metric graph visualization, and threshold-based alerting triggers across all system components.

It highlights core DevOps capabilities in full-stack observational engineering, custom agent deployment, metric aggregation, proactive system alerts, and distributed infrastructure management.

---

## Architecture Overview
The Zabbix server architecture polls metrics via Zabbix Agent nodes running locally across all application components over encrypted channels:

* **Zabbix Server Host:** Core engine processing incoming monitoring data, executing triggers, managing database persistence (MySQL/PostgreSQL), and powering the PHP Web Frontend.
* **Zabbix Agents (Monitored Nodes):**
  * `web01` (Nginx): Monitors HTTP worker processes, connection limits, and network throughput.
  * `app01` (Tomcat): Tracks JVM heap utilization, active threads, and Java application health.
  * `db01` (MariaDB): Collects database query statistics, active thread connections, and disk I/O metrics.
  * `mc01` (Memcached): Monitors memory fragmentation, cache hit/miss ratios, and connection pool saturation.
  * `rmq01` (RabbitMQ): Tracks message queue depth, consumer state, and node resource consumption.

### Architecture Diagram
```text
                     ┌───────────────────────────┐
                     │   Zabbix Monitoring Hub   │
                     │  (Server + MySQL + Web)   │
                     └─────────────┬─────────────┘
                                   │
                Zabbix Agent Traffic (Port 10050/10051)
                                   │
      ┌──────────────┬─────────────┼─────────────┬──────────────┐
      ▼              ▼             ▼             ▼              ▼
  [ web01 ]      [ app01 ]     [ db01 ]      [ mc01 ]       [ rmq01 ]
   (Nginx)       (Tomcat)     (MariaDB)    (Memcached)    (RabbitMQ)


Tech Stack & Tools
Monitoring Engine: Zabbix Server (v6.0 LTS / v7.0)

Agent Framework: Zabbix Agent / Zabbix Agent 2

Database Backend: PostgreSQL or MariaDB

Web Interface: Apache / Nginx with PHP Frontend

Operating Systems: Ubuntu / CentOS Linux

Automation: Bash Shell Provisioning Scripts

Deployment & Setup Instructions
Prerequisites
Active 5-tier target virtual machine environment (web01, app01, db01, mc01, rmq01).

Dedicated VM or container host with root/sudo privileges for the Zabbix Server.


<img width="724" height="439" alt="zabbix" src="https://github.com/user-attachments/assets/3ddb2789-162d-49a2-bded-76ff30460c82" />
