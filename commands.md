Before starting make sure that Docker daemon is running
Make sure that your ports are not being used by other applications

## Start the Minikube and Check the Status

```powershell
minikube start
minikube status
```

## Create Deployments

If using Macbook with Apple Silicon Chip:
```powershell
kubectl create -f deployment-apple-silicon.yml -n devldx
```

If using Windows11:
```powershell
kubectl create -f deployment-windows11.yml -n devldx
```

## Get information of our deployments, services
```powershell
kubectl get deployments  -n devldx
kubectl get services  -n devldx
kubectl get pods  -n devldx
```

OR:

```powershell
kubectl get deployments  -n devldx ; kubectl get services  -n devldx ; kubectl get pods  -n devldx
```

# Start the services

With this commands we can start our services mapping the internal ports to whatever we need in the loca machine, in case we need to define something more robust, we can do so for a Cloud service provider with DSNs or some LoadBalancer structure, and with more security, these two commands most stay running, you cannot close the terminal window in Windows, if you can use nohup, you can run it with that but the purpose of this is not production by any means.

## Use kubectl to forward the port:

In one terminal execute the below command (do not close the windows):

```powershell
kubectl port-forward service/spring-boot-backend-rest-service 8080:8080 -n devldx
```

In another terminal execute the below command (do not close the window)

```powershell
kubectl port-forward service/react-front-end-service 3000:80 -n devldx
```

# Get the IP address

```powershell
minikube ip
```

## Delete all

```powershell
kubectl delete deployments --all -n devldx
kubectl delete services --all -n devldx
kubectl delete namespace devldx
```
