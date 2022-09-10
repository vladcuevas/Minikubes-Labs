## Create Deployments and Ingress
minikube addons enable ingress
kubectl create -f deployment-apple-silicon.yml -n devldx

## Get information of our deployments, services and ingress
kubectl get deployments  -n devldx
kubectl get services  -n devldx
kubectl get ingress  -n devldx

# Start the services
If you want to avoid waisting time, do not try the below two lines of command, go directly to the next step where we have more control of the ports.

minikube service react-front-end-service -n devldx
minikube service spring-boot-backend-rest-service -n devldx

With this commands we can start our services mapping the internal ports to whatever we need in the loca machine, in case we need to define something more robust, we can do so for a Cloud service provider with DSNs or some LoadBalancer structure, and with more security, these two commands most stay running, you cannot close the terminal window in Windows, if you can use nohup, you can run it with that but the purpose of this is not production by any means.

In one terminal execute the below command (do not close the windows):
kubectl port-forward service/spring-boot-backend-rest-service 8080:8080 -n devldx

In another terminal execute the below command (do not close the window)
kubectl port-forward service/react-front-end-service 3000:80 -n devldx

# Get the IP address
minikube ip

## Delete all
kubectl delete deployments --all -n devldx
kubectl delete services --all -n devldx
kubectl delete ingress --all -n devldx
kubectl delete namespace devldx