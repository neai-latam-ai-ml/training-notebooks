# Policies

The following document states the configuration policies of the devices of the ACME company

## Addressing Schema

1. Routable addresses used on physical Interfaces (E.g: Ethernet 1/2), Port-Chanels (port-channel1) or SVI Interfaces must be taken from the CIDR 10.1.0.0/8

    Example: 
    This is a valid interface configuration
    ```
    interface vlan 123
        no switchport
        ip address 10.1.1.254/24
    ```


2. IP Addresses assigned to Router IDs (RID) of routing protocols such as OSPF, EIGRP or BGP must be taken from the CIDR 172.20.0.0/16

    Example: 
    This is a valid OSPF process configuration

    ```
    router ospf OSPF1
        router-id  172.1.1.5
    ```


## Interface description

1. Interfaces must have a description that matches the following convention: <type>_<speed>_<peer_id>, where `type` is `L2` for switches interfaces, `L3` for routed interfaces and `PC` to interfaces member of a port-channel

    ```
    interface ethernet1/1
        no switchport
        description L3_10G_DMZ Router  
        ip address 10.1.2.254/24
    ```

## Security protocols


1. The only valid hashing protocol for payload integrity is MD5. This applies for SNMP configurations and authenticated BGP peerings as shown below:

    ```
    snmp-server user MYUSER MYGROUP v3 auth sha <password> priv aes 256 <password>

    ```

2. The only valid authentication protocol for payload encryption is AES 256
        