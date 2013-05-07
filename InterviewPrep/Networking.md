###Browser Interaction

What happens when typing google.com in a browser.

1. Browser takes apart the hostname and the path from the URL.
* Browser checks in local cache.
* Browser asks OS for server IP’s address.
* OS makes a DNS lookup and gives the IP address to the browser.
* Browser opens a TCP connection (3 way handshake) to server.
* Browser sends the HTTP request through the TCP connection.
* Browser receives the HTTP response and can close the TCP connection, or reuse it.
* Browser checks if the response is a re-direct (3xx), authorization request (401), error (4xx, 5xx), or normal (2xx).
* Cache what can be cached.
* Browser decodes response (ex. if it gzipped)
* Browser determines what to do with response (is it a HTML page, image, or media?)
* Browser renders response, or offers a download dialog for unrecognized types.

#####DNS Lookup

Occurs at various levels: browser, OS, ISP, and then root. Usually cached. DNS queries are done over UDP, and maybe if TCP is packet is large.
Host -> Root DNS -> TLD DNS Server -> Authoritative DNS -> back to host

#####Connection

Browser establishes a TCP/IP socket connection, typically on TCP port 80, with the web server.
A HTTP GET request is sent to the server and the browser decides what it wants to do with the response. It may get more resources using the same TCP connection.
TCP/IP breaks up the request into multiple parts if needed.

#####Server-side

The server gets a request which includes a path name. And it might return a static page depending if it's cached.
Load balancing (can use source IP, url for hashing)

#####Restful/HTTP Methods Commands
Get, Post, Put, Delete


###OSI Model
#####OSI Layer Responsibilities
1. Application - contains all protocols and methods that fall into the realm of process-to-process communications across an Internet Protocol (IP) network.
* Presentation - serves as the data translator for the network
* Session - provides the mechanism for opening, closing and managing a session between end-user application processes
* Transport Layer - provides convenient services such as connection-oriented data stream support, reliability, flow control, and multiplexing.
    * Takes care of packet retransmission in case of packet loss, and in order delivery of packets if necessary
* Network - responsible for packet forwarding including routing through intermediate routers, whereas the data link layer is responsible for media access control, flow control and error checking.
    * Takes care of routing algorithms to route packets between destinations
* Data Link - responsible for media access control, flow control and error checking.
* Physical - hardware related to data transmission

#####Layers Functions
* Application: Passes the message to the transport layer.
* Transport: Makes TCP/UDP segments. Adds header (source/destination port num)
* Network: adds another header (Source/Destination IP)
* Data Link: adds another header (Source/Destination MAC address) 
* Physical: Passes

#####Common Uses
1. Application: http, smtp, pop 
* Transport: tcp, udp,  provides reliable data communication service (reliable, ordered byte stream with bounded delay)
* Network: IP, unreliable
* Data link: ethernet, wifi, has physical addressing
* Physical: wiring, sends the bits

###UDP/TCP

TCP: connection-oriented service (TCP has client/server exchange transport layer control information before application-level messages begin to flow, aka handshaking), reliable data transfer service. Occurs between sockets of two processes. Full duplex. Can be made secure, as in SSL., error correction, flow control. TCP handshake: SYN, SYN/ACK, ACK

UDP: connectionless (no handshaking), unreliable, no congestion-control mechanism, good for multimedia/real time, no error/flow control.

#####Use Cases:
* TCP
    * Web browsing, email, file transfer.
    * TCP is used to control segment size, data exchange speed, flow control/network congestion. 
* UDP
    * Domain Name System, VOIP, Trivial file transfer protocols and online games.
    * Time sensitive cases, used for responding to small queries for large number of clients.
