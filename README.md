# Base configuration for kubernetes cluster with ansible playbooks
## Description
This method created for self-use with Yandex.Cloud infrastructure with two Ubuntu 20.04 LTS servers. For your self cases paths on servers may be difference of my. Check files/scripts and edit this before first play.

**Important:** First you need to be logged in all machines with uses in playbooks ssh-key for complete ssh auth.

## Installation
First steps:
1. Install anbible
2. Install git
3. Fork this repository
4. Clone your fork to local

## Next
Come into repository directory on your local machine and configure inventory/k8s-hosts/group_vars/all/hosts.yml file:
```yaml
# Fill the list of ip's. 
# If list contains more of one element - you can make duplicate of line.
ip_k8s_master: 
  - { ip: "public-ip-master", name: "k8s-master" }

ip_k8s_agent: 
  - { ip: "public-ip-agent", name: "k8s-agent" }
```
## Run
Run this command in your console.
```bash
ansible-playbook -i inventory/k8s-hosts -i inventory/k8s-master -i inventory/k8s-agent playbooks/k8s_setup.yml
```