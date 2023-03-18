# Commands - Project Setup

Before starting, make sure that the Docker daemon is running and your ports are not being used by other applications.

## Start Minikube and Check the Status

```powershell
minikube start
minikube status
```

## Create Deployments

Choose the appropriate deployment file based on your system:

### Apple Silicon Macbook
```powershell
kubectl create -f deployment-apple-silicon.yml -n devldx
```

### Windows 11

```powershell
kubectl create -f deployment-windows11.yml -n devldx
```

## Get Information on Deployments, Services, and Pods

```powershell
kubectl get deployments  -n devldx
kubectl get services  -n devldx
kubectl get pods  -n devldx
```

Alternatively, you can execute all three commands at once:

```powershell
kubectl get deployments  -n devldx ; kubectl get services  -n devldx ; kubectl get pods  -n devldx
```

# Start the Services

Use the following commands to start the services and map the internal ports to your local machine. Note that these commands should remain running, so do not close the terminal windows. For production environments, consider using a cloud service provider with DNS or LoadBalancer configurations for enhanced security.

## Forward Ports with kubectl

In one terminal, execute the following command (do not close the window):

```powershell
kubectl port-forward service/spring-boot-backend-rest-service 8080:8080 -n devldx
```

In another terminal, execute the following command (do not close the window):

```powershell
kubectl port-forward service/react-front-end-service 3000:80 -n devldx
```

# Get the IP address

```powershell
minikube ip
```

## Clean Up

To delete all deployments, services, and the namespace, run the following commands:

```powershell
kubectl delete deployments --all -n devldx
kubectl delete services --all -n devldx
kubectl delete namespace devldx
```
