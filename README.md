# kubectl-getc
A simple kubectl plugin that orders fields in status condition to always show the type first, followed by status, reason, message, observedGeneration and lastTransitionTime.

## Prerequisites
Before you begin, ensure you have the following installed on your system:

- kubectl - Kubernetes command-line tool that allows you to run commands against Kubernetes clusters.
- yq (version 4.x or higher) - A portable command-line YAML, JSON, and XML processor.

## Installation
To install the kubectl-getc plugin, follow these steps:

Clone the repository:

```bash
git clone https://github.com/raghavendra-talur/kubectl-getc.git
```

Make the script executable and move it to a directory in your PATH:

```bash
chmod +x kubectl-getc/kubectl-getc
sudo mv kubectl-getc/kubectl-getc /usr/local/bin
```

## Usage
To use the plugin, simply replace get subcommand with getc in your regular kubectl get commands when using yaml output. For example:

```bash
kubectl getc pods -o yaml
```

## Sample output
Status condition with the get subcommand
```
  status:
    conditions:
    - lastProbeTime: null
      lastTransitionTime: "2024-04-10T01:30:36Z"
      status: "True"
      type: Initialized
    - lastProbeTime: null
      lastTransitionTime: "2024-04-10T01:30:43Z"
      status: "True"
      type: Ready
    - lastProbeTime: null
      lastTransitionTime: "2024-04-10T01:30:43Z"
      status: "True"
      type: ContainersReady
    - lastProbeTime: null
      lastTransitionTime: "2024-04-10T01:30:36Z"
      status: "True"
      type: PodScheduled
```

Status condition with the getc subcommand
```
    status:
      conditions:
        - type: Initialized
          status: "True"
          reason: null
          message: null
          observedGeneration: null
          lastTransitionTime: "2024-04-10T01:30:36Z"
        - type: Ready
          status: "True"
          reason: null
          message: null
          observedGeneration: null
          lastTransitionTime: "2024-04-10T01:30:43Z"
        - type: ContainersReady
          status: "True"
          reason: null
          message: null
          observedGeneration: null
          lastTransitionTime: "2024-04-10T01:30:43Z"
        - type: PodScheduled
          status: "True"
          reason: null
          message: null
          observedGeneration: null
          lastTransitionTime: "2024-04-10T01:30:36Z"
```
