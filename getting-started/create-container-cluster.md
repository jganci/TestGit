# Create Container Cluster
This document includes steps for a RIS DevOps admin to create a container cluster.


### Step 1: Create VLANs
Within Softlayer / Bluemix, you can create the public and private VLANs with primary subnet with following size:
* 8 (5 usable):  Web and cli
* 16 (13 usable) Web and cli
* 32 (29 usable) cli only

Key info needed:
* Name of cluster:  Name of cluster is used in vlan name
* Worker nodes: This is needed to ensure VLAN primary subnet size is large enough 
* Data center:  ie. DAL12 is only DC for CS at this time.

In following example, we are creating public and private VLANs with primary subnet of 32 IPs
for new container cluster:

Steps to create VLANs:
1. Create Public VLAN:
* bx sl vlan create -t public -d dal12 -s 32 -n ow-kube-dev-pub
2. Create Private VLAN:
* bx sl vlan create -t private -d dal12 -s 32 -n ow-kube-dev-prv
3. List VLANs after create
* bx sl vlan list | grep <name>
4. Verify router is correct


### Step 2: Create Dedicate Hardware Firewall


