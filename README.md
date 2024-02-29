6.IMPLEMENTATION
In this section, we configure DNS for forward lookup as well as reverse lookup.
6.1 Deployment of DNS for Forward Lookup Tree:-
Following DNS servers are configured and tested for forward lookup in the test bed hierarchy 
hosted on IPv4:
1. Root DNS server configuration 
2. Top-Level Domain (TLD) DNS server configuration 
3. Second Top-Level Domain (STLD) DNS server configuration 
4. Recursive Resolver
6.1.1 Configuration on Root DNS Server:
The root server is the first step in translating (resolving) human readable host names into IP 
addresses. It maintains information regarding top-level domains. Root-zone servers for internet 
top-level domains are already deployed, with this we can create our own internet naming scheme.
● Install bind packages
yum install bind bind-utils bind-chroot bind-libs
● Make changes on named.conf file
nano /etc/named.conf
Inside we have to edit this:-

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/ae37d399-b467-46b6-b511-0bff88e5fc62)

