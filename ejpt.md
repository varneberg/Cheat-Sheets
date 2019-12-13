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