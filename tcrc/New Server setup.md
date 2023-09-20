# 4 new server came with 2x4TB storage. 
## Dell EMC PowerEdge T440
### Service Tag : 47DVJQ3
- iDRAC
- RAID
- OS ubuntu 22LTS 
- Disk Encryption 
- Resize disk space
- Firewall
- SSL
- LAMP ?
- docker
- CICD

## iDRAC
- Connect an Ethernet port to iDRAC port on the server
- Enter F2 or F10 on boot screen for iDRAC setting
- Disable DHCP and assign static ip to the server 
- I gave ip 172.28.21.205 to the server 
- apply changes by exiting and saving changes 
- On your local machine with same ip range, go to your browser and enter the ip  (in my case 172.28.21.205) 
- If chrome blocks the page enter 'thisisunsafe' to bypass
- To login, username is 'root' and default password is written on the back of service tag
- Update your iDRAC password.
- Download updated BIOS and iDRAC firmware at the [dell.com/support](https://www.dell.com/support/home/en-in/product-support/product/poweredge-t440/drivers) site 
- go to Maintenance > System Update > Manual Update 

### iDRAC connection from LAN
If you don't want to use the dedicated iDRAC ethernet port you can configure iDRAC to be accessible over the LAM. To do so:
- go to iDRAC > network setting on boot by pressing F2
- Change the iDRAC port from default dedicated to LOM1 
- Set Fallover to LOM2 
- Give static ip in the same range at your local machine 
- Apply and exit

## Redundant Array of Independent Disks (**RAID**)
- Make sure Physical Disks are all the way plugged in
- go to Storage > Physical Disks > Create Virtual Disk and follow the steps 

## OS Installation
- Download the Ubuntu Server iso 
- from iDRAC go to Virtual Console > Virtual Media > Map CD/DVD and select the iso file
- map the Device and Boot with CD/DVD/ISO
- follow the steps 

## Disk Encryption 
- During the Ubuntu Server OS installation, opt for Encrypt the LVM group with LUKS and give password. For docker server I set the disk encryption to 9vgXDLBQvLmvCt
- username tcrc  and password es4RbC3QY

## Initial Ubuntu setup
- Switch to root user with  
> sudo -i
- Give static ip address
	- Go to /etc/netplan > open 00-installer-config.yaml
	- Change the netplan accordingly
```
# This is the network config written by 'subiquity'
network:
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
      addresses:
        - 172.28.13.222/24
      routes:
        - to: default
          via: 172.28.13.1
      nameservers:
        addresses: [8.8.8.8,1.1.1.1]
    eno2:
      dhcp4: true
  version: 2
```
Apply the changes with
> sudo netplan apply
- Optionally do [[how to ssh without entering password]]
- Do the [initial server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04)
- Do [install docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)
