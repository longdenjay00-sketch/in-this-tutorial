# In This Tutorial

> *A tutorial should teach you "how."*

How to build, how to explore, and how to operate across the modern Linux stack.

---

## The Hook

> **"Chances are, Docker is your go-to..."**

For most developers and operators, containerization begins and ends with Docker. It is familiar, battle-tested, and ubiquitous.

**...But did you know?**

There is a vast ecosystem of container runtimes thriving beyond the default Docker engine. Containerization is not a monolithic tool—it is an Open Container Initiative (OCI) standard supported by specialized engines designed for different workloads, environments, and threat models.

---

## Did You Know? The Container Runtime Ecosystem

When you examine how containers actually execute, different engines optimize for distinct architectural priorities:

### 1. Some are lighter
Minimalist runtimes strip away background daemons and desktop overhead to deliver sub-millisecond execution and a tiny memory footprint:
- **`runc` & `crun`**: Low-level OCI runtimes. `crun` (written in C) provides lightning-fast startup and negligible resource usage.
- **`containerd`**: The lean, daemon-driven core engine that powers production infrastructure without unnecessary bloat.
- **`proot` / `chroot`**: Userspace virtualization engines that execute complete guest distributions without requiring kernel root privileges (e.g. running Linux environments inside Termux on Android).

### 2. Some are more secure
Standard Linux containers share the host kernel. When running untrusted multi-tenant code, security-focused runtimes introduce hardware or user-space isolation barriers:
- **Kata Containers**: Wraps each container pod in its own dedicated, lightweight microVM (via QEMU or Cloud-Hypervisor), providing hardware-enforced VM isolation at container speeds.
- **gVisor (`runsc`)**: Intercepts guest system calls in an isolated user-space kernel (Sentry), dramatically shrinking the attack surface on the host kernel.

### 3. Some are specifically built for Kubernetes
Modern orchestration clusters have phased out heavy general-purpose container engines in favor of dedicated Container Runtime Interface (CRI) implementations:
- **CRI-O**: Built strictly from the ground up for Kubernetes. It exists only to serve the Kubelet, with zero extraneous features or overhead.
- **`containerd` (CRI integration)**: High-throughput container orchestration interface tuned specifically for pod life-cycle management.

---

## What We Cover

A tutorial should always teach practical mechanics, not just theory. In this tutorial series, we explore:
- **How to** evaluate container runtimes based on latency, security boundaries, and runtime overhead.
- **How to** run daemonless, rootless containers safely across unprivileged host environments.
- **How to** configure alternate runtimes for Kubernetes nodes, CI/CD runners, and edge devices.
