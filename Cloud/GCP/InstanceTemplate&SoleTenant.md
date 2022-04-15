# VM Instance 

# Instance Templates
An instance template is a resource that can be use to create virtual machine (VM) instance or Managed Instance Groups (MIG).

Instance Templates defines:
- Machine Type
- Boot Disk Image / container Image
- Labels
- startUp scripts
- Other instance properties.

Best way to save the configuration for an indiviual instance or Managed Instance Group.
Instance Templates are a convenient way to save a VM instance's configuration so you can se it later to create VMs or a group of VMs.

Instance Templates are the **Global Resource**. But if we define any zonal resource say we used an persistant disk which is in us-central1-a then template becomes zonal and can not be used in any other zone.

Label are not for templates they will be applied to all the instances which are created using these templates.

## When to use Instance templates:
 - preexisting configuration instance
 - Create a group of idential instance

 We need to create a template which managed group instance use to create instances.

Always set explicit properties in your template that reflect exact onfiguration hat you want.

## Pricing:
There is no additional charges for instance template. You are charged for the resources that you create based on he template.


## Limitations:
You can not edit the existing instance template or change an instance template after it has been created.

If an instance template goes out-of-date, or you need to make the changes in instance templates, create a new instance template.

## Creating an Instance Template
While creating we need to efine:
 - Machine Type
 - Boot disk
 - Image
 - VPC network
 - IP Address

- **Optional**

Security> Sheilded VM
 - **Secure Boot:** It helps protect your VM against boot-level and kernal level malware and rootkits.
 - **vTPM:** Virtual Trusted Platform Modulevalidates your guest VM pre-boot and boot integrety, and offers key generation and protection.
 - **Integerated Monitoring:** Lets you monitor and verify the runtime boot integerity of your shield VM instance using Stackdriver reports. Require vTPM to be enable.

**Firewall option:**
 - http traffic
 - https traffic

**Disks:**

 we can attach upto 15 non boot disk

## Deterministic instance templates:
It consist of determined values in the templates.


# Managed Instance Group
A managed instance group (MIG) is a group of virtual machine (VM) instance that are treated a single entitiy.

These instance are grouped together there is a provision to create number of instances but not linked together for those look **Bulk instance API**

There are several cases for designing MIG such as:
- Single zone
- Multi Zone
- Autoscaling
- Preemptible VMs
- With stateful configurations

## Single Zone MIG:
These single zone Managed Instance Groups are also known as zonal MIG.

To create a managed Instance group in a single zone we need to provide the below details
 - Name
 - Description (optional)
 - Instance template
 - Number of Instance
 - Location (Single zone)
 - Select Region & zone
 - Autoscaling
    - Autoscaling mode (add & remove instance)
    - Minimum number of instance
    - Maximum number of instance
    - AutoScaling metrics
        - CPU Utilization 
        - Rest we can add
    - Cool down period
 - AutoHealing
 - Port Mapping

## Multi Zone MIG:
These multi zone Managed Instance Groups are also called as Regional MIG. As they are spread over mutliple zones in a region.

To craete a Managed Instance Group in multi zone we need to provide the below details
 - Name
 - Description (optional)
 - Instance template
 - Number of Instance
 - Location (Multiple zone)
 - Select single Region with all zones
 - Target Distribution shape 
    - Even {Distribute evenly across the zones}
    - Balanced {Distribute as evenly as possible as per the availablity of resouces in the zone}
    - Any {Deploy the instance in one or more zone as per avialablity of resources}
 - Autoscaling
    - Autoscaling mode (add & remove instance)
    - Minimum number of instance
    - Maximum number of instance
    - AutoScaling metrics
        - CPU Utilization 
        - Rest we can add
    - Cool down period
 - AutoHealing
 - Port Mapping

## Autoscaling:
It adds or removes the VM automatically from the group as per the CPU utlization (Default criteria).

It is already discussed and provissioned in the above types.

## Preemptible VMs:
Preemptible VM are the userful if your workload can tolerate disruptions and you want to take advantage of the cost-saving associated with preemptible VMs.

For this MIG we need to setup option while creating Instance template.
We just need to select preemptibility to On under management section.

Create Instance Template > Management > Availability policy > preemptibility > On

By Default its set to Off

## Stateful:
Preserve the data on the disk with a given name for all the MIG's VMs, even in the event of VM recreations.

### Best Practise:
Instead of Stateful use a persistent disk and keep your VMs stateless.

To create a stateful VM MIG we need to select stateful option present on the left drawer of the google console and remaining part is same as the above.

## Limitations for Stateful:
- We can not use autoscaling if MIG are set for stateful.
- If we need to use the automated rollout updates, we must set the **replacement method** to **RECREATE**.
- We must disable proactive redistribution to prevent deletion of stateful instances by automatic cross-zone redistribution.



# Sole-tenant-nodes:
Sole Tenant Node is a server on which only we can create VMs.

These are the physical server on which your own VMs are hosted no one else can host.

Sole-tenant lets you have exclusive access to  a sole-tenant node, which is a physical Compute Engine server that is dedicated to hosting only your projects VMs.

Use Sole-tenant nodes to keep your VMs physically seperated from VMs in other projects, or to group your VMs together on the same ost hardware.





# Reference:
[Instance templates](https://cloud.google.com/compute/docs/instance-templates)

[Create instance templates ](https://cloud.google.com/compute/docs/instance-templates/create-instance-templates)

[Sole-Tenant Node](https://cloud.google.com/compute/docs/nodes/sole-tenant-nodes)
