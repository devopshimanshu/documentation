# VPC
VPC: Virtual Private Cloud provides networking for your cloud-based resources and services that is global, scalable and flexile.
VPC allow you to easily (virtually) expand your IP space.

VPC is divided into subnetworks called subnets. These subnets are hosted in Google Cloud data centers. Each subnet is assigned to a specific region.

Subnets can span multiple regions without ever communicating to the public internet

## VPC Topics:
- VPC
- Projects
- Networks
- Regions
- Zones
- Subnets
- Switching
- Routing
- Firewalls

GCP has 
- 29 regions
- 88 zones (three zones per region except US-Central1 region having 4 zones)
- 146 network edge locations

## Regions:
A region is a geographical region which is further devided into zones.

For example:

In the Americas, you have four regions, and each of these resign is bronken down into multiple zones:

Americas:
- Region: us-central1
    - Zone: us-central1-a
    - Zone: us-central-b
    - Zone: us-central-c
    - Zone: us-central-f

- Region: us-west1
    - Zone: us-west1-a
    - Zone: us-west1-b
    - Zone: us-west1-c

- Region: us-east1
    - Zone: us-east1-b
    - Zone: us-east1-c
    - Zone: us-east1-d

- Region: us-east4
    - Zone: us-east4-a
    - Zone: us-east4-b
    - Zone: us-east4-c

*Note:- Some of the resources in GCP are global and others are regional as well as zonal.*

Regional resources can be used anywhere within the same region.

Zonal resources can be used anywhere within the same zonal.

- Global Resources:
    - Images
    - Snapshots
    - VPC Network
    - Firewall
    - Routes

- Regional Resources:
    - Static external IP address
    - Subnets

- Zonal Resources:
    - Instances (VMs)
    - Persistent Disks

*We can attach a disk from one instance to another within the same zone, but I cannot do it cross the zones.*

*Since images and snapshotsre Global Resources, I can use these across zones in the same region.*

*In GCP we can add subnet when ever we needed. No need to create it once. Add subnet when ever is required*

## Why Region and zones?
 - High Availability
 - Fault Tolerance

Zones are independent of each other, with completely seperate physical infrastructure, networking, and isolated control plane that ensure typical failure events only affect that zone.

*Zones can share subnets but Regions can not share the subnet. But traffic can be routed internally to different regions within the same VPC and also firewall rules must be implemented for this.*


# Project:
A Project is really an organisational construct used for billing and permissions.

Its simply a way to organize resources from a billing and permissions prespective, and each project has its own VPC network(s) isolated from other projects in GCP.

*Default VPC is a global as it has subnets in all the regions.*

*Instance can communicate with each other internally using private Ip, But we can restrict this communication using firewall rules.*

*We can have upto 5 VPC in a single project. Don't worry it can be incereased by increasing a quota request.*

Multiple network within a single project provides:
 - Multi-tenancy
 - IP overlap
 - isolation within the project
 - Just another option instead of having multiple projects

## IP Address:
Every instance have internal as well as external Ip (external is optional).

Through internal Ip instance communicate with each others. 

External IPs are use to communicate with internat and other regions instances.

These IPs are ephmeral by default but can be statically assigned (IPs are released when instances deleted).

Internal IPs are allocated to instances from subnet's IP range via DHCP(Dynamic Host Configuration Protocol).

External IPs are also assigned via DHCP from some Google-provided pool.We can reserve static IPs addresses if needed.

External IPs can be global or regional for example a global static IP addresses are available or global forwarding rules used for gloabl load balanceing.

## Routes
All networks have routes in order to communicate with each other.

The default network has default routes to the internet and individual route to each subnet.

Routes are consider as "network resources" and con not be share between the projects or networks.

Traffic must match the route and firewall rule in order for it to pass.


## Firewalls
Firewall are the rules for the traffic, which allow or deny the traffic into and out of the network.

The firewall has an explicit-deny policy, meaning that any traffic taht needs to be permitted must have a rule created.

You can not create "DENY" rules, only "ALLOW" rules.

GCP is a full SDN(Software defined network)

Firewall rules are the network resource level and are not shared between projects and networks


## DNS Resolution
When an instance is created, DNS entry is automatically created resolving to a formatted hostname.

Synatx:
```
FQDN=[hostname].c.[project-id].internal

Example:
if 
projectName = tree
instanceName = porcupine

FQDN=porcupine.c.tree.internal
```

Resolution of this name s handled by n internal metadata server at acts as a DNS resolver (169.254.169.254), provided as a part of Google Compute Engine (GCE).

For routing to external we need to use Google Cloud DNS.

## Network Billing

Google changes only for egress traffic only

Egress traffic is consider as:
 - traffic to internet.
 - from one region to another (in the same network)
 - between zones within the region

## Some limitations:
- VPC network only support IPv4 unicast traffic (no IPv6 , or broadcast/multicast)
- Maximum of 7000 VM instance per VPC network.


# At Glance

What is Multi-Tenancy?








# Refence Urls
[GCP 101: Understanding Google Cloud VPC](https://www.onixnet.com/insights/google-cloud-vpc)

[Google Cloud Platform (GCP) Networking Fundamentals](https://www.networkmanagementsoftware.com/google-cloud-platform-gcp-networking-fundamentals/#wbounce-modal)
