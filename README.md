# vagrant_leaf_spine

## What is it?
1. This is a project that allows the user to build multiple topologies based on the diagram below
2. This project utilizes Vagrant, vEOS, VirtualBox and python to build the topologies
3. The topologies that are supported: 
    1. L3LS w/BGP
    2. Assymmetric EVPN w/VXLAN
    3. Multicast

![alt text](https://github.com/mtharpie/vagrant_leaf_spine/blob/master/images/vagrant-leaf-spine.png)

## Why use this?
1. Get hands on training on Arista's EOS
2. Easy to build next-generation topologies for the datacenter

## How it works?
1. Uses jsonrpclib to provision the configurations (stored in configs folder)
2. topology defined in vagrant
3. uses vEOS and CentOS7 virtualbox.box images for topology

## Requirements / Setup
1. Decent amount of RAM and a CPU that supports multithreading
    1. 12+GB RAM
    2. 8 vCPUs
2. Install Vagrant 2.0 for CentOS7
```
arista@labnuc:~$ yum install vagrant_2.0.0_x86_64.rpm
```
3. Install VirtualBox 5.2 for CentOS7
```
arista@labnuc:~$ yum install VirtualBox-5.2-5.2.0_118431_el7-1.x86_64.rpm
```
4. Download vEOS Box image for 4.20.5.2F from https://www.arista.com/en/support/software-download
    1. Create account on https://www.arista.com/en/user-registration
    2. Download vEOS box
5. Install jsonrpclib python library
```
arista@labnuc:~$ sudo pip install jsonrpclib
```
6. git clone project
```
arista@labnuc:~$ git clone https://github.com/tharpie/vagrant_leaf_spine.git
```
7. Add virtual box images
```
arista@labnuc:~$ vagrant box add vEOS-lab-4.20.5.2F-virtualbox.box --name 'vEOS-4.20.5.2F'
arista@labnuc:~$ vagrant box add CentOS-7-x86_64-Vagrant-1804_02.VirtualBox.box --name 'centos7'
```
8. Start environment
```
arista@labnuc:~$ vagrant up
## This can take a while...
```
9. Provision environment based on environment
```
arista@labnuc:~$ python provision-topology.py -h
Help Menu
---------------------
valid toplogies are bgp, evpn, mcast, her

Please use the following usage:
python provision-topology.py [topology_name]

```
