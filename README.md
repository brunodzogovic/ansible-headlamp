# Ansible Headlamp
Ansible playbooks for installing and cleanup of Headlamp in an existing k8s cluster. The playbook installs Headlamp in the `headlamp` namespace, uses a task to set a fixed IP for a load-balancer service. This can be overriden.

## Variables
Highest priority variables are located in `group_vars/k8s.yml`. The headlamp role includes defaults with variables with lower priority. It is possible to override the variables by passing `-e` in Ansible or by inserting a variable group in Ansible-Semaphore with values corresponding from the `group_vars/k8s.yml` file. 

## Headlamp management
1. Generate a token
   ```kubectl create token headlamp-admin -n kube-system```
2. Grant admin access to headlamp so it can control the clusters: 
```kubectl create clusterrolebinding headlamp-admin-crb \
  --clusterrole=cluster-admin \
  --serviceaccount kube-system:headlamp-admin
