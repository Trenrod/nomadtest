# Provision VMs to a Nomad Cluster

Before you run it make sure the nomad cluster infrastructure ist already available.
If not checkout this [README.md](../infrastructure/README.md)

## Szenarios

### Prerequirements
```sh
# Create virtual environment for python
python -m venv .venv
# Activate it
source .venv/bin/activate
# Install all libs
pip install -r requirements.txt
```
```sh
# First run only ignore remote host identification check
export ANSIBLE_HOST_KEY_CHECKING=False
```
```sh
# After known_hosts are set remove env var
unset ANSIBLE_HOST_KEY_CHECKING
```

### Provision nomad cluster

```sh
# Installs nomad on all machines. Configures client and servers and install docker on all client machines.
.venv/bin/ansible-playbook create_initial_cluster.yaml  -i inventory/inventory.yaml
```