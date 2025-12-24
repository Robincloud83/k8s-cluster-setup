# k8s-cluster-setup
# helm installations
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
##  Installing Argo CD

- Create a namespace for Argo CD:
  ```bash
  kubectl create namespace argocd
  ```

- Apply the Argo CD manifest:
  ```bash
  kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
  ```

- Check services in Argo CD namespace:
  ```bash
  kubectl get svc -n argocd
  ```

- Expose Argo CD server using NodePort:
  ```bash
  kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
  ```

- Forward ports to access Argo CD server:
  ```bash
  kubectl port-forward -n argocd service/argocd-server 8443:443 &
  ```
