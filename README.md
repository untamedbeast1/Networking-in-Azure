# Networking-in-Azure
Creating a simplen Virtual netrwork on azure and attaching resources to it.

We live in todays world where even a microwave has an IP address, the internet of things has shed a spot light on the importance of IP address hence the development of the IPV6. When subnetting a typical IP address using a CIDR notation the first and last address is reserved for the network addrss and the Broadcast address.
Let take for instance a Typical subnet 192.168.10.0 /29 this gives a total of 8 ip subnets 2 would be used for network address and broadcast address(192.168.10.0 and 192.168.10.8)


<img width="852" alt="Screenshot 2022-02-06 at 12 46 07" src="https://user-images.githubusercontent.com/55625732/152681413-d510bcef-fd06-4f6c-b8c0-5be7fca17802.png">

However when networking in azure, Azure reserves 5 IP : Network and broadcast IP address, 2 for DNS and 1 for the NIC of the virtual network that is created.
so subnetting this IP above on azure only 3 IP address would be available.

A virtual machine or a resource needs to be attached to a subscription> a resource group> a Network security Group> a virtual network

This is just a brief step by step way of creating a virtual resource to it, for instance a vrtual machine or sql instance.

First you would neeed to have a subscription and createw a resurce group 

Here I create a virtual network and attach resources like virtual machines to it.

Creating a network for your 

Network group filters traffic in and out
Virtual network.  (subnetting is managed here)
Virtual IP

