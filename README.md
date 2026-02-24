# ELK Learning Project
Enterprise-Style Elastic Stack Deployment on PCs

---

## Overview

The ELK Learning Project is a structured lab designed to simulate a small-scale enterprise logging and monitoring environment.

The project focuses on:
- Multi-node Elasticsearch cluster deployment
- Kibana and Fleet configuration
- Elastic Agent enrollment
- Stack monitoring and health troubleshooting
- Cluster configuration and resilience testing

This lab is built entirely on PCs and serves as a hands-on platform for learning system administration, networking, and security monitoring.

---

## Infrastructure

### PCs
- 1 × Ubuntu Server (Elasticsearch Node + Kibana)
- 1 × Rocky Server (Elasticsearch Node)
- 1 x Ubuntu Server (Elasticsearch Node)

---

## Elasticsearch Cluster Architecture

Cluster Name: my-application

Nodes:
- node-1 (master, data)
- node-2 (master, data)
- node-3 (master, data)

Cluster Type:
- 3-node distributed cluster
- Replica shards enabled
- Fault tolerance supported (1 node failure scenario)

---

## Services Deployment

### Elasticsearch
- Installed on all three nodes
- Configured for cluster discovery
- Nodes joined using cluster.initial_master_nodes
    - then removed, as it was used for bootstrap only
- Verified using cluster health API

### Kibana
- Installed on 1 of elasticsearch node
- Connected to Elasticsearch cluster
- Used for:
  - Stack Monitoring
  - Index Management
  - Fleet Management

### Fleet Server
- Will be installed and enrolled
- Used to manage Elastic Agents

### Elastic Agent
- Enrolled using Fleet enrollment token
- Connected to Fleet Server
- Used for monitoring and telemetry

---

## Cluster Monitoring & Testing

Performed:

- Cluster health verification
- Replica shard validation
- Stack monitoring setup
- Node failure simulation testing
- Bootstrap password troubleshooting
- 503 cluster health debugging
- Missing replica shard analysis

---

## Network Topology (Simplified)

ISP Router
→ Unmanaged Switch
→ Elasticsearch Nodes (3)
→ Kibana + Fleet Server

All nodes communicate within the same subnet.

---

## Learning Objectives

This project was created to develop skills in:

- Distributed systems architecture
- Linux server administration
- Elasticsearch cluster management
- High availability concepts
- Troubleshooting production-style issues
- Monitoring and observability practices

---

## Future Improvements

- Introduce Logstash pipeline
- Add Kafka between agents and Elasticsearch
- Separate dedicated master and data nodes
- Implement VLAN segmentation
- Deploy Suricata logs into Elasticsearch
- Harden security (TLS, certificates, RBAC tuning)

---

## Project Status

Active Development – Architecture still evolving.
