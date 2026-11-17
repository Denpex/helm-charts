# Denpex Helm charts

Source for the `denpex-gpu-watcher` chart, published at `https://denpex.com/charts` and listed
on Artifact Hub.

The chart runs a small watcher on every GPU node. It follows the node's kernel log, recognises
GPU and distributed-training faults (GPU Xid errors, a GPU falling off the bus, uncorrectable
ECC, CUDA out-of-memory, NCCL watchdog timeouts, hung tasks, Lustre errors) and diagnoses each
one on the node. Nothing leaves the node unless you set a Denpex API key. Details and values:
[charts/denpex-gpu-watcher/README.md](charts/denpex-gpu-watcher/README.md).

## Quickstart

```bash
helm repo add denpex https://denpex.com/charts
helm install denpex-watcher denpex/denpex-gpu-watcher --namespace monitoring --create-namespace
kubectl -n monitoring logs -l app.kubernetes.io/name=denpex-gpu-watcher -f
```

The earlier `denpex-agent` chart that lived here downloaded its script at every pod start and
is replaced by this one.

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
