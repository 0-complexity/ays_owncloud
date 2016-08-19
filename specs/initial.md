# Easy OwnCloud deployment via AYS

![setup](./owncloud-setup.jpg)

Ownclouds of different customers will be hosted in one VDC. In this VDC there is 1 infrastructure VM that will act als DNS server, Reverse Proxy and SSL terminator. 

Each customer will have its own OwnCloud virtual machine with its own private storage.

Users will be able to authenticate to the deployed OwnCloud instances via ItsYou.Online

## Input parameters that customers will need to pass when buying an OwnCloud system

- domain
- capacity in GB
- ItsYou.Online organisation of people allowed to login on the OwnCloud instance
- ItsYou.Online organisation of people allowed to administer the OwnCloud instance

## Infrastructure vm (RP/SSL/DNS)

The infrastructure virtual machine will be running the following dockers:
- Caddy docker
  - SSL termination
  - Reverse proxy mapping incomming requests to the right OwnCloud vm using the hosts header in the http request
- DNS dockers

## OwnCloud vm

### OwnCloud virtual machines will be running the following dockers:
- OwnCloud 
- PerconaDB with TokuDB

### Storage in the VM is setup as follows:
- 10GB Bootdisk
- X number of data volumes depending on the requested capacity supporting a single btrfs filesystem mounted on /data
  - /data/cfg will contain the OwnCloud configuration
  - /data/db will be used for the data directory of the PerconaDB docker
  - /data/storage will be used for the OwnCloud file storage

### Storage capacity upgrade
If a running OwnCloud runs out of storage, the capacity can be upgraded by adding a disk to the vm and also to the btrfs filesystem in the vm. The virtual machine should not be brought down for this action.
