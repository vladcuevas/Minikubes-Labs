# Ingress

1. Run Minikube Locally

minikube start

2. Enable the Ingress controller, in this case NGINX

minikube addons enable ingress

3. Verify that the NGINX Ingress controller is running

> kubectl get pods -n ingress-nginx
NAME                                        READY   STATUS      RESTARTS   AGE
ingress-nginx-admission-create-t95tq        0/1     Completed   0          44s
ingress-nginx-admission-patch-fn5l2         0/1     Completed   1          44s
ingress-nginx-controller-755dfbfc65-2qpw5   1/1     Running     0          44s