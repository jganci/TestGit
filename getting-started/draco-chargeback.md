# Draco Chargeback
This page lists the chargeback cost for draco container services related resources.

# Chargeback for a container cluster
Here is a list of the key components of a container cluster that include chargeback:
* Worker node
* VLANs:  A container cluster includes a public and private VLAN consisting of a primary subnet of 16 IPs (13 usable) or 32 IPs (29 usable).  The IPs of the primary subnet are assigned by Bluemix for the K8S worker nodes.
* Public Portable Subnet: The IPs are used to apps or services deployed to the K8S cluster.
* Dedicated Hardware Firewall:  The firewall is required for each Public VLAN used by a container cluster.
* File Storage:
* Object storage: 

For example:
* Research customer requires container cluster for Cloud project with ability to scale between 2-10 worker nodes.
* Fixed cost: 
  * VLANs
  * Public Portable Subnet
  * Dedicated Hardware Firewall for VLAN
  * File storage for container cluster
  * Optional:  Object storage 
* Variable cost:
  * Worker nodes (3-10)



## Worker node
The key attributes that determine the cost of a K8S worker node in bluemix are the machine type (CPU, RAM), and quantity of workers.  Bluemix offers ability to deployed shared workers, however the RIS DevOps team only uses dedicated worker nodes.

| Machine Type | 2 CPU & 4 GB RAM | 4 CPU / 16 GB RAM | 16 CPU / 64 GB RAM  |32 CPU / 128 GB RAM | 56 CPU / 242 GB RAM |
|--------------| ----------------:|------------------:|--------------------:|-------------------:|--------------------:|
| Cost / hr:   | $0.34            | $0.54             | $1.34               | $2.29              | $3.71               |
| Cost / day:  | $8.04            | $12.87            | $32.18              | $54.90             | $89.09              |

## VLAN








