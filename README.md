### This is a follow-along project of 

[Youtube: ArgoCD Tutorial for Beginners | GitOps CD for Kubernetes](https://www.youtube.com/watch?v=MeU5_k9ssrs)<br />
[Source: GitLab](https://gitlab.com/nanuchi/argocd-app-config)<br />
[ArgoCD Doc](https://argo-cd.readthedocs.io/en/stable/getting_started/)<br />
[ArgoCD Declarative Setup Example](https://argo-cd.readthedocs.io/en/stable/getting_started/)<br />

```bash
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

# you can change and delete init password
```

### Configure GitHub or other Git repo connection:
![image](https://github.com/phl6/argocd-config-demo/assets/43781029/4b9875b3-a333-4822-8fd1-d51c4a3c5453)

If successful, the status will change and a new secret is added to the namespace
![image](https://github.com/phl6/argocd-config-demo/assets/43781029/d7401a2a-4599-4d21-96af-c04524207d96)
![image](https://github.com/phl6/argocd-config-demo/assets/43781029/e1397847-9022-4497-8b7a-5bd05c583937)
