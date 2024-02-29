IMPLEMENTATION

In this section, we configure DNS for forward lookup as well as reverse lookup.
1 Deployment of DNS for Forward Lookup Tree:-
Following DNS servers are configured and tested for forward lookup in the test bed hierarchy 
hosted on IPv4:
* Root DNS server configuration
* Top-Level Domain (TLD) DNS server configuration 
* Second Top-Level Domain (STLD) DNS server configuration 
* Recursive Resolver
1.1 Configuration on Root DNS Server:
The root server is the first step in translating (resolving) human readable host names into IP 
addresses. It maintains information regarding top-level domains. Root-zone servers for internet 
top-level domains are already deployed, with this we can create our own internet naming scheme.
● Install bind packages
yum install bind bind-utils bind-chroot bind-libs
● Make changes on named.conf file
nano /etc/named.conf
Inside we have to edit this:-

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/ae37d399-b467-46b6-b511-0bff88e5fc62)

Disable recursion, dnssec-enable and dnssec-validation. Never disable these three 
lines by using comment.

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/7c9ca8b7-b331-45ee-958c-34b9f003f6d5)
![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/3917296d-2cbd-461f-aab8-0a652c63bf00)


●	Create and edit root.net
nano /var/named/root.net

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/678daeac-c2cc-4630-b9d4-9e5ed372398f)

●	Edit resolv.conf file

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/66d4d01d-fa68-4769-a1cf-faadf2fdc805)

●	Now edit named.ca file
nano /var/named/named.ca

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/082ba105-7d74-4c89-998d-612aeb9ae92a)

●	systemctl restart named
●	iptables -F

6.1.2 Configuration on TLD DNS Server:
This nameserver is the next step in the search for a specific IP address, and it hosts the last portion of a hostname (In example.net, the TLD server is “net”).
Create a file accordingly to point towards our own root DNS server with some changes.
●	Install bind packages
Yum install bind bind-utils bind-chroot bind-libs
●	Make changes on named.conf file
nano /etc/named.conf
Inside we have to edit this:- 

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/db98b609-7bd0-4b7d-ab60-eca3dc5c9665)

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/d676f5f3-b8b5-4a00-8992-f456464ac9fa)

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/13a5cb58-ea07-48a4-bd21-cfc25a0a88e3)

●	Create and edit tld.net
nano /var/named/tld.net

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/8ad3f1a7-472e-4505-8156-454a38d9bf25)

●	Edit resolv.conf 

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/adf4e9ee-4e49-4c8b-b3c7-7bfee9e854a4)

●	systemctl restart named
●	Query some records that are stored in primary server's tld.net file by using nslookup command
6.1.3 Configuration on STLD Authoritative DNS Server:
The authoritative nameserver is the last step in the nameserver query. If the authoritative name server has access to the requested record, it will return the IP address for the requested hostname back to the DNS Recursor that made the initial request.
●	For this again install bind packages
yum install bind bind-utils bind-chroot bind-libs

●	Make changes on named.conf file
nano /etc/named.conf
Inside we have to edit this:- 

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/4d6be861-3918-47ac-b58d-de4f27536e19)

 
Disable recursion, dnssec-enable and dnssec-validation. Never disable these three 
lines by using uncomment.

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/db366a30-1a40-403d-9409-d002b4de684d)

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/1d3a3f9f-3c7a-45ce-a1d1-231c9b355d1c)

●	Create and edit stld.net
nano /var/named/stld.net

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/f6b91a1a-bddd-4c1a-899e-d4ed49ac57f4)

●	Edit resolv.conf file

![image](https://github.com/gawhale-ashwini/Project-0732/assets/149654320/455f84a8-c8ce-4ef8-ba30-319e8fab25f6)

●	systemctl restart named

●	Query some records that are stored in primary server's stld.net file by using nslookup command















