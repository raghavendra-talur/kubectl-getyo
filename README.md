# kubectl-getc
A simple kubectl plugin that provides alternative get command that shows type as the first field in the status condition.

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

Copy the script to a directory in your PATH:

```bash
sudo cp kubectl-getc/kubectl-getc /usr/local/bin
```

## Usage
To use the plugin, simply replace get subcommand with getc in your regular kubectl get commands. For example:

```bash
kubectl getc pods
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
        lastProbeTime: null
        lastTransitionTime: "2024-04-10T01:30:36Z"
        status: "True"
      - type: Ready
        lastProbeTime: null
        lastTransitionTime: "2024-04-10T01:30:43Z"
        status: "True"
      - type: ContainersReady
        lastProbeTime: null
        lastTransitionTime: "2024-04-10T01:30:43Z"
        status: "True"
      - type: PodScheduled
        lastProbeTime: null
        lastTransitionTime: "2024-04-10T01:30:36Z"
        status: "True"
```
