# Test infrastructure

Read (also all sub chapters) to understand:
 * [Vagrant Getting started](https://learn.hashicorp.com/collections/vagrant/getting-started)
 * [Vagrant Mutiple servers](https://www.vagrantup.com/docs/multi-machine)
 * [Vagrant networks](https://www.vagrantup.com/docs/networking)
 * [Helpful example](https://manski.net/2016/09/vagrant-multi-machine-tutorial/)

 ## What we are going to create

```plantuml

!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Deployment.puml

AddProperty("Datacenter ID", "Local")
AddProperty("VM ID", "NJ1")
AddProperty("Hostname", "nomad.dc1.nj1.jumpserver")
AddProperty("Private IP", "10.0.1.1")
Node(nomad, nomad_Jumpserver, ubuntu, "Orchestration via Nomad will be triggered from this VM")

AddProperty("Datacenter ID", "DC1")
AddProperty("VM ID", "VM1")
AddProperty("Hostname", "nomad.dc1.vm1.worker")
AddProperty("Private IP", "10.0.1.2")
Node(dc1_vm1, worker_dc1_vm1, ubuntu, "Worker VM1 of Datacenter1")

AddProperty("Datacenter ID", "DC1")
AddProperty("VM ID", "VM2")
AddProperty("Hostname", "nomad.dc1.vm2.worker")
AddProperty("Private IP", "10.0.1.3")
Node(dc1_vm2, worker_dc1_vm2, ubuntu, "Worker VM2 of Datacenter1")

AddProperty("Datacenter ID", "DC2")
AddProperty("VM ID", "VM1")
AddProperty("Hostname", "nomad.dc2.vm1.worker")
AddProperty("Private IP", "10.0.1.4")
Node(dc2_vm1, worker_dc2_vm1, ubuntu, "Worker VM1 of Datacenter2")

AddProperty("Datacenter ID", "DC2")
AddProperty("VM ID", "VM2")
AddProperty("Hostname", "nomad.dc2.vm2.worker")
AddProperty("Private IP", "10.0.1.5")
Node(dc2_vm2, worker_dc2_vm2, ubuntu, "Worker VM2 of Datacenter2")

Rel(nomad, dc1_vm1, "manages", "ssh")
Rel(nomad, dc1_vm2, "manages", "ssh")
Rel(nomad, dc2_vm1, "manages", "ssh")
Rel(nomad, dc2_vm2, "manages", "ssh")

```