# Focused Problem Set for Computer Networking: A Top-Down Approach, 7th Edition

**Source:** https://gaia.cs.umass.edu/kurose_ross/knowledgechecks/index.php  

---

# Interactive Implementation

## Chapter 1: Introduction

### Circuit Switching

Consider the circuit-switched network shown in the figure below, with circuit switches A, B, C, and D. Suppose there are 12 circuits between A and B, 14 circuits between B and C, 18 circuits between C and D, and 11 circuits between D and A.

![Untitled](img/interactive1/Untitled.png)

#### Focused Questions

1. Find the maximum number of simultaneous connections in the network.
2. Under the 2-hop clockwise constraint, find the maximum number of simultaneous connections.
3. Decide whether 16 A→C connections and 12 B→D connections can be supported, and justify briefly.

#### Focused Solutions

1. Maximum simultaneous connections = 61.
2. Maximum under the 2-hop clockwise constraint = 29.
3. Yes. The demand is 28 connections, and the constrained maximum is 29.

---

### Quantitative Comparison of Packet Switching and Circuit Switching

This question requires a little bit of background in probability (but we'll try to help you though it in the solutions). Consider the two scenarios below:

- A circuit-switching scenario in which *Ncs* users, each requiring a bandwidth of 25 Mbps, must share a link of capacity 200 Mbps.
- A packet-switching scenario with *Nps* users sharing a 200 Mbps link, where each user again requires 25 Mbps when transmitting, but only needs to transmit 10 percent of the time.

![Untitled](img/interactive1/Untitled%201.png)

#### Focused Questions

1. For circuit switching, find the maximum number of users supported by a 200 Mbps link when each user needs 25 Mbps.
2. For packet switching with 15 users and activity probability p = 0.1, compute:
   - the probability exactly one user is transmitting,
   - the probability exactly six users are transmitting,
   - the probability more than eight users are transmitting.
3. Explain why packet switching can support more users than circuit switching in this example.

#### Focused Solutions

1. Circuit switching supports 8 users.
2. Results:
   - Exactly one user: 0.34
   - Exactly six users: 0.0019
   - More than eight users: 2.85E-6
3. Packet switching relies on statistical multiplexing. Not all users transmit at the same time, so 15 users can share the link with only a very small probability of overload.

---

### Car - Caravan Analogy

Consider the figure below, adapted from Figure 1.17 in the text, which draws the analogy between store-and-forward link transmission and propagation of bits in packet along a link, and cars in a caravan being serviced at a toll booth and then driving along a road to the next tollbooth.

![Untitled](img/interactive1/Untitled%202.png)

Suppose the caravan has 10 cars, and that the tollbooth services (that is, transmits) a car at a rate of one car per 1 seconds. Once receiving serving a car proceeds to the next tool both, which is 200 kilometers away at a rate of 10 kilometers per second. Also assume that whenever the first car of the caravan arrives at a tollbooth, it must wait at the entrance to the tollbooth until all of the other cars in its caravan have arrived, and lined up behind it before being serviced at the toll booth. (That is, the entire caravan must be stored at the tollbooth before the first car in the caravan can pay its toll and begin driving towards the next tollbooth).

#### Focused Questions

1. Compute the total service time for the caravan at one tollbooth and the travel time to the next tollbooth.
2. When does the first car enter service at the next tollbooth?
3. Decide whether two tollbooths can serve cars at the same time, and whether there can be a period when no cars are in service.

#### Focused Solutions

1. Service time for the caravan = 10 seconds. Travel time = 20 seconds.
2. The first car enters service at the next tollbooth after 29 seconds.
3. Two cars are never in service at both tollbooths at the same time. Yes, there can be a period with zero cars in service while the caravan is traveling.

---

### One-hop Transmission Delay

Consider the figure below, in which a single router is transmitting packets, each of length *L* bits, over a single link with transmission rate *R* Mbps to another router at the other end of the link.

Suppose that the packet length is *L*= 12000 bits, and that the link transmission rate along the link to router on the right is *R* = 100 Mbps.

![Untitled](img/interactive1/Untitled%203.png)

#### Focused Questions

1. Compute the transmission delay for L = 12000 bits and R = 100 Mbps.
2. Compute the maximum number of packets per second the link can transmit.

#### Focused Solutions

1. Transmission delay = 0.00012 seconds.
2. Maximum packet rate = 8333 packets/second.

---

### Queuing Delay

Consider the queuing delay in a router buffer, where the packet experiences a delay as it waits to be transmitted onto the link. The length of the queuing delay of a specific packet will depend on the number of earlier-arriving packets that are queued and waiting for transmission onto the link. If the queue is empty and no other packet is currently being transmitted, then our packet’s queuing delay will be zero. On the other hand, if the traffic is heavy and many other packets are also waiting to be transmitted, the queuing delay will be long.

![Untitled](img/interactive1/Untitled%204.png)

Assume a constant transmission rate of R = 400000 bps, a constant packet-length L = 3900 bits, and a is the average rate of packets/second. Traffic intensity I = La/R, and the queuing delay is calculated as I(L/R)(1 - I) for I < 1.

#### Focused Questions

1. Explain whether queuing delay is usually constant or variable in practice.
2. Compute the queuing delay for a = 33 and a = 63.
3. Given delay = 2.3101 ms and 1819 arriving packets, compute the packets left in an infinite buffer, then the number dropped if the buffer size is 968.

#### Focused Solutions

1. Queuing delay varies a lot in practice.
2. For a = 33: 2.1279 ms. For a = 63: 2.3101 ms.
3. Packets left = 1387. Dropped packets = 851.

---

### End-to-End Delay

Consider the figure below, with three links, each with the specified transmission rate and link length.

![Untitled](img/interactive1/Untitled%205.png)

Assume the length of a packet is 4000 bits. The speed of light propagation delay on each link is 3x10^8 m/sec

#### Focused Questions

1. Compute the transmission, propagation, and total delay for each of the three links.
2. Compute the total end-to-end delay.

#### Focused Solutions

1. Link delays:
   - Link 1: transmission = 4.00E-6 s, propagation = 1.00E-5 s, total = 1.40E-5 s
   - Link 2: transmission = 0.0004 s, propagation = 0.017 s, total = 0.017 s
   - Link 3: transmission = 0.0004 s, propagation = 3.33E-6 s, total ≈ 0.0004 s
2. Total end-to-end delay ≈ 0.017 seconds.

---

### End-to-End Throughput

Consider the scenario shown below, with four different servers connected to four different clients over four three-hop paths. The four pairs share a common middle hop with a transmission capacity of R = 400 Mbps. The four links from the servers to the shared link have a transmission capacity of RS = 60 Mbps. Each of the four links from the shared middle link to a client has a transmission capacity of RC = 20 Mbps.

![Untitled](img/interactive1/Untitled%206.png)

#### Focused Questions

1. Find the maximum end-to-end throughput per client-server pair.
2. Identify the bottleneck link and compute utilization for RS, RC, and R.

#### Focused Solutions

1. Maximum throughput = 20 Mbps.
2. Bottleneck = RC. Utilizations:
   - RS: 0.33
   - RC: 1
   - Shared R: 0.2

---

### The IP Stack and Protocol Layering

In the scenario below, imagine that you're sending an http request to another machine somewhere on the network.

![Untitled](img/interactive1/Untitled%207.png)

#### Focused Questions

1. Match each description to the correct layer: application, transport, network, link, physical.
2. Label the protocol stack from sender to receiver using the five layers.
3. Explain why routers do not use the application and transport layers for forwarding.

#### Focused Solutions

1. Matches:
   - Handles application messages: Application
   - Reliable/unreliable segment delivery: Transport
   - Moves datagrams source-to-destination: Network
   - Passes frames between nodes: Link
   - Bits on the wire: Physical
2. Sender stack: Application → Transport → Network → Link → Physical. Receiver stack is the reverse. Routers mainly process Physical, Link, and Network layers.
3. Routers forward datagrams based on network-layer information; they do not need application data or end-host transport state.

---

## Chapter 2: Application Layer

### DNS - Basics

Imagine that you are trying to visit www.enterprise.com, but you don't remember the IP address the web-server is running on.

Assume the following records are on the TLD DNS server:

- (www.enterprise.com, dns.enterprise.com, NS)
- (dns.enterprise.com, 146.54.219.75, A)

Assume the following records are on the enterprise.com DNS server:

- (www.enterprise.com, west5.enterprise.com, CNAME)
- (west5.enterprise.com, 142.81.17.206, A)
- (enterprise.com, mail.enterprise.com, MX)
- (mail.enterprise.com, 247.29.64.33, A)

![Untitled](img/interactive1/Untitled%208.png)

Assume your local DNS server only has the TLD DNS server cached.

#### Focused Questions

1. State the transport protocol(s), port number, and whether DNS uses caching.
2. Identify the main DNS record types in the example and explain what A, NS, CNAME, and MX are used for.
3. Trace the lookup for www.enterprise.com: local DNS → TLD → authoritative DNS, including the key returned records.
4. Trace the email lookup for admin@enterprise.com and identify the MX record contents.

#### Focused Solutions

1. DNS uses both UDP and TCP, port 53, and it uses caching.
2. Record types:
   - A: hostname to IP address
   - NS: domain to authoritative DNS server
   - CNAME: alias to canonical hostname
   - MX: domain to mail server
3. The TLD returns:
   - NS: www.enterprise.com → dns.enterprise.com
   - A: dns.enterprise.com → 146.54.219.75  
   The authoritative DNS returns:
   - CNAME: www.enterprise.com → west5.enterprise.com
   - A: west5.enterprise.com → 142.81.17.206
4. MX record: enterprise.com → mail.enterprise.com.

---

### DNS - Iterative vs Recursive Query

Assume that a user is trying to visit [gaia.cs.umass.edu](http://gaia.cs.umass.edu/), but his browser doesn't know the IP address of the website. In this example, examine the difference between an iterative and recursive DNS query.

![Untitled](img/interactive1/Untitled%209.png)

#### Focused Questions

1. Compare iterative and recursive DNS lookup paths.
2. Identify the record type returned when the authoritative DNS server resolves gaia.cs.umass.edu.
3. State which query style is preferred in practice and why.

#### Focused Solutions

1. Iterative: local DNS contacts root, then TLD, then authoritative server. Recursive: each DNS server forwards the request to the next server.
2. The returned record is type A.
3. Iterative is preferred because it reduces load on root and TLD servers.

---

### DNS and HTTP Delays

Before doing this question, you might want to review sections 2.2.1 and 2.2.2 on HTTP (in particular the text surrounding Figure 2.7) and the operation of the DNS (in particular the text surrounding Figure 2.19).

Suppose within your Web browser you click on a link to obtain a Web page. The IP address for the associated URL is not cached in your local host, so a DNS lookup is necessary to obtain the IP address. Suppose that four DNS servers are visited before your host receives the IP address from DNS. The first DNS server visited is the local DNS cache, with an RTT delay of RTT0 = 3 msecs. The second, third and fourth DNS servers contacted have RTTs of 42, 29, and 14 msecs, respectively. Initially, let's suppose that the Web page associated with the link contains exactly one object, consisting of a small amount of HTML text. Suppose the RTT between the local host and the Web server containing the object is RTTHTTP = 93 msecs.

![Untitled](img/interactive1/Untitled%2010.png)

#### Focused Questions

1. Compute total delay for one small HTML object after DNS lookup.
2. Compute total delay for a base object plus 8 embedded objects using:
   - non-persistent HTTP without parallel TCP,
   - non-persistent HTTP with up to 5 parallel TCP connections,
   - persistent HTTP with up to 5 parallel TCP connections.
3. Rank the methods from fastest to slowest.

#### Focused Solutions

1. One object: 274 ms.
2. Results:
   - Non-persistent serial: 1762 ms
   - Non-persistent parallel: 646 ms
   - Persistent parallel: 460 ms
3. Fastest to slowest: persistent parallel, non-persistent parallel, non-persistent serial.

---

### HTTP GET

Consider the figure below, where a client is sending an HTTP GET message to a web server, [gaia.cs.umass.edu](http://gaia.cs.umass.edu/)

![Untitled](img/interactive1/Untitled%2011.png)

Suppose the client-to-server HTTP GET message is the following:

*GET /kurose_ross_sandbox/interactive/quotation5.htm HTTP/1.1Host: gaia.cs.umass.eduAccept: text/plain, text/html, image/jpeg, image/gif, audio/vnf.wave, audio/basic, video/mp4, video/wmv,Accept-Language: en-us, en-gb;q=0.7, en;q=0.8, fr, fr-ch, zh, de, ar, csIf-Modified-Since: Thu, 19 Oct 2023 12:28:38 -0700User Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:12.0) Gecko/20100101 Firefox/12.0*

#### Focused Questions

1. From the HTTP GET request, identify the requested file, HTTP version, accepted media types, and accepted languages.
2. Explain what the If-Modified-Since header tells the server.

#### Focused Solutions

1. File: quotation5.htm. HTTP version: HTTP/1.1. The client accepts text/html, image/jpeg, German, and several other languages.
2. It means the client has a cached copy and asks the server to send the file only if it has changed since Thu, 19 Oct 2023 12:28:38 -0700.

---

### HTTP Response

Consider the figure below, where the server is sending a HTTP RESPONSE message back the client.

![Untitled](img/interactive1/Untitled%2012.png)

Suppose the server-to-client HTTP RESPONSE message is the following:

*HTTP/1.0 404 Not FoundDate: Thu, 19 Oct 2023 19:41:19 +0000Server: Apache/2.2.3 (CentOS)Content-Length: 353Connection: CloseContent-type: image/html*

#### Focused Questions

1. From the HTTP response, identify the HTTP version, status meaning, object size, connection type, content type, and server version.
2. Explain whether the ETag changes when the resource content changes.

#### Focused Solutions

1. HTTP/1.0. Status 404 Not Found, so the document was not successfully sent. Size = 353 bytes. Connection = nonpersistent. Content type = image/html. Server = Apache/2.2.3.
2. Yes. The ETag changes when the resource changes.

---

### Browser Caching

Consider an HTTP server and client as shown in the figure below. Suppose that the RTT delay between the client and server is 30 msecs; the time a server needs to transmit an object into its outgoing link is 1 msecs; and any other HTTP message not containing an object has a negligible (zero) transmission time. Suppose the client again makes 100 requests, one after the other, waiting for a reply to a request before sending the next request.

![Untitled](img/interactive1/Untitled%2013.png)

Assume the client is using HTTP 1.1 and the IF-MODIFIED-SINCE header line. Assume 60% of the objects requested have NOT changed since the client downloaded them (before these 100 downloads are performed)

#### Focused Questions

1. Compute the total time for 100 sequential requests when RTT = 30 ms, object transmission time = 1 ms, and 60% of objects are unchanged.

#### Focused Solutions

1. Total time = 3040 ms.

---

### Electronic Mail and SMTP

Look at the scenario below, where Alice sends an email to Bob.

![Untitled](img/interactive1/Untitled%2014.png)

For the questions below, assume both Bob's and Alice's user agents use the POP3 protocol.

#### Focused Questions

1. Identify which protocols are used when Alice sends mail to Bob and Bob retrieves it using POP3.
2. State whether SMTP and POP3 are push or pull protocols, and give their port numbers.

#### Focused Solutions

1. SMTP is used to send mail between Alice, Alice's mail server, and Bob's mail server. POP3 is used when Bob retrieves the email.
2. SMTP: TCP, push, port 25. POP3: pull, port 110.

---

### Client-Server vs P2P File Distribution

#### Focused Questions

1. Compute the minimum distribution time using the client-server model and identify the bottleneck.
2. Compute the minimum distribution time using P2P and identify the bottleneck.

#### Focused Solutions

1. Client-server time = 833.33 seconds. Bottleneck = client c1.
2. P2P time = 833.33 seconds. Bottleneck = client download rate.

---

## Chapter 3: Transport Layer

### Internet Checksum

Consider the two 16-bit words (shown in binary) below. Recall that to compute the Internet checksum of a set of 16-bit words, we compute the one's complement sum [[1](http://mathforum.org/library/drmath/view/54379.html)] of the two words. That is, we add the two numbers together, making sure that any carry into the 17th bit of this initial sum is added back into the 1's place of the resulting sum); we then take the one's complement of the result. Compute the Internet checksum value for these two 16-bit words:

10001011   01011010

*this binary number is 35674 decimal (base 10)*

00001001   00001001

*this binary number is 2313 decimal (base 10)*

#### Focused Questions

1. Add the two 16-bit words and compute the Internet checksum.

#### Focused Solutions

1. Sum = 1001010001100011. Checksum = 0110101110011100.

---

### Reliable Data Transfer: rdt2.2

Consider the rdt2.2 protocol from the text (pages 209-212). The FSMs for the sender and receiver are shown below:

![Untitled](img/interactive1/Untitled%2016.png)

![Untitled](img/interactive1/Untitled%2017.png)

Suppose that the channel connecting the sender and receiver can corrupt but not lose or reorder packets. Now consider the figure below, which shows four data packets and three corresponding ACKs being exchanged between an rdt 2.2 sender and receiver. The actual corruption or successful transmission/reception of a packet is indicated by the corrupt and OK labels, respectively, shown above the packets in the figure below.

![Untitled](img/interactive1/Untitled%2018.png)

#### Focused Questions

1. For the shown exchange, identify the sender/receiver states and sequence or ACK numbers at t = 0, 1, 2, and 3.
2. How many payloads are delivered to the higher layer?

#### Focused Solutions

1. Summary:
   - t=0: sender waits for ACK 0, receiver waits for 0, sequence = 0
   - t=1: sender waits for ACK 0, receiver waits for 0, ACK = 1
   - t=2: sender waits for ACK 0, receiver waits for 0, sequence = 0
   - t=3: sender waits for ACK 0, receiver waits for 1, ACK = 0
2. One payload is delivered.

---

### Reliable Data Transfer: rdt3.0

Consider the RDT 3.0 protocol, for reliably communicating data from a sender to receiver over a channel that can lose or corrupt packets in either direction, and when the maximum delay from sender to receiver and back is not known. The FSMs for the sender and receiver are shown below, with their transitions labeled as SX and RY, respectively.

![Untitled](img/interactive1/Untitled%2019.png)

![Untitled](img/interactive1/Untitled%2020.png)

Now let’s consider the sequence of sender and receiver transitions that would happen when one or more of the following complications occur: a packet (data or ACK) is lost, a timer times out (prematurely or not), or a message is corrupted. One or more of these events has occurred to produce the sequence of transitions below. In the sequence below, one transition has been omitted and replaced with a "*".

Transition Sequence: S0, R0, S1, S2, *, S1, S2, R1, S1, S2, R1, S3, S5, R2, S6, S7, R3, S6, S7, R3, S6, S7, R3, S6, S7, R3, S6, S7, R3, S8

#### Focused Questions

1. Identify the missing transition in the transition sequence.

#### Focused Solutions

1. Missing transition = R1.

---

### TCP Sequence and ACK Numbers with Segment Loss

Consider the figure below in which a TCP sender and receiver communicate over a connection in which the sender->receiver segments may be lost. The TCP sender sends an initial window of 3 segments. Suppose the initial value of the sender->receiver sequence number is 47 and the first 3 segments *each* contain 685 bytes. The delay between the sender and receiver is 7 time units, and so the first segment arrives at the receiver at t=8. As shown in the figure below, 1 of the 3 segment(s) are lost between the segment and receiver.

![Untitled](img/interactive1/Untitled%2021.png)

#### Focused Questions

1. Compute the sender sequence numbers for the 3 sent segments.
2. Compute the receiver ACKs, using x for the lost segment.

#### Focused Solutions

1. Sequence numbers: 47,732,1417.
2. ACKs: 732,1417,x.

---

### TCP RTT and Timeout

Suppose that TCP's current estimated values for the round trip time (*estimatedRTT*) and deviation in the RTT (*DevRTT*) are 270 msec and 45 msec, respectively (see Section 3.5.3 for a discussion of these variables). Suppose that the next three measured values of the RTT are 360 msec, 320 msec, and 200 msec respectively.

![Untitled](img/interactive1/Untitled%2022.png)

Compute TCP's new value of *DevRTT, estimatedRTT,* and the TCP timeout value after each of these three measured RTT values is obtained. Use the values of α = 0.125, and β = 0.25. Round your answers to two decimal places after leading zeros.

#### Focused Questions

1. Compute EstimatedRTT, DevRTT, and Timeout after each of the three RTT samples: 360 ms, 320 ms, and 200 ms.

#### Focused Solutions

1. Results:
   - After RTT1: EstimatedRTT = 281.25, DevRTT = 56.25, Timeout = 506.25
   - After RTT2: EstimatedRTT = 286.09, DevRTT = 51.88, Timeout = 493.59
   - After RTT3: EstimatedRTT = 275.33, DevRTT = 60.43, Timeout = 517.05

---

### TCP Congestion Window Evolution

Consider the figure below, which plots the evolution of TCP's congestion window at the beginning of each time unit (where the unit of time is equal to the RTT); see Figure 3.53 in the text. In the abstract model for this problem, TCP sends a "flight" of packets of size *cwnd* at the beginning of each time unit. The result of sending that flight of packets is that either *(i)* all packets are ACKed at the end of the time unit, *(ii)* there is a timeout for the first packet, or *(iii)* there is a triple duplicate ACK for the first packet. In this problem, you are asked to reconstruct the sequence of events (ACKs, losses) that resulted in the evolution of TCP's *cwnd* shown below.

![Untitled](img/interactive1/Untitled%2023.png)

Consider the evolution of TCP's congestion window in the example above and answer the following questions. The initial value of *cwnd* is 1 and the initial value of *ssthresh* (shown as a red +) is 8.

#### Focused Questions

1. From the cwnd plot, list the time intervals for slow start, congestion avoidance, and fast recovery.
2. List the times of packet loss by timeout and by triple duplicate ACK.
3. List the times when ssthresh changes.

#### Focused Solutions

1. States:
   - Slow start: 1,2,3,13,14,15,16,22,23,26,27,34,35,36,39,40
   - Congestion avoidance: 4,5,6,7,8,9,10,11,12,17,18,19,20,21,24,25,28,29,31,32,33,37,38
   - Fast recovery: 30
2. Losses:
   - Timeout: 12,15,21,25,33,38
   - Triple duplicate ACK: 29
3. ssthresh changes: 16,22,26,34,39.

---

### TCP Retransmissions with ACK Loss

Consider the figure below in which a TCP sender and receiver communicate over a connection in which the segments can be lost. The TCP sender wants to send a total of 10 segments to the receiver and sends an initial window of 5 segments at t = 1, 2, 3, 4, and 5, respectively. Suppose the initial value of the sequence number is 104 and every segment sent to the receiver each contains 957 bytes. The delay between the sender and receiver is 7 time units, and so the first segment arrives at the receiver at t = 8, and an ACK for this segment arrives at t = 15. As shown in the figure, 1 of the 5 segments is lost between the sender and the receiver, but *one* of the ACKs is lost. Assume there are no timeouts and any out of order segments received are thrown out.

![Untitled](img/interactive1/Untitled%2025.png)

#### Focused Questions

1. Compute the sequence numbers of the first 5 sent segments.
2. Compute the ACKs sent by the receiver for arrivals at t = 8 through t = 12.
3. Compute which new segment sequence numbers are sent at t = 15 through t = 19, using x where none is sent.

#### Focused Solutions

1. First 5 sequence numbers: 104,1061,2018,2975,3932.
2. ACKs: 1061,2018,2975,x,2975.
3. Sent at t=15..19: 4889,x,5846,6803,x.

---

### UDP Mux and Demux

In the scenario below, the left and right clients communicate with a server using UDP sockets. The same socket at the server is used to communicate with both clients. The Python code used to create the sockets is shown in the figure. Consider the four transport-layer packets – A, B, C and D – shown in the figure below.

![Untitled](img/interactive1/Untitled%2026.png)

#### Focused Questions

1. For packets A, B, C, and D, give each packet's source and destination port.

#### Focused Solutions

1. Ports:
   - A: src 7478, dst 7376
   - B: src 7376, dst 7478
   - C: src 7478, dst 7376
   - D: src 7376, dst 7478

---

### TCP Mux and Demux

In the scenario below, the left and right TCP clients communicate with a TCP server using TCP sockets. The Python code used to create a single welcoming socket in the server is shown in the figure (the welcoming socket itself is not shown graphically); code is also shown for the client sockets as well. The three sockets shown in server were created as a result of the server accepting connection requests on this welcoming socket from the two clients (one connection from the client on the left, and two connections from the client on the right).

![Untitled](img/interactive1/Untitled%2027.png)

#### Focused Questions

1. For packets A, B, C, and D, give each packet's source and destination port.

#### Focused Solutions

1. Ports:
   - A: src 6595, dst 5429
   - B: src 5429, dst 6595
   - C: src 5641, dst 5429
   - D: src 6918, dst 5429

---

## Chapter 4: Network Layer: Data Plane

### Longest Prefix Matching

![Untitled](img/interactive2/Untitled.png)

#### Focused Questions

1. For the three destination addresses, apply longest-prefix matching and give the forwarding interface for each.

#### Focused Solutions

1. Interfaces:
   - 00001100 → interface 3
   - 11100010 → interface 4
   - 01010111 → interface 5

---

### Packet Scheduling

![Untitled](img/interactive2/Untitled%201.png)

#### Focused Questions

1. For the shown arrivals, give the complete transmission order for FIFO, Priority, Round-Robin, and WFQ.

#### Focused Solutions

1. Transmission orders:
   - FIFO: 1,2,3,4,5,6,7,8,9,10,11
   - Priority: 1,2,3,7,8,9,10,11,4,5,6
   - Round-Robin: 1,2,3,7,4,5,8,6,9,10,11
   - WFQ: 1,2,3,7,8,9,10,11,4,5,6

---

### Subnet Addressing

![Untitled](img/interactive2/Untitled%202.png)

#### Focused Questions

1. Determine whether 12.5.14.0/24 is public or private, and compute the total usable host addresses.
2. Allocate subnets A and B, then give each subnet's CIDR, broadcast address, first usable address, and last usable address.

#### Focused Solutions

1. 12.5.14.0/24 is public. Usable hosts = 254.
2. Subnets:
   - A: 12.5.14.128/26, broadcast 12.5.14.191, usable range 12.5.14.129–12.5.14.190
   - B: 12.5.14.0/25, broadcast 12.5.14.127, usable range 12.5.14.1–12.5.14.126

---

### Network Address Translation

![Untitled](img/interactive2/Untitled%203.png)

#### Focused Questions

1. Trace the source and destination IP addresses through the four NAT steps.
2. Explain whether NAT changes the source port and when the NAT table entry is created.

#### Focused Solutions

1. IP address trace:
   - Step 1: src 10.0.1.15, dst 128.119.177.183
   - Step 2: src 135.122.200.220, dst 128.119.177.183
   - Step 3: src 128.119.177.183, dst 135.122.200.220
   - Step 4: src 128.119.177.183, dst 10.0.1.15
2. Yes, NAT changes the source port. The NAT table entry is created during the outbound request between step 1 and step 2.

---

### IPv6 Tunneling and Encapsulation

![Untitled](img/interactive2/Untitled%204.png)

#### Focused Questions

1. Identify the tunnel entrance and tunnel exit.
2. For the tunnel path, state the outer datagram version, outer source/destination addresses, and encapsulated source/destination addresses.
3. For the final IPv6 segment, state whether the datagram is still encapsulated.
4. State which protocol encapsulates the other.

#### Focused Solutions

1. Tunnel entrance = B. Tunnel exit = F.
2. Tunnel path uses an IPv4 outer datagram:
   - Outer src: 8.160.132.48
   - Outer dst: 18.178.57.239
   - Encapsulated IPv6 src: FB43:DDB6:212F:27F9:68DB:5812:4B5E:3F85
   - Encapsulated IPv6 dst: 777A:84D4:4A7A:443B:DE75:67FA:8983:8159
3. The final F→D datagram is IPv6 and is not encapsulated.
4. IPv4 encapsulates IPv6 during the tunnel.

---

### OpenFlow Flow Tables

![Untitled](img/interactive2/Untitled%205.png)

#### Focused Questions

1. Write the OpenFlow rule for s1.
2. Write the OpenFlow rule for s4.

#### Focused Solutions

1. s1 rule: IP_Src=128.122/16, IP_Dst=128.119/16, Src_Port=Any, Dst_Port=Any, IP_Protocol=Any, Action=Forward(1).
2. s4 rule: IP_Src=128.122/16, IP_Dst=128.119/16, Src_Port=Any, Dst_Port=Any, IP_Protocol=Any, Action=Forward(2).

---

## Chapter 5: Network Layer: Control Plane

### Dijkstra's Link State Algorithm

![Untitled](img/interactive2/Untitled%206.png)

#### Focused Questions

1. From source u, give the shortest distance and predecessor for v, y, and x.

#### Focused Solutions

1. Results:
   - v: 6,u
   - y: 10,w
   - x: 5,u

---

### Dijkstra's Link State Algorithm - Advanced

![Untitled](img/interactive2/Untitled%207.png)

#### Focused Questions

1. Compute the unknown link costs X and Y, or write n/a if not determinable.

#### Focused Solutions

1. X = 9. Y = 5.

---

### Bellman-Ford Distance Vector Algorithm

![Untitled](img/interactive2/Untitled%208.png)

#### Focused Questions

1. Give router U's converged distance vector.
2. Give router X's initial distance vector.
3. Name the problem that occurs when link costs increase.

#### Focused Solutions

1. U converged vector (u,v,w,x,y) = 0,4,8,5,10.
2. X initial vector (u,v,w,x,y) = x,1,3,0,5.
3. Count-to-infinity problem.

---

## Chapter 6: Link Layer

### Error Detection and Correction: Two-Dimensional Parity

![Untitled](img/interactive2/Untitled%209.png)

#### Focused Questions

1. For figure 1, compute the column parity string, row parity string, and final parity bit.
2. For figure 2, locate the flipped bit.
3. For figure 3, decide whether the bit errors can be detected and corrected.

#### Focused Solutions

1. Column parity = 1101011011000100. Row parity = 10001. Final parity bit = 0.
2. Flipped bit = 3,4.
3. Yes, a single flipped bit can be detected and corrected with 2D parity.

---

### Error Detection and Correction: Cyclic Redundancy Check

Consider the Cyclic Redundancy Check (CRC) algorithm discussed in Section 6.2.3 of the text. Suppose that the 4-bit generator (G) is 1001, that the data payload (D) is 10011101 and that r = 3.

#### Focused Questions

1. Compute the CRC remainder R for D = 10011101, G = 1001, and r = 3.

#### Focused Solutions

1. R = 100.

---

### Random Access Protocols: ALOHA

Assume that there are 3 active nodes, each of which has an infinite supply of frames they want to transmit, and these frames have a constant size of L bits. If two or more frames collide, then all nodes will detect the collision.

There are two versions of the Aloha protocol: Slotted and Pure. In this problem we will be looking at the efficiency of these two variations. In the case of Slotted Aloha, frames will be sent only at the beginning of a time slot, frames take an entire time slot to send, and the clocks of all nodes are synchronized.

Please round all answers to 2 decimal places

#### Focused Questions

1. For N = 3, compute pure ALOHA and slotted ALOHA efficiency for p = 0.21 and p = 0.74.

#### Focused Solutions

1. Efficiencies:
   - Pure ALOHA, p=0.21: 0.25
   - Pure ALOHA, p=0.74: 0.01
   - Slotted ALOHA, p=0.21: 0.39
   - Slotted ALOHA, p=0.74: 0.15

---

### Multiple Access Protocols: Collisions

![Untitled](img/interactive2/Untitled%2011.png)

#### Focused Questions

1. For ALOHA and slotted ALOHA, give transmission start times and successful frames.
2. For CSMA without collision detection, give start times and successful frames.
3. For CSMA/CD, give start times, successful frames, and stop times for collided packets.

#### Focused Solutions

1. ALOHA:
   - Times: 0.2,0.9,1.4,1.5,1.8,2.2,2.5,2.9,3.2,4.9
   - Successful frames: 10  
   Slotted ALOHA:
   - Times: 1,1,2,2,2,3,3,3,4,5
   - Successful frames: 9,10
2. CSMA:
   - Times: 0.2,s,s,s,1.8,s,s,s,3.2,4.9
   - Successful frames: 1,5,9,10
3. CSMA/CD:
   - Times: 0.2,s,s,s,1.8,s,s,s,3.2,4.9
   - Successful frames: 1,5,9,10
   - Stop times: x,x,x,x,x,x,x,x,x,x

---

### Link Layer and Network Layer Addressing and Forwarding

![Untitled](img/interactive2/Untitled%2012.png)

#### Focused Questions

1. At point 6, give source MAC, destination MAC, source IP, and destination IP.
2. Explain whether MAC addresses change across point 5.

#### Focused Solutions

1. At point 6:
   - Source MAC: 90-54-8A-61-C5-F5
   - Destination MAC: 0E-F7-40-E8-B7-25
   - Source IP: 128.119.40.206
   - Destination IP: 128.119.40.64
2. No. The datagram stays within the subnet, so link-layer forwarding can happen directly.

---

### Learning Switches - Basic

![Untitled](img/interactive2/Untitled%2013.png)

#### Focused Questions

1. For t = 1 through t = 4, summarize which new switch-table entries are learned by switch 1 and switch 2.

#### Focused Solutions

1. Learned entries:
   - t=1: switch 1 learns C,3 and B,2; switch 2 learns C,8
   - t=2: switch 1 learns H,7 and D,4; switch 2 learns H,11 and D,8
   - t=3: switch 1 learns A,1; switch 2 observes no new useful entry
   - t=4: switch 1 observes nothing; switch 2 learns K,14

---

### Learning Switches - Advanced

![Untitled](img/interactive2/Untitled%2014.png)

#### Focused Questions

1. For t = 1, 2, 5, and 7, identify the communicating nodes where enough information is available.

#### Focused Solutions

1. Results:
   - t=1: L
   - t=2: n/a
   - t=5: K,L
   - t=7: D,G

---

