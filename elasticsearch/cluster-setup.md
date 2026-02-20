# Elasticsearch Cluster Setup

This document describes how the 3-node Elasticsearch cluster was created for the Learning Project.

---

## Initial Node Setup (Node 1)

Operating System: Ubuntu Server  
Role: First cluster node (bootstrap node)

### Step 1 – Install Elasticsearch & Kibana

Elasticsearch and Kibana were installed on the first Ubuntu server.

After installation, Elasticsearch was started.  
Since this was the first node, it automatically:

- Generated the cluster UUID
- Generated the elastic user password
- Generated an enrollment token
- Enabled security by default

---

## Generate Enrollment Token

To allow other nodes to join the cluster, an enrollment token was generated on Node 1:

```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node
```

---

## Adding Node 2
Operating System: Ubuntu Server

### Step 1 - Install Elasticsearch

Elasticsearch was installed normally 

### Step 2 - Join cluster using enrollment token

The generated token from Node 1 was used during setup:

```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token>
```

After configuration:

```bash
sudo systemctl start elasticsearch
```

Node successfully join the cluster

---

## Adding Node 3
Operating System: Rocky Server

The same process was repeated:
1. Install Elasticsearch
2. Use enrollment token from Node 1
3. Start Elasticsearch service

Node successfully joined the cluster

---

## Cluster Verification
Cluster health was verified using:
```bash
curl -u elastic https://localhost:9200/_cluster/health?pretty
```

Also verified in Kibana under:
Stack Management → Monitoring
