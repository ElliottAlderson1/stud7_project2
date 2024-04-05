## Virtualization
Break connection between hardware and the OS. Dynamic resources, utilize more hardware.

- Server Virtualization - allows more than one server on a machines
- Network Virtualization - recreates physical networks, can communicate data across remote locations
- Desktop Virtualization - access computer without hardware in front of you

#### Physical v. Virtual
Physical is known as bare-metal, single tenant. 
Hardware <-> OS

Legacy server had an OS with software applications installed on top.

- Performance: Physical is faster
- Management: VM is easier
- Portability: VM is easier
- Scalability: VM is easier
- Capacity Management - Physical does not use maximum level of hardware, VM optimizes
- System recovery: Easier to recover with VM backups
- Business Continuity: VM are more fault tolerant
- Security: Can use universal configs on VM
- Cost: VM easier to manage in large services for optimization

A virtual machine is a software computer, OS sees consistent hardware regardless of physical hardware.

#### Hypervisor
### **Type 1** - Bare Metal or Native
Very Secure, no vulnerability of underlying OS, and less latency than Type 2.
- Hardware <-> Hypervisor <-> OS
- KVM
- RHEV
- Xen
-Microsoft Hyper-V
- VMware vSphere
- Oracle VM Server

**Type 2** - Hosted Hypervisors
- Hardware <-> OS <-> Hypervisor <-> OS
- Oracle VM virtualbox
- VMware Workstation Pro
- Parallel Desktop for MAC
- Windows virtual PC

#### Virtual Machine
A software computer. Consolidation of the OS and its applications. It has all the elements of a physical device. an OS on a virtual machine is called a **guest OS**. Can create vNIC to pair to physical switches.

In vSphere, virtual machines run on hosts or clusters.

Multiple VMs can run on the same host or cluster at the same time.

#### Benefits
- Consolidating many physical servers into one reduces energy
- Easy to relocate
- Independent of physical hardware
- Isolated from other VM
- Support legacy apps
- CPU virtualization is NOT emulation - only allocation of resources
- Reduced Energy

## VMware vSphere
There are two core components of vSphere are VMware ESXi and VMware vCenter Server.
- VMwar ESXi is the core hypervisor - host
- Contsins Managed hosts and virtual machine, vSphere clients
#### ESXi
Software a host runs as a hypervisor. Adding a host to vCenter Server lets you manage it.
#### vCenter Server

1. Infrastructure Services
- vCompute
- vStorage
- vNetwork
2. Application Services
- High Availability
- Distributed Resource Scheduler DRS
- Fault Tolerance
3. VMware vCenter Server - management and control pane
4. Clients - users that consume vSphere datacenter

#### vSphere Web Client
manage and monitor virtual machines. You can install on a Windows machines, can access on Web browser.

Host client is on host. vSphere Client is on the vCenter Appliance0

## Datastore
Logical container holding VM files and other necessary files for machine ops. Can be VMFS or NFS based. Go to vCenter > Datastores
- VMFS (version 5 or 6)
- NFS (3 and 4.1)
- vSAN
- Virtual Volumes


## Networking in vSphere
Two types of architecture

1. **vSphere Distributed Switches** manage vm at data center level

2. **Standard switches** manages virtual machine and host networking as host level. Works at the layer 2. Created by default. Between VM and ESXi hosts, between VM on network, between VM and Physical Machines. No license required.

#### vSphere Standard Switch Connection
Can enable two types of network in ESXi
1. Standard Ports Group
    - One or more physical adapter
    - Provide network connectivity to VM
2. VMkernel Adapter
    - Provides network connectivity for IP storage
    - VMware FT, and the ESXi management network

## Virtual Disk Provisioning
Three Types of Virtual Disks
### 1. Thick Provision Lazy Zeroed (Default)
All the space required for Virtual Disk is allocated during creation. The space is **zeroed on the first command**. Consumes all 10 GB if its a 10 GB disk. 
- Advantages: Fast Creation, All space allocated up front.
- Disadvantage: performance on first command write (needs zerps) does not allow for over provisioning of storage
### 2. Thick Provision Eager Zeroed
Space is allocated during creation. **Space is Zeroed** on creation too. Offers best performance, but takes longer to provision.
- Advantages: **highest performance**, all space allocated in advance, most secure option
- Disadvantages: longest creation time, does not allow for over provisioning
### 3. Thin Provision
As much space as needed.
- Advantages: fastest creation, and over-provisioning of storage.
- Disadvantages: highest performance penalty on first write, need storage capacity management to be in place to stay.




