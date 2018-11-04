# Install Kubernetes
This is an ansible script to deploy kubernetes on bare-metal servers. Kubernetes will be installed using the kubeadm tool. This means that all kubernetes services will be running in docker containers.

## Prerequisites
* All nodes running Ubuntu 16.04+.
* Nodes networking should be configured.
* The nodes can be accessed with the same SSH key.
* Ansible 2.3.

The following should be run on a jumpbox:
~~~
git clone https://github.com/miguelcastilho/kube-inst.git
cd kube-inst
~~~

## Files to update with environment configuration
Copy the example files for update
~~~
cp hosts.example hosts
cp ansible.cfg.example ansible.cfg
cp groupvars/all.example groupvars/all
~~~

 * ./hosts: change ip and host names
 * ./ansible.cfg: change path to ssh_key to connect to all hosts
 * ./groupvars/all: adapt all variables to the environment

## How to deploy Kubernetes:
~~~
ansible-playbook -i hosts deploy.yml
~~~

### Supported networks
The networking plugin can be specified in the ```./groupvars/all``` file.
* Flannel

### Included addons
The addons can be enabled or disabled individually in the ```./groupvars/all``` file.
* Grafana, Heapster and InfluxDB
* Helm
* Dashboard
* Demo app
* Federation control plane
* Traefik ingress
