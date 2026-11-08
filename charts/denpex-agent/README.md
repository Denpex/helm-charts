# Denpex GPU Crash Forensics Helm Chart (`denpex-agent`)

Official Kubernetes Helm chart for deploying the **Denpex GPU & Distributed Training Diagnostics** DaemonSet across NVIDIA H100, H200, B200, A100, and L40S GPU nodes.

Automatically monitors `/dev/kmsg`, DCGM telemetry, ECC row remapping, NVLink/PCIe errors, NCCL collective hangs, and CUDA OOM events across every GPU node in your cluster.

## Quickstart

```bash
helm install denpex-agent ./charts/denpex-agent \
  --namespace kube-system \
  --set denpex.apiKey=dpx_your_api_key
```

## Official Denpex Ecosystem & Documentation

| Resource | URL | Description |
| :--- | :--- | :--- |
| **Denpex Platform** | [https://denpex.com](https://denpex.com) | GPU crash forensics and distributed training diagnostics |
| **Interactive Console** | [https://denpex.com/console](https://denpex.com/console) | Browser-based log analyzer with zero-egress local mode |
| **Documentation Hub** | [https://denpex.com/docs](https://denpex.com/docs) | Full integration guides for Kubernetes, Slurm, and PyTorch |
| **5-Minute Quickstart** | [https://denpex.com/docs/quickstart](https://denpex.com/docs/quickstart) | Get your first GPU crash diagnosis in under 5 minutes |
| **Python Agent & CLI** | [https://denpex.com/docs/agent](https://denpex.com/docs/agent) | Single-file agent and `pip install denpex` CLI reference |
| **REST API & SDKs** | [https://denpex.com/docs/api](https://denpex.com/docs/api) | HTTP endpoints, Python SDK, TypeScript SDK, and MCP server |
| **CI & GitHub Action** | [https://denpex.com/docs/ci](https://denpex.com/docs/ci) | Automated preflight and post-failure diagnosis in CI |
| **VS Code Extension** | [https://denpex.com/vscode](https://denpex.com/vscode) | Offline log diagnostics for Visual Studio Code |
| **Open VSX Extension** | [https://denpex.com/openvsx](https://denpex.com/openvsx) | Extension for Cursor, Windsurf, VSCodium, and Gitpod |
| **Failure Encyclopedia** | [https://denpex.com/failures](https://denpex.com/failures) | Searchable database of 700+ GPU, CUDA, and NCCL failure signatures |
| **Free GPU Calculators** | [https://denpex.com/tools](https://denpex.com/tools) | VRAM calculators, NCCL timeout calculators, and topology tools |
| **NVIDIA Xid Reference** | [https://denpex.com/xid](https://denpex.com/xid) | Hardware fault guide for Xid 31, 43, 48, 63, 74, 79, 94, 95, 119 |
| **NCCL Error Guide** | [https://denpex.com/nccl-errors](https://denpex.com/nccl-errors) | Root-cause analysis for collective timeouts and IB fabric drops |
| **CUDA Error Guide** | [https://denpex.com/cuda-errors](https://denpex.com/cuda-errors) | OOM, device-side assert, illegal memory access, and driver mismatches |
| **vLLM Error Guide** | [https://denpex.com/vllm-errors](https://denpex.com/vllm-errors) | KV cache exhaustion, PagedAttention, and tensor-parallel hangs |
| **Slurm GPU Guide** | [https://denpex.com/slurm-gpu-errors](https://denpex.com/slurm-gpu-errors) | Epilog scripts, cgroup OOM kills, and srun rank failures |
