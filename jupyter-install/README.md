# jupyter-install
Repository to install JupyterHub, Jupyter Lab and Enterprise Gateway on Kubernetes

# Requirements

You will need a driver machine with ansible installed and a clone of the current repository:

* If you are running on cloud (public/private network)
  * Install ansible on the edge node (with public ip)
* if you are running on private cloud (public network access to all nodes)
  * Install ansible on your laptop and drive the deployment from it

### Installing Ansible on RHEL

```
curl -O https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
sudo rpm -i epel-release-latest-7.noarch.rpm
sudo yum update -y
sudo yum install -y  ansible
```

### Installing Ansible on Mac

* Install Annaconda
* Use pip install ansible

```
pip install --upgrade ansible
```

### Updating Ansible configuration

In order to have variable overriding from host inventory, please add the following configuration into your ~/.ansible.cfg file

```
[defaults]
host_key_checking = False
hash_behaviour = merge
command_warnings = False
```

### Supported/Tested Platform

* RHEL 7.x
* Ansible 2.6.3


# Defining your Enterprise Gateway and JupyterHub deployment metadata (host inventory)

```
[all:vars]

[ingress]
tommy-kubeflow.us-south.containers.appdomain.cloud

[kernel_namespace]
kubeflow

[kernel_sa_name]
pipeline-runner
```

# Deploying Enterprise Gateway and JupyterHub

### Deployment playbook

### Deploying

```
ansible-playbook --verbose <deployment playbook.yml> -i <hosts inventory>
```

Example:

```
ansible-playbook --verbose setup-jupyterhub.yml -i kubernetes-settings
```
