# Nomad Test 

This project is a PoC to setup multiple services over multiple datacenters having each 2 VM`s.
For simplicity we will use a local emulation of multiple datacenters using Vagrant and Virtualbox.

Enjoy.

## Create local test infrastructure

Install, setup and doc -> [README.md](infrastructure/README.md)

Fast path:
 * Replace in the vagrant/Vagrantfile the name of the bridged network to use which you use to connection to the internet. You can check available network adapter names with 
    ```sh
    C:\Program Files\Oracle\VirtualBox>VBoxManage.exe list bridgedifs
    ```
 * Execute
    ```sh
    cd vagrant
    vagrant up
    ```

## Provision local test infrastructure

Install, setup and doc -> [README.md](infrastructure/README.md)

Fast path:
 * on windows
    ```sh
    cd ansible
    python -m venv .venv
    source .venv/bin/activate
    pip i -r requirements.txt
    ansible-playbook provision-all.yaml -i inventory/inventory.yaml
    ```

 * on linux
    ```sh
    cd ansible
    python -m venv .venv
    .venv/Scripts/activate
    pip i -r requirements.txt
    ansible-playbook provision-all.yaml -i inventory/inventory.yaml
    ```

## TODO Add Loadbalancer

## TODO Add Ingress and Egress

## TODO Write container to handle tls certificates
