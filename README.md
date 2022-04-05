# LOXILIGHT

![loxilight Logo](logos/color.png)

## Overview

Cloud-native Network functions (CNFs) are the evolution of how network functions are built using micro-service architecture. The following figure shows the evolutionary journey of network functions thus far:

![loxilight Logo](logos/CNF.png)

CNI (or cloud-native networking interface) plays a very important role in deployment of data-intensive CNFs since CNI decides how network communication happens between the CNFs inside the same node or across multiple nodes of a same K8s cluster. CNI intercepts all packets between CNFs in-line and applies security and networking policies to them. There are many CNIs to choose from depending on the use-case but when bandwidth of 10Gbps or more is needed per CNF, we need to carefully select the CNI to ensure optimal performance. 

Loxilight is based on [eBPF](https://www.netlox.io/post/cloud-networking-with-ebpf) technology. It works either as a pure eBPF mode or in a hybrid-mode with multi-vendor DPU support when DPU units are available. As a matter of fact, it is one of the first CNI to provide such a hybrid mode of operation working seamlessly in both eBPF mode (generic) and multi-vendor DPU mode while providing hyperscale performance of 40G or more per server node.

There are number of [CNIs](https://github.com/containernetworking/cni) available in the market which uses stock Linux, iptables etc. They all work fine until they hit the scale and performance bottlenecks. Loxilight solution unleashes the benefits of eBPF and DPU to be used for high performance and ultra-low latency Cloud Native networking.

## Compatibility Matrix 

### Host OS requirements
To install LOXILIGHT Packages, you need the 64-bit version of one of these Ubuntu versions:
* Ubuntu Focal 20.04(LTS)
* Ubuntu Hirsute 21.04
* RockyOS (Planned)
* Enterprise Redhat (Planned)
* Windows Server(Planned)

### Linux Kernel Requirements
* Linux Kernel Version >= 5.1.0

### Compatible DPU Lists
* NVIDIA Mellanox Bluefield-II
* Intel Mount Evans DPU (Planned)
* Pensando DSC (Planned)

### Compatible Kubernetes Versions
* Kubernetes 1.19
* Kubernetes 1.20
* Kubernetes 1.21
* Kubernetes 1.22

## Roadmap
We are adding features very quickly to Loxilight. Check out the list of features we are considering on our Roadmap [page](docs/roadmap.md). 

## Documentation
- [Architecture](docs/design/architecture.md)
- Installation
  - [Installing loxilight DP components on Nvidia BF2](docs/install_bf2.md)
  - [Installing Kubernetes and loxiCNI](docs/install_k8s.md)
- [Configuration](docs/configuration.md)
- [Troubleshooting](docs/troubleshooting.md)
