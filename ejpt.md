# EJPT Cheat Sheet

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

