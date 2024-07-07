---
title: "Install and Configure Krs with MiniKube"
weight: 20
date: 2024-07-02
description: >
  How to install and configure KRS with a MiniKube cluster.
  Let's dicover that in this tutorial. 
author: "Oluchukwu Obi"
---

## Prerequisites

- Podman, Docker, or Virtual Box (container runtime)
- Kubectl

## Getting Started

### 1. Setup a MiniKube Kubernetes Cluster on your Local Machine
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube start
```
![minikube_cluster_done](https://github.com/kubetoolsca/krs/assets/171302280/23638e61-8416-43eb-943f-d8da34346585)

### 2. Setup KRS using these commands:

```
git clone https://github.com/kubetoolsca/krs.git
cd krs
pip install .
```

### 3. Initialize KRS to permit it access to your cluster using the given command,

```
krs init
```

### 4. Get a view of all possible actions with KRS, by running the given command
```
krs --help
```

```
krs --help
                                                                                
 Usage: krs [OPTIONS] COMMAND [ARGS]...                                         
                                                                                
 krs: A command line interface to scan your Kubernetes Cluster, detect errors,  
 provide resolutions using LLMs and recommend latest tools for your cluster     
                                                                                
╭─ Options ────────────────────────────────────────────────────────────────────╮
│ --install-completion          Install completion for the current shell.      │
│ --show-completion             Show completion for the current shell, to copy │
│                               it or customize the installation.              │
│ --help                        Show this message and exit.                    │
╰──────────────────────────────────────────────────────────────────────────────╯
╭─ Commands ───────────────────────────────────────────────────────────────────╮
│ exit         Ends krs services safely and deletes all state files from       │
│              system. Removes all cached data.                                │
│ export       Exports pod info with logs and events.                          │
│ health       Starts an interactive terminal using an LLM of your choice to   │
│              detect and fix issues with your cluster                         │
│ init         Initializes the services and loads the scanner.                 │
│ namespaces   Lists all the namespaces.                                       │
│ pods         Lists all the pods with namespaces, or lists pods under a       │
│              specified namespace.                                            │
│ recommend    Generates a table of recommended tools from our ranking         │
│              database and their CNCF project status.                         │
│ scan         Scans the cluster and extracts a list of tools that are         │
│              currently used.                                                 │
╰──────────────────────────────────────────────────────────────────────────────╯
```
### 5. Permit KRS to get information on the tools utilized in your cluster by running the given command 

```
krs scan
```

```
krs scan

Scanning your cluster...

Cluster scanned successfully...

Extracted tools used in cluster...


The cluster is using the following tools:

+-------------+--------+------------------+---------------+
| Tool Name   |   Rank | Category         | CNCF Status   |
+=============+========+==================+===============+
| cilium      |      1 | Network Policies | graduated     |
+-------------+--------+------------------+---------------+
| hubble      |      7 | Security Tools   | listed        |
+-------------+--------+------------------+---------------+

```

### 6. Get recommendations on possible tools to use in your cluster by running the given command 

```
krs recommend
```

```
krs recommend

Our recommended tools for this deployment are:

+------------------+------------------------+-------------+---------------+
| Category         | Recommendation         | Tool Name   | CNCF Status   |
+==================+========================+=============+===============+
| Network Policies | Already using the best | cilium      | graduated     |
+------------------+------------------------+-------------+---------------+
| Security Tools   | Recommended tool       | trivy       | listed        |
+------------------+------------------------+-------------+---------------+

```
 
### 7. Check the pod and namespace status in your Kubernetes cluster, including errors.

```
krs health
```

```
krs health

Starting interactive terminal...


Choose the model provider for healthcheck: 

[1] OpenAI 
[2] Huggingface

>> 1

Installing necessary libraries..........

openai is already installed.

Enter your OpenAI API key: sk-proj-qxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxP

Enter the OpenAI model name: gpt-3.5-turbo
API key and model are valid.

Namespaces in the cluster:

1. default
2. kube-node-lease
3. kube-public
4. kube-system
5. portainer

Which namespace do you want to check the health for? Select a namespace by entering its number: >> 4

Pods in the namespace kube-system:

1. cilium-9lqbq
2. cilium-ffpct
3. cilium-pvknr
4. coredns-85f59d8784-nvr2n
5. coredns-85f59d8784-p9jcv
6. cpc-bridge-proxy-c6xzr
7. cpc-bridge-proxy-p7r4p
8. cpc-bridge-proxy-tkfrd
9. csi-do-node-hwxn7
10. csi-do-node-q27rc
11. csi-do-node-rn7dm
12. do-node-agent-6t5ms
13. do-node-agent-85r8b
14. do-node-agent-m7bvr
15. hubble-relay-74686df4df-856pj
16. hubble-ui-86cc69bddc-xc745
17. konnectivity-agent-9k8vk
18. konnectivity-agent-h5fm2
19. konnectivity-agent-kf4xh
20. kube-proxy-94945
21. kube-proxy-qgv4j
22. kube-proxy-vztzf

Which pod from kube-system do you want to check the health for? Select a pod by entering its number: >> 1

Checking status of the pod...

Extracting logs and events from the pod...

Logs and events from the pod extracted successfully!


Interactive session started. Type 'end chat' to exit from the session!

>>  The log entries provided are empty {}, so there is nothing to analyze. Therefore, I can confirm that 'Everything looks good!' in this case.

If there were warnings or errors in the log entries, I would have analyzed them thoroughly to identify the root cause. Depending on the specific warnings or errors, potential steps to resolve the issues could include:

1. Analyzing the specific error message to understand the problem
2. Checking Kubernetes resources (e.g., pods, deployments, configmaps) for any misconfigurations
3. Verifying connectivity to external resources or dependencies
4. Checking for resource limitations or constraints that could be causing issues
5. Reviewing recent changes in the Kubernetes environment that could have introduced problems
6. Using Kubernetes troubleshooting tools like kubectl logs, describe, or events to gather more information 

By following these steps and addressing any identified issues, you can resolve warnings or errors in the Kubernetes environment.

>> Wonderful, anything else to note?
>>  In addition to resolving warnings or errors in Kubernetes logs, it's important to regularly monitor and maintain the Kubernetes environment to ensure smooth operation. Some best practices for Kubernetes maintenance include:

1. Regularly updating Kubernetes components and cluster nodes to the latest stable versions to benefit from bug fixes and security patches.
2. Implementing automated backups of critical data and configurations to prevent data loss in case of failures.
3. Monitoring resource utilization and scaling components as needed to optimize performance and cost efficiency.
4. Implementing security best practices, such as network policies, RBAC, and pod security policies to protect the cluster from unauthorized access or malicious activities.
5. Conducting regular health checks and performance tuning to identify and address any bottlenecks or inefficiencies in the cluster.
6. Developing a disaster recovery plan and testing it periodically to ensure business continuity in case of unexpected events.

By following these maintenance practices, you can ensure the stability, scalability, and security of your Kubernetes environment for optimal DevOps operations.

>> Alright, so are we done?
>>  Yes, we have covered the analysis of the Kubernetes log entries and discussed best practices for Kubernetes maintenance. If you have any more questions or need further assistance, feel free to ask. Otherwise, we can consider this conversation complete.

>> Wonderful. Thanks! end chat
>>  You're welcome! If you have any more questions in the future, feel free to reach out. Have a great day! Goodbye!

>> end chat


```
