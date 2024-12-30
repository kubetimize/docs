# Kubetimize Documentation

Welcome to the Kubetimize documentation page! Here, you'll find comprehensive information on how to set up, use, and optimize Kubernetes clusters with Kubetimize.

## Table of Contents

1. [Introduction](#introduction)
2. [Key Features](#key-features)
3. [Getting Started](#getting-started)
   - [Installation](#installation)
   - [Authentication](#authentication)
4. [Using Kubetimize](#using-kubetimize)
   - [Cluster Insights](#cluster-insights)
   - [Recommendations](#recommendations)
   - [Node Optimization](#node-optimization)
5. [Advanced Configuration](#advanced-configuration)
6. [FAQ](#faq)
7. [Support](#support)

---

## Introduction

Kubetimize is your go-to solution for managing Kubernetes clusters efficiently. It provides insights into resource usage, optimizes node utilization, ensures cost-effectiveness, and enhances overall cluster performance.

Kubetimize is designed for both platform-based deployments and on-premises setups, catering to organizations with unique operational needs.

---

## Key Features

- **Cost Optimization**: Identify unnecessary nodes and workloads to reduce cloud expenses.
- **Cluster Insights**: Detailed analytics for nodes, pods, and workloads.
- **Multi-Cloud Support**: Manage clusters across AWS, GCP, Azure, and hybrid environments.
- **AI-Powered Recommendations**: Automatically adjust cluster configurations for peak efficiency.
- **Security Enhancements**: Integrated security checks for compliance and best practices.

---

## Getting Started

### Installation

1. **Platform-Based Installation:**
   - Sign up at [Kubetimize Platform](https://kubetimize.com).
   - Download the Kubetimize agent for your Kubernetes cluster.
   - Follow the setup wizard to register your cluster.

2. **On-Premises Installation:**
   - Clone the Kubetimize repository:
     ```bash
     git clone https://github.com/kubetimize/kubetimize-agent.git
     ```
   - Deploy the agent using Helm or kubectl:
     ```bash
     helm install kubetimize-agent ./charts
     ```

### Authentication

Kubetimize uses secure authentication via AWS Cognito. For Google OAuth users, ensure you are registered in Cognito before accessing internal pages.

---

## Using Kubetimize

### Cluster Insights

Gain visibility into:
- CPU and memory usage per node and pod.
- Node and pod pricing across cloud providers.
- Historical trends and projections.

Access insights via the web dashboard or API endpoint:
```http
GET /v1/cluster/{cluster_id}/insights
```

### Recommendations

Get AI-driven recommendations for optimizing your cluster:
```http
GET /v1/getrecommendation/{org_id}/{cluster_id}
```
- **Node Right-Sizing**: Match node types to workload requirements.
- **Workload Distribution**: Balance workloads across nodes.

### Node Optimization

Kubetimize allows you to:
- Identify and delete underutilized nodes.
- Schedule node scaling based on demand.

Example:
```bash
kubetimize-cli optimize --cluster-id=my-cluster
```

---

## Advanced Configuration

### Custom Node Types
- Add or modify node types using the Kubetimize Planner.
- Enable custom launch templates for EC2 nodes in AWS.

Example:
```yaml
nodeTypes:
  - name: custom-large
    cpu: 8
    memory: 16GB
```

### Security Policies
- Define policies for workload access.
- Integrate with IAM roles for advanced permission management.

---

## FAQ

**Q1: How does Kubetimize calculate cost savings?**
A1: Cost savings are calculated based on the reduction in node and pod usage after optimization.

**Q2: Can Kubetimize run in air-gapped environments?**
A2: Yes, Kubetimize supports air-gapped deployments with minimal external dependencies.

**Q3: What if my cluster has no internet access?**
A3: Kubetimize agents can send data securely to your backend or store insights locally.

---

## Support

For assistance, reach out via:
- **Email**: support@kubetimize.com
- **Slack**: [Join our community](https://kubetimize.com/slack)
- **Documentation Portal**: [Docs](https://kubetimize.com/docs)

We’re here to help you optimize your Kubernetes clusters!

---

## API Key for On-Premises Installation

To ensure secure communication with the Kubetimize backend, an API key is required for on-premises installations. Follow these steps:

1. **Generate Your API Key:**
   - Log in to the Kubetimize platform.
   - Navigate to **Account Settings > API Keys**.
   - Generate and copy your unique API key.

2. **Set the API Key in Your Environment:**
   Add the following line to your server's environment configuration:
   ```env
   KUBETIMIZE_API_KEY=YOUR_API_KEY
   ```

3. **Validate API Key Communication:**
   Test the connection using cURL or a similar tool:
   ```bash
   curl -X GET "https://api.kubetimize.com/v1/status" \
   -H "X-API-Key: YOUR_API_KEY"
   ```

