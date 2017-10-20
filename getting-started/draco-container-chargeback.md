# Chargeback for RIS managed IBM Container Service
This document outlines the chargeback cost for the project "draco" RIS managed IBM Container Service.  The costs listed below are discounted from what is displayed in Bluemix directly.

There are two fundamental approaches for allocation of resource and chargeback:
* Shared container cluster
  * In this scenario, research customers request access to a shared container cluster with their own namespace and resource quota. The chargeback is done at the resource quota level for a given namespace.  Additional services such as object storage will be charge accordingly.  This is the preferred environment for most research customers seeking to deploy applications and services.  
* Dedicated container cluster
  * In this scenario, research customers require their own container cluster for Cloud related research. The chargeback for this model includes all components of the containter cluster (ie. vlans, subnet, firewall, storage, workers).  Justification and approval is needed for this environment.


## Chargeback for a shared container cluster
work in progress


## Chargeback for a dedicated container cluster
The chargeback for a research customer to have their own dedicated container cluster includes the cost of VLANs, Public portable subnet, dedicated hardware firewall for the public VLAN, K8S worker nodes, file storage, object storage.

For example:
* Research customer requires container cluster for Cloud project with ability to scale between 2-10 worker nodes.
* Fixed cost: 
  * VLANs - public and private
  * Public Portable Subnet 
  * Dedicated Hardware Firewall for public VLAN  
* Variable cost:
  * Worker nodes (2-10)
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


### VLANs
A container cluster includes a public and private VLAN consisting of a primary subnet of 16 IPs or 32 IPs for each VLAN.  The IPs of the primary subnet are managed by Bluemix and assigned to the K8S worker nodes at time of provisioning.

* VLAN Cost = $25 / mon
* Option of VLAN with 16 (13 usable) or 32 (29 usable) IP primary subnets

### Portable Public Subnet
The portable public subnet IPs are used by apps or services deployed to the K8S cluster.  Each subnet requires IPs reserved for gateway, broadcast and network thus subnet is always 3 IPs less than total.

|              | Subnet 8 IPs (5 usable) | Subnet 16 IPs (13 usable) | Subnet 32 IPs (29 usable) |
|-------------:|------------------------:|--------------------------:|--------------------------:|
| Cost / mon:  | $13.41                  | $26.81                    | $53.63                    |



### Dedicated Hardware Firewall
The firewall is required for each Public VLAN used by a container cluster.

* Dedicated Hardware Firewall = $585 / mon


### Object Storage
Object storage is optional to a container cluster and based on need of research customer apps / services use of object storage.


|                                    | Standard    | Vault      | Cold Vault | Flex       |
|-----------------------------------:| -----------:|-----------:|-----------:|-----------:|
| Capacity usage / GB:               | $0.0134     | $0.0073    | $0.0034    | $0.0054    |
| Bandwidth usage / GB:              | $0.0545     | $0.0545    | $0.0545    | $0.0545    |
| Class A operations / 1k requests:  | $0.0034     | $0.0075    | $0.0151    | $0.0061    |
| Class B operations / 10k requests: | $0.0134     | $0.0075    | $0.0151    | $0.0061    |
| Data Retrieval:                    | $0.0000     | $0.0061    | $0.0302    | $0.0176    |      
| Flex Max Cap                       | $0.0000     | $0.0000    | $0.0000    | $0.0176    |      

### File Storage
There are 3 types of File storage in Bluemix including: Endurance, Performance and NAS/FTP. Each has many possible values for sizes ranging from 20 GB - 12 TB (varies based on IOPS selected). For simplicity we have listed some common sizes as reference. Research customers can request each of the types of storage within the defined ranges via a Maximo ticket for cost estimate.

* Endurance: Includes selection of 4 different IPOS / GB (ie. .25, 2, 4, 10) + selection of storage GB size (ie. 100, 500, 1000, 2000, 5000).
* Performance: Includes selecting storage GB size in (ie. 100, 500, 1000, 2000, 5000) + entering IOPS value (100 - 6000) for DAL12.
* NAS: Includes only the selection of storage GB size (ie. 100, 500, 1000, 2000, 5000)


|                         | Endurance    | Performance | NAS         |
|-------------------------| ------------:|------------:|------------:|
| 2 IOPS / GB - 100 GB:   | $0.34        | $0.54       | $1.34       |




