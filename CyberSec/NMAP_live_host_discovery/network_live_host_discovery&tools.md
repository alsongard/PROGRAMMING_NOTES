Nmap (Network Mapper) is a open-source tool used for network discovery and security auditing. It also assists in the exploration of network hosts and services, providing information about open ports, operating systems, and other details.
ddress Resolution Protocol (ARP) is responsible for finding the MAC (hardware) address related to a specific IP address. It works by broadcasting an ARP query, "Who has this IP address? Tell me." And the response is of the form, "The IP address is at this MAC address."
ICMP scan: This scan uses ICMP requests to identify live hosts
TCP/UDP ping scan: This scan sends packets to TCP ports and UDP ports to determine live hosts.

address resolution protocol (ARP) can only be used to find machines within the subnet / network segment.
if a target is on another subnet, we cannot use ARP as packets need to head for the router gateway and then be transmitted to the desired target network segment.

nmap can be used to scan multiple hosts.
``nmap -iL list_of_hosts.txt``
``nmap -sL TARGETS ``:the command will list all the host that nmap **will** scan and try to perform reverse-DNS solution.To avoid these, use the -n.``nmap -n``
``nmap -R `` : this informs nmap to use dns-resolution


privilege and unprivelege users:
when using nmap as a priveleged users, on local network nmap uses ARP(Address resolution Protocol) and when scanning a target outside the local network nmap uses  ICMP(Internet control message protocol) request, TCP ACK(acknowledge) to port 80, TCP SYN(sychronize) (does not complete the 3 way handshake)  to port 443 and ICMP timestamp request.
For unprivilege users, nmap uses 3-way handshake by sending SYN packets to port 443 and 80.

To discover hosts on the same network/subnet, nmap uses ARP protocol.
``nmap -PR -sn ip_address ``
The option ``-sn`` is used to stop port scan.
The option ``-PR`` is used for address resolution port scan.

## arp-scan tool
the arp-scan is a tool that is built for ARP queries. It has many options:
Always remember to use with **sudo** privileges: ``sudo arp-scan ip_address``
Example
``arp-scan -l`` : send arp request to all ip address on your subnet.
``arp-scan -l -I wlan0``: ``-I`` option is used to provide an interface.

## ICMP scan
Internet control message protocol. Using ICMP echo scan, ICMP timestamp scan and ICMP address map scan.
ICMP echo reqeust(Type 8) : used by pings to discover in a device is online. Use option ``-PE``. If host is online will receive an ICMP response packet(Type 0)
``sudo nmap -PE -sn ip_address``

ICMP timestamp(-PP): 
``sudo nmap -PP -sn iap_address``
timestamp request (ICMP type 13) and reply will be Timestamp reply(ICMP type 14)

ICMP address mask(-PM):
``sudo nmap -PM -s ip_address``
using address mask to check host is live.
The 3 types of ICMP scans can be used alternatively since most firewall tend to drop ICMP echo requests. 


### Nmap Host Discovery Using TCP and UDP
Using the SYN flag.
``nmap -PS -sn ip_address[portlist,range,portnumber]`` : default port set is 80. For privileged users no need to finish 3-way handshake, opposite for unprivileged users. If port is open, we recieve reply (ACKNOWLEDGE), otherwise(closed) receive RESET
****
Using the ACK flag:
only  privilege users can use this;
``nmap -PA -sn ip_address[portrange, portlist, portnumber]`` : if a port is open, receive a **RESET** flag, as the packet is not part of any sychronizer handshake.
****
Using the UDP(user datagram packet):
``nmap -PU -sn ip_address[portrange, portlist, portnumber]`` : when sending a UDP packet, if the port is open, there is no reply, however if the port is closed, we should receive an ICMP host unreachable and this indicates that the target is online. 
