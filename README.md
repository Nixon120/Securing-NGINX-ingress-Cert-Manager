
Securing-NGINX-ingress-Cert-Manager


Step 1 - Install Helm
$ brew install kubernetes-helm


Step 2 - Deploy the NGINX Ingress Controller
$ helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
$ helm repo update

Step 3 - Use helm to install an NGINX Ingress controller:

$ helm install quickstart ingress-nginx/ingress-nginx


It can take a minute or two for the cloud provider to provide and link a public IP address. When it is complete, you can see the external IP address using the kubectl command

$ kubectl get svc
NAME                                            TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)                      AGE
kubernetes                                      ClusterIP      10.0.0.1       <none>        443/TCP                      13m
quickstart-ingress-nginx-controller             LoadBalancer   10.0.114.241   <pending>     80:31635/TCP,443:30062/TCP   8m16s
quickstart-ingress-nginx-controller-admission   ClusterIP      10.0.188.24    <none>        443/TCP                      8m16s

Step 4 - Assign a DNS name

The external IP that is allocated to the ingress-controller is the IP to which all incoming traffic should be routed. To enable this, add it to a DNS zone you control, for example as www.example.com.

This quick-start assumes you know how to assign a DNS entry to an IP address and will do so.

Step 5 - Deploy an Example Service
kubectl apply -f https://raw.githubusercontent.com/cert-manager/website/master/content/docs/tutorials/acme/example/deployment.yaml
kubectl apply -f https://raw.githubusercontent.com/cert-manager/website/master/content/docs/tutorials/acme/example/service.yaml
kubectl create --edit -f https://raw.githubusercontent.com/cert-manager/website/master/content/docs/tutorials/acme/example/ingress.yaml


Step 6 - Deploy cert-manager
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.9.1/cert-manager.yaml










