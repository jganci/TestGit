# Draco Chargeback
This document outlines the chargeback cost for draco container services managed by the RIS DevOps team.

There are two fundamental approaches for allocation of resource and chargeback:
* Shared container cluster
  * In this scenario, research customers request access to a shared container cluster with there own namespace and resource quota. The chargeback is done at the resource quata level for a given namespace.  Additional services such as object storage will be charge accordingly.  This is the preferred environment for most research customers seeking to deploy applications and services.  
* Dedicated container cluster
  * In this scenario, research customers require their own container cluster for Cloud related research. The chargeback for this model includes all components of the containter cluster (ie. vlans, subnet, firewall, storage, workers).


# Chargeback for a container cluster
Here is a list of the key components of a container cluster that include chargeback:
* Fixed cost: 
* Worker node
* VLANs
* Public Portable Subnet

For example:
* Research customer requires container cluster for Cloud project with ability to scale between 2-10 worker nodes.
* Fixed cost: 
  * VLANs
  * Public Portable Subnet
  * Dedicated Hardware Firewall for VLAN
  * File storage for container cluster
* Variable cost:
  * Worker nodes (3-10)
* Optional:
  * Object storage
  * File storage


### Worker node
The key attributes that determine the cost of a K8S worker node in Bluemix are the machine type (CPU, RAM), and quantity of workers.  Bluemix offers ability to deployed shared workers, however the RIS DevOps team only uses dedicated worker nodes.

| Machine Type | 2 CPU & 4 GB RAM | 4 CPU / 16 GB RAM | 16 CPU / 64 GB RAM  |32 CPU / 128 GB RAM | 56 CPU / 242 GB RAM |
|--------------| ----------------:|------------------:|--------------------:|-------------------:|--------------------:|
| Cost / hr:   | $0.34            | $0.54             | $1.34               | $2.29              | $3.71               |
| Cost / day:  | $8.04            | $12.87            | $32.18              | $54.90             | $89.09              |
| Cost / mon:  | $244.68          | $391.48           | $978.70             | $1669.91           | $2709.79            |


### VLAN
A container cluster includes a public and private VLAN consisting of a primary subnet of 16 IPs or 32 IPs for each VLAN.  The IPs of the primary subnet are managed by Bluemix and assigned to the K8S worker nodes at time of provisioning.

* VLAN Cost = $25 
* Option of VLAN with 16 (13 usable) or 32 (29 usable) IP primary subnets

### Portable Public Subnet
The portable public subnet IPs are used by apps or services deployed to the K8S cluster.  Each subnet requires IPs reserved for gateway, broadcast and network thus subnet is always 3 IPs less than total.

|              | Subnet 8 IPs (5 usable) | Subnet 16 IPs (13 usable) | Subnet 32 IPs (29 usable) |
|-------------:|------------------------:|--------------------------:|--------------------------:|
| Cost / mon:  | $13.41                  | $26.81                    | $53.63                    |



### Dedicated Hardware Firewall
The firewall is required for each Public VLAN used by a container cluster.



### Object Storage


### File Storage 



