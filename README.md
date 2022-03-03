# Networking-in-Azure
Just as the title implies this is an implementation of creating a virtual network on azure and attaching resources to it. 
We live in a world where even a microwave has an IP address, the internet of things has shed a spot light on the importance of IP address hence the development of the IPV6. When subnetting a typical IP address using a CIDR notation the first and last address is reserved for the network addrss and the Broadcast address.
Let take for instance a Typical subnet 192.168.10.0 /29 this gives a total of 8 ip subnets 2 would be used for network address and broadcast address(192.168.10.0 and 192.168.10.8)


<img width="852" alt="Screenshot 2022-02-06 at 12 46 07" src="https://user-images.githubusercontent.com/55625732/152681413-d510bcef-fd06-4f6c-b8c0-5be7fca17802.png">

However when networking in azure, Azure reserves 5 IP : Network and broadcast IP address, 2 for DNS and 1 for the NIC of the virtual network that is created.
so subnetting this IP above on azure only 3 IP address would be available or assignable.

A virtual machine or a resource needs to be attached to a subscription> a resource group> a Network security Group> a virtual network

** Note that when creating a resource it is automatically attached to a virtual network and a virtual group, however due to personal preference you can create your 
own virtual network and assign you own private IP addressing***

There are several ways of creating a virtual network
one way is to simply click the virtual network on the azure services tab
<img width="966" alt="Screenshot 2022-02-24 at 16 46 30" src="https://user-images.githubusercontent.com/55625732/155572700-b7d180ca-8a75-4ab4-8d3a-e7ae6598e1b7.png">

A second way is to use the search bar to look for virtual networks

<img width="1094" alt="Screenshot 2022-02-24 at 17 10 59" src="https://user-images.githubusercontent.com/55625732/155573292-36614887-bab6-4111-bec5-968b540953d9.png">

The other could also be create the resource directly, azure would will further prompt you to create a virtual network.
The Azure CLI can be used also to create a Virtual network, Kindly scroll to the both to find out how.

Having clicked on virtual network, select create virtual network. 

<img width="800" alt="Screenshot 2022-02-24 at 17 15 24" src="https://user-images.githubusercontent.com/55625732/155573971-5051a0f6-3514-49e9-a383-585c702404b8.png">

Azure gives a default private IP address, however this can be customized and you can select you own private ip to use.
Here, an IP address of 192.168.10.0 /29 is used


<img width="899" alt="Screenshot 2022-02-24 at 17 16 30" src="https://user-images.githubusercontent.com/55625732/155574133-99c68717-e06d-40da-9cf1-b1d3e10188bf.png">


++
Name the subnet to be used for the selected ip address


<img width="305" alt="Screenshot 2022-02-24 at 17 19 19" src="https://user-images.githubusercontent.com/55625732/155574756-4c421e35-67f6-4258-80f7-fca126f08603.png">

Viola you IP address is added to column
<img width="918" alt="Screenshot 2022-02-24 at 17 19 36" src="https://user-images.githubusercontent.com/55625732/155574789-d2d4eefe-c701-4cd4-96af-f8793acdb983.png">

** Please bear in mind that to use the virtual network the resource created has to also be in the same regoin as the virtual network**

So when creating a virtual resource like windows server or ubuntu you can attach it to the already created virtual network.

<img width="998" alt="Screenshot 2022-02-24 at 17 26 17" src="https://user-images.githubusercontent.com/55625732/155575808-9818b8e2-ab3a-443f-9018-4fd1de155a26.png">


USING THE AZURE CLI TO CREATE VIRTUAL NETWORKS

As a prequiste download the Azure Cli to the host machine you intend to use, refer to the documentation on how to insall this

https://docs.microsoft.com/en-us/cli/azure/install-azure-cli

THe first command to input in the command line would be the:

"az login"  


<img width="535" alt="Screenshot 2022-02-24 at 17 54 43" src="https://user-images.githubusercontent.com/55625732/155580194-2c72f5c0-0cec-42e4-8dcb-f93ea78795e0.png">


#This would open a browser window and let you login into you account#

When you have logged in return to the CLI, if you need help on how to combine commands on the Azure CLI environment you can run the command:

"az network vnet create --help"

#This would produce a help page with examples to create a virtual network#


<img width="700" alt="Screenshot 2022-02-24 at 17 57 01" src="https://user-images.githubusercontent.com/55625732/155580790-e793fab2-d3a3-44cd-b3f4-2b9e1ea65c6c.png">

<img width="705" alt="Screenshot 2022-02-24 at 17 57 16" src="https://user-images.githubusercontent.com/55625732/155580827-bfefeca6-5036-449f-8897-d4352f816ad6.png">


Using the example above the command would look like tis .

 az network vnet create -g testnetwork -n MyVnet --address-prefix 192.168.10.0/29 \
            --subnet-name MySubnet --subnet-prefix 192.168.10.0/24


