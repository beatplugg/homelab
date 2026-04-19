# Raspberry Pi 5 Homelab Cluster

Lightweight 4-node ARM cluster built on Raspberry Pi 5 for Kubernetes, observability, and distributed workload experiments.

---

## Overview

- 3 nodes → k3s Kubernetes cluster (1 master + 2 workers)
- 1 node → standalone (LLM / experiments)

Use cases:
- Kubernetes workloads
- Monitoring (Prometheus + Grafana + Alertmanager)
- GitOps (Argo CD)
- Distributed LLM (distributed-llama / exo)
- CI/CD runners (WIP)

---

## Architecture

- rpi1 — master (192.168.0.101)
- rpi2 — worker (192.168.0.102)
- rpi3 — worker (192.168.0.103)
- rpi4 — standalone node (192.168.0.110)

---

## Tech Stack

- k3s (Kubernetes)
- containerd
- Argo CD (apps-of-apps)
- Prometheus + Grafana + Alertmanager
- Traefik (ingress)
- Ansible
- distributed-llama / exo

---

## Hardware

- 4 × Raspberry Pi 5 (16GB RAM)
- NVMe SSD (mounted on master)
- ARM64

---

## Features

- GitOps deployment (Argo CD)
- Monitoring with ServiceMonitor (10s scrape)
- Ingress:
  - grafana.homelab
  - prometheus.homelab
  - argocd.homelab
- LLM experiments across nodes

---

## Setup (short)

1. Install OS on nodes (ARM64)
2. Bootstrap k3s (master + workers)
3. Install Argo CD
4. Deploy apps via GitOps
5. Install monitoring (Helm)

---

## Notes

- No GPU → only quantized LLMs
- Limited CPU → experimental workloads
- Suitable for learning and testing

---

## TODO

- GitHub Actions runners
- Centralized logging
- Better LLM orchestration