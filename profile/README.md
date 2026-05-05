<div align="center">
  <h1>ResonTech</h1>
  <p><strong>The ML & AI Operating Ecosystem.</strong></p>
  <p>Run any model on bare GPU. No DevOps, no overhead, no waiting — just submit and get results.</p>

  <p>
    <a href="https://reson.tech">reson.tech</a> ·
    <a href="https://beta.reson.tech">platform</a> ·
    <a href="https://reson.tech/docs">docs</a> ·
  </p>


</div>

---

## What it is

A unified runtime that turns bare GPUs into a single ecosystem you submit jobs to. Two execution modes — **Training** and **Inference** — share the same kernel, dashboard, API, and scheduler. CUDA, NCCL, networking, checkpointing, sharding, recovery: handled.

You write the model. We run the compute.

## Where it runs

| Pool | What it is | When to use |
|---|---|---|
| **Public Pool** | Shared multi-tenant. Instant provisioning, cold start <60s, FIFO + priority lanes. | Research, experiments, bursty workloads. |
| **Managed Cluster** | Reserved nodes, isolated kernel, persistent state, no queue contention. | Production training and serving with SLAs. |
| **Private Cluster** | Your hardware, our orchestration. Zero data egress, air-gap mode. | Compliance-bound, sovereign, or on-prem teams. |

## Training pipeline

1. **Shard dataset** — split into `.zip` shards (one per GPU), push to your bucket via browser, `rclone`, or SDK.
2. **Bucket pull** — workers get presigned URLs, pull shards directly. Control plane never sees your data.
3. **Submit** — pick GPU count and topology, submit. Cluster provisions and distributed training starts.
4. **Parallel execution** — gradients sync over NVLink/InfiniBand where available. Checkpoints stream back every epoch.
5. **Get the model** — weights land in `jobs/<name>/model_out/`. Download, deploy, or resume.

## What's handled for you

- **Topology-aware placement** — multi-node jobs prefer high-bandwidth interconnects (NVLink, InfiniBand).
- **Automatic NCCL** — no manual rank setup, no `MASTER_ADDR` rituals.
- **Checkpoint recovery** — node crash resumes from last epoch, not zero.
- **Elastic inference** — replicas scale on demand, idle scales to zero.
- **Spot reclamation** — preempted nodes auto-reschedule, not fail.
- **Cost-aware scheduling** — prefer cheaper nodes when latency budget allows.

## GPU support

Any CUDA GPU. Specifically tested:

- **Hopper** — H100 SXM5 / NVL / PCIe, H200
- **Ampere** — A100 (40/80GB), A40, A10
- **Ada Lovelace** — L40S, L40, L4
- **Workstation** — RTX 4090, RTX 3090, A6000, A5000
- **Volta / Turing** — V100 (16/32GB), T4

## Status

Currently in **private beta**. Onboarding teams across vision, LLMs, robotics, and federated medical workloads.

Apply at [reson.tech](https://reson.tech).

---

<div align="center">
  <sub>ResonTech — Bare GPU, zero DevOps.</sub><br/>
  <sub><a href="https://reson.tech">reson.tech</a></sub>
</div>
