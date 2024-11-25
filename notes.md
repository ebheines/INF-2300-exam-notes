# Notes for exam


# The different layers and their role

## Application layer
The layer where applications reside and provides network services
directly to the end-user applications. 
There are several protocols in the Application layer:
- HTTP (Web document request/transfer)
- SMTP (transfer of emails)
- FTP (transfer of files)
- DNS (translation of human-friendly names for interned end systems)

A packet of information is called a 'message'.


## Transport layer
Transports application-layer messages between application endpoints, could 
server and client for example. The transport layer has two types of 
protocols; TCP and UDP. 

Transport layer packets are called 'segments'.


## Network layer
The network layer is responsible for moving 'datagrams' the network layer
packets from one host to another. The transport layer will provide a 
segment to the network layer with a destination address, then the network
layers job is to deliver the segment to the destination address. 

IP protocol is included in the network layer; the protocol which defines
the fields in the datagrams as well as how the end systems and routers
act on these fields. The IP protocol is unique and every internet component
that has internet needs to run on it. 

There are also routing protocols which will determine which route the
datagram should take between the source and destination.

The network layer is the glue that binds the Internet together.


## Link layer
The link layer is responsible ofr moving packets from one node (host or
router) to the next node in the route. The link layer gets the datagram
from the network layer and delivers it to the next node.

The services provided by the link layer depends on the specific link-layer
protocol that is employed in the link. The link layer protocol can vary
through the route a packet takes. Examples of link layer protocols are:
- Ethernet
- PPP
- Wifi
- Cable access networks DOCSIS protocol

A link-layer packet is called 'frames'.


## Physical layer
While the job of the link layer is to move entire frames, the physical
layers job is to move the individual bits within the frame from one
node to the next. The protocol in this layer again depends on the 
link layer protocols, and further on the actual transmission medium of
the link, like:
- twisted-pair copper wire
- single-mode fiber optics
- coaxial cable

Depending on the physical cable, Ethernet f.ex. has different protocols
for each physical medium. Every case moves the bit across the link in 
a different way.


# Transport layer in detail

## Demultiplexing
When a computer runs different application with different protocols,
like one with FTP, one HTTP and two Telnet, there are differnet 
sockets for each of these processes. When the transport layer then
receives a segment, it goes through the fields of the segment to find
the fields that describe which socket the segmnet should be delivered
to. Of course there is a difference in TCP and UDP sockets. 

## Multiplexing
While demultiplexing is receiving data and deliviring it to the 
correct socket, multiplexing is gathering data chunks from the
source hosts different sockets, encapsulate each data chunk with
header information for the receiving demultiplexing, and passing
the segments to the network layer to be transmitted to the
destination host. 


Demultiplexing and multiplexing are important services that needs
to be in place to pass data between the network layer and the 
correct application-level process. 



### UDP socket
Fully identified by a two-tuple consisting of:
- Destination IP address
- Destination PORT number

If two UDP segments have different source IP addresses and/or 
source port number, but the same destination PORT and IP address,
the two segments will be directed to the same destination process.

### TCP socket
TCP socket identified by a four-tuple consisting of:
- Source IP address
- Source PORT number
- Destination IP address
- Destination PORT number

The host that receives a TCP segment will use all four values to
direct, or demultiplex, the segment to the appropriate socket. 



## UDP
With UDP the application layer process does almost communicate 
directly with the IP protocol in the network layer, since UDP 
adds very little in the transport layer. It adds the two-tuple
fields for the de- and multiplexing as well as two other small
fields. The resulting segment is passed to the network layer
where it will be encapsulated into a IP datagram and delivers
the segment to the receiving host.
 
With UDP you have no handshaking between the sending and receiving
transport-layer entities before communication segments, thats why
UDP is called connectionless.

DNS is an example of a application-layer protocol which typically
uses UDP. 

With UDP, a segment is immediately passed to the network layer, while
with TCP there is a congestion-control mechanism that throttles
the transport-layer TCP when the connection gets congested. TCP 
will also send the packet until it gets a receipt that the packet
is received at the destination. 



# Network layer in detail

## Forwarding
When a packet arrives at a routers input link, the router must move
the packet to the appropriate output link

A local action taken in the router to transfer the packet from input
to output


## Routing
The network layers determines the route or path the packets should
take as they flow through the internet to their receiver. 

pA network-wide process done to determine the route the packet should
take from it's sender to it's receiver. 


## Forwarding table
A table that shows where packets should be forwarded according to the 
values in the packets headers. The header values will be compared
to the values in the table, and then the packet is moved to the 
appropriate output link according to the table. 

Example of forwarding table:

	header | output
	---------------
	0100   |  3
	0110   |  2
	0111   |  2
	1001   |  1

## NAT, Network Address Translation



## The network edge
End systems or hosts, the edge of the internet. This could be your
phone, computer, TV, smart watch etc. End systems of the internet
are called hosts since they 'host' application on them. Applications
are also a part of the network edge.


## Access networks
The network that physically connects an end system to the first router
on a path from the end system to any other distant end system. 
This means:
- Mobile network
- Home network
- National or global ISP
- Local or regional ISP
- Enterprise network
- Datacenter network


## The network core
Routers, links, servers etc. The core of the internet structure.
This is similar to the access networks, but is only:
- Local or reginoal ISP
- National or global ISP
- Content provider network
- Datacenter Network

The network core is not local networks such as mobile, home, or 
enterprise networks. 


## Store and forward
The concept that a packet switch must receive the WHOLE packet before
it can transmitt the first bit of the packet onto the outbound link. 



# Types of delay
There are several types of delay that could occur at each node that
a packet goes through at it's path. The most important ones are:

## Nodal processing delay
The time requirred to examine the packet's header and determine where
to direct the packet is part of the processing delay. This delay could also 
include other factors. 

## Queuing delay
The delay that occurs when a packet is put into a queue. The time needed
for the packet to be put into and go through the queue. If the queue is 
empty, the delay will be zero. If the queue is almost full, the delay
will be bigger.

## Transmission delay
The time required to push, or transmit, all of the packet's bits into 
the link. Transmission delay is calculated with:

	L / R		L = bit length of packet
			R = rate of bits transmitted per sec

## Propagation delay
The time required for a packet to propagate from the beginning of the link
to router B (destination router). This delay depends on the physical medium
used in that link (fiber optics, twisted-pair copper wire etc.).
The delay is the distance between the source and destination router, divided
by the propagation speed (distance between routers (d)/(s) propagation speed).




















