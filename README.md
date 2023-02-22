# HelloKubernetes

Welcome to the HelloKubernetes repository! This is a beginner-friendly tutorial on deploying a simple `nginx` web server on a local Kubernetes cluster using the Kind container.

## Prerequisites

Before you can follow this tutorial, you'll need to have the following tools installed on your system:

- Docker: https://www.docker.com/
- kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/
- Kind: https://kind.sigs.k8s.io/docs/user/quick-start/

## Getting Started

To get started with the tutorial, follow these steps.

1. Create a local `kind` cluster with a single node:
```bash
kind create cluster --name hello-nginx
```

2. Clone this repository to your local machine
```bash
git clone https://github.com/HelloDevOpsWorld/HelloKubernetes.git
```

3. Navigate to the `hello-kubernetes/kind-nginx` directory
```bash
cd hello-kubernetes/kind-nginx
```

4. Deploy the `hello-nginx` application to your local cluster using the following command
```bash
kubectl create -f nginx.yaml
```

5. Verify that the application is running by accessing it from your web browser at http://<node-internal-ip>:<exposed-nginx-service-port>. 

To obtain the node internal IP address, you can run the following command:
```bash
kubectl get nodes -o wide
```

This will display the internal IP address of the Kubernetes node(s) in your cluster. Look for the IP address of the node where the Nginx deployment is running.

To obtain the exposed Nginx service port, you can run the following command:
```bash
kubectl get services
```

This will display the list of services running in your cluster. Look for the `nginx-service` service and note the value under the `PORT(S)` column for the `http` port. This is the exposed Nginx service port.

Once you have obtained the node internal IP address and the exposed Nginx service port, replace `<node-internal-ip>` and `<exposed-nginx-service-port>` in the URL with the respective values and enter the URL into your web browser to access the Nginx web server.


6. Deleting Your Deployment
When you're finished testing the `hello-nginx` deplyment, you can delete it and free up resources using the following command
```bash
kubectl delete deployment hello-nginx
``` 

## License
This project is licensed under the MIT License.