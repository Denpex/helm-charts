# Denpex GPU & NCCL Watcher Helm chart

Runs a small watcher on every GPU node. It follows the node's kernel log, recognises GPU and
distributed-training faults (GPU Xid errors, a GPU falling off the bus, uncorrectable ECC,
CUDA out-of-memory, NCCL watchdog timeouts, hung tasks, Lustre errors) and diagnoses each one
on the node. Results are printed as JSON lines in the pod log.

```bash
helm repo add denpex https://denpex.com/charts
helm install denpex-watcher denpex/denpex-gpu-watcher --namespace monitoring --create-namespace
kubectl -n monitoring logs -l app.kubernetes.io/name=denpex-gpu-watcher -f
```

## What leaves the node

Nothing, unless you set an API key. With `--set denpex.apiKey=dpx_...` (or
`denpex.existingSecret`), the log context around each fault is also sent to Denpex for cloud
diagnosis and alert routing. `--set denpex.upload=false` keeps everything on the node even
with a key.

## Permissions

The watcher reads `/dev/kmsg` and `/var/log` from the host, read-only, which needs a privileged
container (the same approach as the Kubernetes node-problem-detector). It has no Kubernetes API
access unless you enable `denpex.autoCordon`, which creates a ServiceAccount allowed to get and
patch nodes, and cordons a node only on hardware faults, never on out-of-memory or NCCL
timeouts.

## Values

| Key | Default | Meaning |
|---|---|---|
| `image.repository` / `image.tag` | `ghcr.io/denpex/denpex-node-watcher` / `1.1.35` | Watcher image |
| `denpex.apiKey` / `denpex.existingSecret` | empty | Optional Denpex API key |
| `denpex.upload` | `true` | Send fault context when a key is set |
| `denpex.autoCordon` | `false` | Cordon on hardware faults |
| `denpex.cooldownSeconds` | `60` | Minimum gap between workload-fault reports |
| `preflight.enabled` | `false` | Run `denpex preflight` once at install |
