# ansible-headlamp
Ansible playbooks for installing Headlamp in an existing k8s cluster. 

## Headlamp management
Grant admin access to headlamp so it can control the clusters: 
```kubectl create clusterrolebinding headlamp-admin-crb \
  --clusterrole=cluster-admin \
  --serviceaccount kube-system:headlamp-admin```
