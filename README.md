# Kubernetes cluster setup using Kubespray and cluster management with Rancher
## 📑 Table of Contents

- [Introduction](##Introduction)
- [Overview](#verview)
- [Setting up Virtual Machines](#setting-up-virtual-machines)
- [Kubespray Installation](#kubespray-installation)
- [Setting up the Kubernetes Cluster](#setting-up-the-kubernetes-cluster)
- [Installing Rancher to Manage our Kubernetes Cluster](#installing-rancher-to-manage-our-kubernetes-cluster)

## 🧾 Introduction

This guide demonstrates how to set up a production-grade Kubernetes cluster using Kubespray -— a versatile and powerful tool that simplifies the deployment of Kubernetes on various cloud environments, virtual machines, or bare-metal servers. By leveraging the capabilities of Kubespray. Kubespray simplifies the process of provisioning Kubernetes clusters with powerful automation, while Rancher provides an intuitive interface for managing clusters, workloads, users, and policies.
By combining these two tools, you'll gain a flexible, scalable, and manageable Kubernetes environment that is suitable for both learning and real-world applications.

## 🔍 Overview

Kubespray is an open-source tool that uses Ansible to automate the installation and configuration of Kubernetes clusters. It supports various infrastructure types including public cloud, private cloud, virtual machines, and bare metal.

### Key features of Kubespray:

* Highly configurable and production-ready

* Supports High Availability (HA) clusters

* Compatible with major Linux distributions

* Extensible via Ansible’s playbooks and inventory structure

### Rancher is a powerful Kubernetes management platform that provides:

* Centralized cluster management (on-prem, cloud, hybrid)

* User-friendly web UI and RBAC (Role-Based Access Control)

* Monitoring, logging, and app catalog (via Helm)

CI/CD, backup, and security policies

By deploying Rancher on top of your Kubernetes cluster, you get a full-featured control plane to easily manage workloads, nodes, namespaces, users, and more.

## 🖥️ Setting up Virtual Machines

For this tutorial, we will use 4 VirtualBox VMs running Ubuntu 22.04 LTS, all connected through a NAT network with port forwarding or optionally through a host-only network for easier SSH access.

## 💻 VM Architecture
| VM  | Role                   | Description                                      |
| --- | ---------------------- | ------------------------------------------------ |
| VM1 | Kubernetes Master Node | Runs control plane components                    |
| VM2 | Kubernetes Worker Node | Runs workloads and joins the cluster             |
| VM3 | Kubespray Host         | Runs Ansible to provision the Kubernetes cluster |
| VM4 | Rancher Server         | Hosts the Rancher UI to manage the cluster       |

All VMs should have:

Ubuntu 22.04 installed

SSH enabled

Minimum 2 CPUs, 2–4 GB RAM, and 20 GB disk space (per VM)

✅ Make sure all nodes can reach each other over the private network and that the Ansible control node (VM3) can SSH into the master and worker nodes.

## 🗺️ Network Topology Diagram

