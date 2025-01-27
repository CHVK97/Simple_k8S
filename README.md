# Simple_K8S

## Overview
Simple_K8S is a straightforward project designed to demonstrate the core concepts and functionality of Kubernetes. This project provides examples and configurations for deploying containerized applications on a Kubernetes cluster, showcasing features like Pods, Deployments, Services, ConfigMaps, and more.

## Features
- **Container Orchestration**: Deploy and manage containerized applications.
- **Declarative Configuration**: Use YAML manifests to define infrastructure and application behavior.
- **Scaling and Load Balancing**: Automatically scale applications and distribute traffic with Kubernetes Services.
- **ConfigMaps and Secrets**: Manage application configurations and sensitive data securely.
- **Monitoring and Logging**: Integrate basic tools to monitor and debug applications.

## Prerequisites
To get started, ensure you have the following tools installed:

- Kubernetes CLI (`kubectl`)
- Minikube, Kind, or any Kubernetes cluster
- Docker (for building and managing container images)

## Setup
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Simple_K8S.git
   cd Simple_K8S
   ```

2. **Start a Kubernetes Cluster**:
   Use Minikube or any Kubernetes provider to set up a cluster.
   ```bash
   minikube start
   ```

3. **Deploy Applications**:
   Apply the YAML manifests provided in the `manifests/` directory.
   ```bash
   kubectl apply -f manifests/
   ```

4. **Verify Deployments**:
   Check the status of your Pods, Services, and Deployments.
   ```bash
   kubectl get all
   ```

5. **Access the Application**:
   Use `kubectl port-forward` or access the application through the LoadBalancer/NodePort (depending on the Service configuration).
   ```bash
   kubectl port-forward svc/simple-service 8080:80
   ```

   ## Cleaning Up
To delete all resources created by this project, run:
```bash
kubectl delete -f manifests/
```

## Contribution
Contributions are welcome! Feel free to fork this repository and submit pull requests with improvements or new examples.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Happy Kubernetes-ing!
