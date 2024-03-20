# Run Kubernetes on Portainer 

**Install Minikube:**

Visit the Minikube releases page and download the appropriate installer for your OS.
Follow the installation instructions specific to your operating system from the Minikube Start Guide.


**Start Minikube:**

Open a terminal or command prompt.


* Run the command: `minikube start`
  
This command sets up a single-node Kubernetes cluster running inside a VM on your machine.


**Installing and Configuring kubectl**

* Install kubectl:

**macOS/Linux:** You can use package managers like Homebrew on macOS (brew install kubectl) or apt/yum on Linux.

**Windows:** You can download the binary from the Kubernetes release page or use Chocolatey (choco install kubernetes-cli).
Detailed instructions are available in the Kubernetes documentation.

* Configure kubectl to Connect to Your Cluster:

**Minikube:** kubectl is automatically configured to communicate with the Minikube cluster after `minikube start`.

**Cloud Provider:**
Typically, after creating a cluster, the cloud provider will offer a way to download a configuration file (often called kubeconfig).
Place this file in your ~/.kube directory (create it if it doesn't exist) and name it config or merge it with an existing config file if one exists.
Alternatively, you can set the KUBECONFIG environment variable to point to your kubeconfig file.


**Verifying the Setup**


Open a Terminal or Command Prompt.

* Run `kubectl version`:

This command shows the version of kubectl and details of the cluster it's connected to. It verifies that kubectl is properly installed and configured.
Run `kubectl get nodes`:

This command lists the nodes in your cluster, indicating that kubectl can communicate with your Kubernetes cluster.


**Deploying Portainer for Kubernetes:**


```
kubectl apply -n portainer -f https://raw.githubusercontent.com/excel-azmin/hello-k8s/master/portaienr/portainer-nodeport.yaml
```

**Access Portainer:**

* `kubectl get svc -n portainer`
* `kubectl -n portainer get service portainer`
* `minikube service list`
* `minikube service list -n portainer`
* `minikube service portainer -n portainer`


 **Verify Pod and Service Status**

 * `kubectl get -n portainer pods`
 * `kubectl -n portainer get service portainer`

**Restarting Portainer**

* Identify the Portainer Pod : `kubectl get pods -n portainer`
* Delete the Portainer Pod : `kubectl delete pod -n portainer <portainer-pod-name>`
* Deploye the Portainer : `kubectl apply -n portainer -f portainer-nodeport.yaml`
* Accessing Portainer Again : `minikube service portainer -n portainer`


