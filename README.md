# Raspberry Pi 5 Homelab

Lightweight ARM homelab built on Raspberry Pi 5 for Kubernetes, observability, and distributed workload experiments.

---

## Overview

- 3 nodes → k3s Kubernetes cluster (1 master + 2 workers)
- 1 node → standalone LLM / Open WebUI experiments

Use cases:
- Kubernetes workloads
- Monitoring with kube-prometheus-stack
- GitOps with Argo CD
- Distributed LLM with distributed-llama / exo
- GitHub Actions runners (WIP)

---

## Architecture

- rpi1 — master (192.168.0.101)
- rpi2 — worker (192.168.0.102)
- rpi3 — worker + Pi-hole DNS/DHCP (192.168.0.103)
- rpi4 — standalone node (192.168.0.110)

---

## Tech Stack

- k3s (Kubernetes)
- containerd
- Argo CD (apps-of-apps)
- kube-prometheus-stack (Prometheus + Grafana + Alertmanager)
- Traefik (ingress)
- Ansible
- distributed-llama / exo / Open WebUI
- docker-compose 

---

## Hardware

- 4 × Raspberry Pi 5 (16GB RAM)
- SSD/NVMe storage (256GB k3s master, 128GB worker/standalone nodes)
- ARM64

---

## Features

- GitOps deployment for prod/beta Kubernetes overlays
- Monitoring with ServiceMonitor (5s global scrape)
- Ingress:
  - grafana.homelab
  - prometheus.homelab
  - alert.homelab
  - argocd.homelab
- LLM experiments across the standalone node and k3s nodes

---

## Setup (short)

1. Install OS on nodes (ARM64)
2. Bootstrap k3s on rpi1-rpi3
3. Install Argo CD
4. Deploy prod/beta overlays via GitOps
5. Install monitoring with Helm values from `k8s/helm/monitoring`

---

## Notes

- No GPU → only quantized LLMs
- Limited CPU → experimental workloads
- rpi4 is intentionally outside the k3s cluster
- Suitable for learning and testing

---

## TODO

- GitHub Actions runners
- Centralized logging
- Better LLM orchestration
