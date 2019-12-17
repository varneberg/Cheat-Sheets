# EJPT Cheat Sheet

## 1 Introduction

### 1.1 Terms

- White hat: Legal hacker
- Black hat: Illegal hacker
- User: A computer system user
- Malicous user: A user misusing systems and applications for attack
- Root/Admin: Users with maximum priviledge
- Security through obscurity: Security of design provide security
- Attack: Action aimed at misusing or taking control over a computer system
- Priviledge escalation: When a malicous user gains elevated priviledges over a system
- Dos: Denial of service
- RCE: Remote code execution
- Shellcode A custom code providing the attacker a shell on a victims machine

### 1.2 Crytography

- Clear text is data sent without any encryption
  - Lets attacker eavesdrop
  - Should not be used for critical or sensitive data
  - If no other alternative, use only on trusted networks

- Cryptographic protocols encrypts the data
  - Attackers are not able to eavesdrop
  - Should always be used for sensitive or private data

- Use clear-text protocols on untrusted networks?
  - Wrap(tunnel) a cleartext protocol into a cryptographic one

### 1.3 VPN

- Virtual private network
- Uses cryptography to extend private network over a public network
  - Client --(VPN)--> Internet --> Private network

### 1.4 Binary Arithmethic Codes

#### 1.4.1 Binary Conversion

- 0 and 1
- 1 + 1 = 10
- 111 + 1 = 1000

- From decimal to and from binary:
  - $293 = 3*10^0 + 9*10^1 + 2*10^2$
  - $1101 = 1*2^0 + 0*2^1 + 1*2^2 + 1*2^3 = 13$
  - Divide by 2 and keep note of remainder
  - Do the same with previous and keep note of remainder
  - Do thid until remainder is 0
  - What is 13?
    - $13/2 = 6$ (1)
    - $6/2  = 3$ (0)
    - $3/2  = 1$ (1)
    - $1/2  = 0$ (1)
    - **1101**

#### 1.4.2 Logical Operators

- **NOT**
  - Flips bits
  - **NOT** 1101 = 0010
- **AND** 
  - IF both bits are 1, resulting bit is 1. Otherwise 0
  - 1001 **AND** 1100 = 1000
- **OR**
  - If atleast one bit is 1, the resulting bit is 1
  - 1001 **OR** 1100 = 1101
- **XOR**
  - If just one of the bits are 1, resulting bit is 1
  - 1001 **XOR** 1100 = 0101

### 1.5 Hexadecimal

- 1 to 9, A-F
- Add 0x or h at the end to distinguish
- Converting hexadecimals to decimals:
  - 0x3a1 = 0x(3101) = $1*16^0 + 10*16^1 + 3*16^2 = 929$
  - $1019 = 1019 / 16 = 63,6875$
    - $0,6875*16 = 11$
  - $63/16 = 3,9375$
    - $0,9375*16 = 15$
  - $3/16 = 0,1875$
    - $0,1875 * 16 = 3$
  - **=0x3FB**
- Use converters online for this instead

## 2 Networking

### 2.1 Protocols

- Machines talk to each other by means of protocols

#### 2.1.1 Packets

- Carries information between networked computers
- Consists of a header and a payload
- **Header**
  - Has protocol-specific structure that makes sure the host can correctly interperet the payload
- **Payload**
  - The actual information of the package

- **The IP Header**
  - Atleast 160 bits long
  - First four bits are IP version(4 or 6)
  - 32 bits ad position 96 represent source address
  - Following 4 bytes represent destination address

#### 2.1.2 Protocol Layers

- **ISO layers:**
  1. Application
  2. Presentation
  3. Session
  4. Transport
  5. Network
  6. Data Link
  7. Physical

- Each layer encapsulates a package with its own header
- The recieving host does the same in reverse

### 2.2 IP

- TCP/IP
- Delivering datagrams
- Each host has a unique address

- Reserved IP's:
  - 0.0.0.0 - 0.255.255.255 is This network
  - 127.0.0.0 - 127.255.255.255 is Local host
  - 192.168.0.0 - 192.168.255.255 us reserved for private networks

#### 2.2.1 IP/Mask

- Identifies a network part and host part of an IP address
- Perform bitwise AND operation between the netmask and the IP address
- **Network Prefix:**
  - 192.168.32.0/255.255.224.0
- **CIDR Notation**
  - 192.168.32.0/19
- Subnet calculators

#### 2.2.3 IPv6

- IPv6 has 128 bit addresses compared to IPv4's 32 bit
- Consists of 16-bit hexadecimal numbers seperated by a ":"
  - Case insensitive
  - Can be skipped if zero occur

- Several representations:
  1. **Regular form:** 1080:0:FF:0:8:800:200C:417A
  2. **Compressed form:** FF01:0:0:0:0:0:0:43 --> FF91::43

- Also has reserverd addresses
- Can be split in half into network part and a device part
  - First 64 bits ends with a 16-bits space that can only be used for specifying a subnet

- **Scope and address types of IPv6**
  - Global Unicast Address
    - Scope: Internet-Routed on Internet
  - Unique Local
    - Scope: Internal network or VPN, internally routable but not routed on Internet
  - Link Local
    - Scope: Network link-Not routed internally or externally

- Translating IPv6 to binary
  - One 4-digit hex work represents 16 binary digits
  - Bin 0000000000000000 = Hex 0000
  - Bin 1111111111111111 = Hex FFFF
  - Bin 1101010011011011 = Hex D4DB

- IPv6 addresses has a dedicated subnetting portion
  - First 48 bits are global addressing
  - The 16 next are defining subnets
  - The last 64 bits are for device(interface) ID's

- Prefixes
  - In IPv6, prefixes instead of subnet blocks
  - 2001:1111:1234:1234::/64
    - The number after slaggs is the number of bits that is used for a prefix
    - Everything else behind it can be used for hosts of the subnet

### 2.3 Routing

- Routers are connected to different networks at the same time forwaring datagrams from one network to another
- Forwarding policy based on routing protocols

- Routers use routing tables to find the right forwarding policy
- Routes to network matching the address of the packet, if no matching entry in table, send to default 0.0.0.0

- If two paths have the same number of hops, routing metrics ensures the fastest is selected
- Every host also stores their own routing table

### 2.4 Link Layer Devices and Protocols

- Link layer is the lowest stack of TCP/IP stack
- Packet forwarding also occurs her

- Hubs and switches are network devices that forward frames on a local network wit link layer network addresses: **MAC addresses**
  - Mac addresses uniquely identify network cards at layer 2
  - Media Access Control
  - Also known as the physical address
  - 48 bits long expressed in hex
  - Each host on a network has both an IP address and a MAC address

- Sending a packet from one network to another:
  - The sender creates a packet with:
    1. The destination IP address of the reciever in the header of the datagram
    2. The destination MAC address of the router in the link layer header of the frame
    3. The source IP address of the sender
    4. The source MAC address of the sender
  - The router then takes the packet and forward it to the recievers network, rewriting the packet's MAC addresses 
    - The destination MAC address will be the recievers address
    - The source MAC address will be the router's 

- Broadcast MAC address
  - A frame with this address is delivered to all the hosts in the local network

#### 2.4.1 Switches

- Switches works with mac adresses
- Multiple interfaces
- Forwarding table
- Learns of new hosts dynamically by inspecting packet headers

#### 2.4.2 Forwarding tables

- Content addressable memory table(CAM)
- Contains:
  - MAC addresses
  - Interface tied to MAC addresses and a time to live(TTL)
- Stored in the devices RAM, and is constantly refreshed
- TTL is how long an entry will stay in the table
- TTL is important because CAM's have finite sizes
- Source MAC addresses are compared in the to the entries in the CAM table for all packets
  - If source is not in the table, the switch will add a new MAC interface binding in the table
  - If it exists in the table, TTL is updated
  - Updates if MAC is bound to another interface

#### 2.4.3 Forwarding

- To forward a packet:
  1. Switch reads destination MAC address of frame
  2. Looks in the CAM table
  3. Forwards to corresponding interface
  4. If no entry with that MAC address, the switch forwards the frame to all interfaces

#### 2.4.4 Address Resolution Protocol(ARP)

- Makes hosts able to build correct IP address - MAC address bindings
  
- Host A wants to send traffic to B, but only knows the IP address of B:
  1. A builds an ARP request containing the IP of B and FF:FF:FF:FF as destination MAC address. This makes the switch forward it to all hosts
  2. Every host recieves the requests
  3. B replies with an ARP reply to A, telling it's MAC
  4. A then saves the the IP-MAC in its ARP cache

#### 2.4.5 Hubs

- Just repeaters forwarding packets by repeating the electrical signal it recieves

### 2.5 TPC/UDP

- Transmission control protocol 
- User datagram protcol

- IP protocol suite using TCP is called TCP/IP
- Characteristics of TCP and UDP:
  - TCP:
    - Lower throughput
    - Connection oriented
    - Guarantees delievry
  - UDP:
    - Better throughput
    - Connectionless
    - Does not guarantee packet delivry

#### 2.5.1 Ports

- Used to identify single network process on a machine
- **IP** : **Port**
  - 0.0.0.0:80

#### 2.5.2 TCP and UDP Headers

- Two fields
  - Source
  - Destination ports
- Tells the server or client what port to use

#### 2.5.3 TCP Three Way Handshake

- Header fiels involved:
  - Sequence number
  - Acknowledgment number
  - SYN and ACK flags

- Procedure:
  1. Client sends TCP packet with SYN flag enabled and a random sequence number
  2. Server responds with SYN and ACK flags set, and a random sequence number
     - ACK number is always an increment of recieved SYN
  3. Client completes synchronization by sending ACK

### 2.6 Firewalls and Network Defence

#### 2.6.1 Firewalls

- Software filtering packets
- Access control on different layers of the OSI model
- Filters according to rules:
  - Source IP
  - Destination IP
  - Protocol
  - Source port
  - Destination port
  - etc..

- Packet filters inspects headers to determine what to do:
  - Allow
  - Drop - No notifying to server
  - Deny - Notifying server

- **Problem**: Headers give no information on content data of packet

- Attack example:
  - Company hosts a web server
  - Firewall allows all incoming traffic from internet and direct it to port 80
  - Application exploits go through because firewall can not see the difference between web browsing and web exploit
//TODO

### 2.7 DNS

- Domain Name System
- Application layer protocol
- Converts human-readable names to IP addresses

- A DNS name can be broken down into:
  - Top level domain(TLD)
  - Domain name
  - Subdomain name
  - Host name

- Name resolution performed by resolvers
  - Servers contacting top level domain and follows the hiarchy to resolve the name of the host
  - ISP or publicly available
- OS must contact a resolver to break down DNS into IP address

- DNS resolution algorithm:
  1. Resolver contacts root name servers
  2. Then asks TLD name server what the authoritive name server is that can give information about the domain it seeks
  3. If there are more subdomains, step 2 is performed again on the authorotive DNS server for every subdomain
  4. Finally the resolver asks for the name resolution for the host part

- IP addresses of the root servers are hardcoded in to the configuration of the resolver, and needs to be updated to work

- DNS can also reverse an IP address to a DNS name

### 2.8 Wireshark

#### NIC Promiscuous Mode

- Network interface cards
- A NIC will accept and process any packet it recieves
- To sniff other ethernet traffic, ARP poisoning or Mac flooding must be performed
- **Capture filters** downsizes the amount of traffic gathered
- **Display filters** allows granular filters to every field of the captured packets

## 3 Web Applications

### 3.1 HTTP

- Hyper text transfer protocol
- Transfers web pages and web application data
- Works on top of the TCP protocol

- HTTP message format:
  - Headers\r\n
  - \n\n
  - Message Body\r\n

- HTTP Header fields:
  - **Request method**
    - Type of request(GET, PUT, TRACE, HEAD, POST, etc)
  - **Host**
    - Internet hostname and port number
  - **User-Agent**
    - Client software and OS issuing request
  - **Accept**
    - What  document type it is expecting in response
  - **Accept Language**
    - Specific human language in response
  - **Accept Encoding**
    - Restricts content encoding
  - **Connection**
    - Desired properties for current connection

- Server sends response after client request:
  - **Status Line**
    - Status codes
  - **Date**
    - Date and time request message was originated
  - **Cache-Control**
    - Tells the client about cached content
  - **Content-Type** 
    - Tells the client how to intereperet the message
  - **Content-Encoding**
    - Extends content type
  - **Server**
    - Contains header of server who generated response
  - **Content-Length**
    - Length of content in bytes

### 3.2 HTTPS

- HTTP Secure
- HTTPS over TLS
- Encryption layer
  - Cannot sniff application layer communication
  - Cannot alter application layer data
  - Server and client can authenticate eachother

- An adjacent network user will not be able to recognize:
  - Request headers, body and domain
  - Response headers, body
- He coulf be able to recognize:
  - Target IP
  - Target Port
  - DNS

- Does not protect against web application flaws!

### 3.3 HTTP Cookies

- Textual information stored in the servers cookie jar
- A cookie contains the following attributes:
  - The actual content
    - ID=value 
  - An expiration date
    - expires=.......
  - A path
    - path=/...../..
  - The domain
    - domain=.example.com
  - Optional flags:
    - Http only flag
    - Secure flag

#### 3.3.1 Cookie Domain

- Cookies are sent only to their valid domain/path if they are not expired and according to their flags
- The domain field sets the scope of the cookie, browser only sends cookie if it is for the right domain
- When a cookie has the domain attribute set to:
  - domain=example.com or .example.com, the browser will send the cookie to the site and whatever else subdomains within the scope

- If the server does not specify the domain attribute, the browser automatically set the domain of the server domain, and set the host  only domain flag

#### 3.3.2 Cookie Expiration

- Expires is the validity timer for the cookie
- Browsers will not send expired cookies to servers

#### 3.3.3 Cookie Http-Only Attribute

- Prevents any other language than HTTP to read from the cookie

#### 3.3.4 Cookie Secure Attribute

- Secure flag creates secure cookies only sent over HTTPS

#### 3.3.5 Cookie Protocol

- Servers sends Set-Cookie response in header field. telling the browser to install the cookie
- For every subsequen request the browser considers:
  - Domain
  - Path
  - Expiration
  - Flags
- If all pass, the browser will insert a cookie: header in the request
  
### 3.4 Sessions

- Server side stored variables
- Identified by an ID or Token
- Clients presents this ID for all requests, being recognized by the server

- Web servers install session ID's by using session cookies
  - Single parameter referring to the session
  - Each language has their own session parameter name

- Session IDs can also transmitted via GET requests

#### 3.5 Same Origin Policy

- Prevents JavaScript code from getting or setting properties on resource coming from a different origin
- To determine if JavaScript can access a source, the browser uses:
  - Protocol
  - Hostname
  - Port
- All must match!
- Only works for the actual script, HTML tags are still vulnerable

## 4 Scripting

### 4.1 Important Windows Commands

- **Output redirection:**
  - echo aaa > output.txt

- **Execute two commands regardless of eachother:**
  - [Command1] & [Command2]

- **Execute two commands where the other executes if the other succeeds:**
  - [Command1] && [Command2]

- **To create larger command line scripts, save them as .bat with one command per line**

- **List all files in a directory:**
  - for %i (*.*) do @echo FILE: %

## 5 Information Gathering

### 5.1 Open-Source Intelligence

#### 5.1.1 Social Networks

- Easiest way to gather information about employees
- Important to select the correct social media depending on client
- Integration between social media profiles can help you find important information on one site, unnavailable on the other
  - Twitter and LinkedIn can be used to autheticate eachother
  - LinkedIn displays full name along with email

#### 5.1.2 Public Sites Information Gathering

- **CrunchBase**
  - Information about founder, investors, employees, buyouts and acquisitions

- **Government sites**

- **Whois**
  - Command on OSX and Linux
  - Displays information stored in the whois database
  - Used on internet domains

#### 5.1.3 Browsing Client´s Sites

- Products
- Services
- Technologies
- Company culture
- Employees profiles

#### 5.1.4 Email Patterns 

- Many companies uses internal email schemas for employees
- Often:
  - name.surename@company.com
  - surname.name@company.com

- Some systems informs the sender if an email address does not exist
  - Gather names of employees in the company
  - Try different combinations of first- and surnames
  - Send non suspicous mails to the different addresses and observe what the addresses return
  - If some of the addresses return a failed mail request notification, you can disregard it, and find the actual addresses

### 5.2 Subdomain Enumeration

- Enumerate to find new resources
- Widens the attack surface
- Common for companies to share the same top level domain name
  - e.g careers.company.com, mail.company.com
  - May be outdated

- Passive subdomain enumeration
  - Identifying subdomains without directly interracting with the target
  - Interracting through open sources such as search engines
  - Google for example may index pages that were not meant to be indexed
    - site:company.com

- **dnsdumpster.com**
- **sublist3r**
  - Collects DNS data

## 6 Footprinting and Scanning

### 6.1 Mapping Networks

- Enumeration process to find nodes from IPs
  - What is a client and server?

- Ping sweeping:
  - Sending echo requests(IMCP packets) to hosts to see who is alive
  - It it replies with an echo reply packet, the host is alive
  - Fping
    - Linux ping sweeper
      - *Fping -a -g 10.54.12.0/24*

#### 6.1.1 nmap

- **-sn**
  - Ping scan
    - *nmap -sn 200.200.0.0/16*
- **-il**
  - Save host list to file and use as input
    - *nmap -sn -iL hostslist.txt*
- **-Pn**
  - Skips the ping scan
  - If you allready know the targets are alive
- **-O**
  - OS fingerprinting
  - Determining which OS the host is running
  - Sends a series of specifically crafted requests to hosts and examines every bit to find OS signatures
    - *nmap -Pn -O <target(s)>*
  - Limit to promising hosts
    - *nmap -O --osscan-limit <targets>*
