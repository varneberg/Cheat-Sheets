# INF140 Summary

## Overview of Cybersecurity

### What is cybersecurity
  
* U-S.Department of Commerce:
  * The protection of information against unauthorized disclosure, transfer, modification, or destruction, whether accidental or intentional

* Wikipedia:
  * The protection of computer systems from the theft of or damage to their hardware, software, or electronic data, as well as from the disruption or misdirection of the services they provide

* U.S.NIST:
  * The protection afforded to an automated information system in order to attain the applicable objectives of preserving the integrity, availability and confidentiality of information system resources

### Key questions in cybersec
  
* What do we want to protect
* Why do we need to protect them
* How can we protect them

### CIA Triad
  
* Confidentiality
  * Data cannot be read by unauthorized entities
  * Systems cannot be accessed by unauthorized entities

* Integrity
  * Data integrity: Data cannot be modified in an unauthorized and undesired manner
  * System integrity: Performs its intended function in an unimpaired manner, free from deliberate or inadvertent unauthorized manipulation of the system

* Availability
  * Systems work promptly and service is not denied to authorized user

### Pakerian hexad
  
* Information security
  * Authenticity
    * The proper attribution to the owner or creator of the data in question
  * Availability
  * Utility
    * How useful the data is to the owner
  * Confidentiality
  * Possession
    * The physical disposition of the media on which the data is stored
  * Integrity

### Security attributes

* Assets
  * Confidentiality, integrity, availability
  * Utility, possession, authenticity
  * Accountability/Non-repudiation
  * Authentication
  * Privacy
  * Anonymity

### What can adversaries do
  
* Bot activity
* Account credentials
* Financial credentials
* Hostage attacks
* Reputation hijacking
* Virtual goods
* E-mail attacks
* Web server

### Security vs privacy
  
* Security as term covers several attributes of assets
* Privacy is the control of what kind of information to be disclosed to whom/which entity to what extent

### Vulnerabilities
  
* A weakness in a system that allows a threat source to compromise its security
  * e.g no encryption
  * weak password

### Security threats
  
* Any potential danger that is associated with the exploitation of a vulnerability
  * Malware
  * Hacking tool kits
  * Remote access Trojans
  * Ransomware, spyware
  * Phishing
  * Mass surveillance

### Security risks (vulnerabilities x threats x impacts)
  
* The likelihood of a threat source exploiting a vulnerability and the corresponding impact from compromise of security principles/attributes
  * e.g a weak password has a high likelihood of being easily cracked and data falls in the hands of unauthorized individuals

### Security controls(countermeasures, safeguard)
  
* Actions that are put into place to mitigate or reduce the potential risk
* Administrative controls
  * Personnel training
  * Law/regulation enforcement
* Physical protection
  * Fence, locked gates
  * Security guards
* Technological controls
  * Cryptography
  * Security protocols
  * System mechanisms(firewall, access control, ...)

### Multi-layered defense
  
* Makes it more difficult for adversaries to further penetrate into the network
* Buys time to detect and mitigate the attack

### Security control protections
  
* Preventive
* Detective
* Corrective
* Deterrent
* Recovery
 
### Risks

* Physical damage
* Human interaction
* Equipment malfunction
* Internal and external attacks
* Misuse of data
* Application errors

#### Risk management

* A process of identifying and assessing risk, but also reducing it to an acceptable level and remaining at that level
* Procedures:
  * Frame risk
  * Assess risk
  * Respond to risk
  * Monitor risk
  
#### Risk assessment
  
* Risk = vulnerability x threat x impact
  * Detailed examination of the components of risk used to ensure that security is cost effective, relevant, timely and responsive to threats
  * Goals:
    * Identify assets and their value to the organization
    * Determine the likelihood that a threat exploits a vulnerability
    * Determine the business impact of these potential threats
    * Provide a resource balance between the impact of the threat and the cost of countermeasure
  * Ultimate goal: Provide cost-effective countermeasure according to risks

#### Quantitative and qualitative analysis

* Quantitative: Each element in the analysis is quantified and entered into equations to determine total and residual risk

* Qualitative: Assign ratings instead of numeric quantities to the risk
* Residual risk = total risk - countermeasure

### Threat models
  
* Data:
  * Data at rest
  * Data in transit
  * Data in use
* Humans:
  * Social engineering
  * Password misuse
  * Social network
* Threats:
  * Malicious adversaries seeking vulnerabilities over time by examining system
  * Insider
  * Natural damage
* Attack tree:
  * Set of attacks that associate a threat source and vulnerabilities

## Identification and Authentication

### Identification
  
* A process that presents an identifier to others or systems
  * Expected to be unique but not necessarily secret

### Requirements on Identification

* Each value should be unique for user accountability
* The value should not be shared
* A standard naming scheme should be followed
* The value should be non descriptive of the user's position or tasks

### Authentication

#### User Authentication

* A process that verify the binding between a claimed entity with some attributes/information such as:
  * Password, PIN, security token, bio metric information that cannot be provided by others
* User authentication is the primary line of the defense in computer security
* Other security tools rely on user authentication

#### Means of Authentication

* Knows
  * Password, PIN ...
* Possesses
    Token, key card, smart card ....
* Is
  * Static bio metrics
* Does
  * Dynamic bio metrics

#### Password Bases Authentication

* Many systems rely on a combination of user ID and password
* System stores username and password initially
* User submits username/password to system and the system compares against stored values
* ID :
  * Determine whether the user is authorized to gain access
  * Determines privileges of user(e.g normal or superuser)
  * User in access control to grant permissions to resources for user 


## Firewalls

### Why firewalls

* Effective for protecting LANs
* Establishes a controlled link between the premises network and the internet
* Used as a perimeter defense:
  * Single choke point to impose security and auditing
  * Insulates the internal systems from external networks

### Firewall characteristics
  
* Design goals:
  * All traffic from inside to outside must pass through the firewall
  * Only authorized traffic as defined by the local security policy will be allowed to pass
  * The firewall itself is immune to penetration
* General techniques:
  * Service control(e.g filter based on IP-address, port number)
  * Direction control(e.g internal LAN, to external internet)
  * User control(e.g student vs faculty)
  * Behavior control(e.g. filter emails)

### Firewall capabilities
  
* Defines a single choke point
* Provides a location for monitoring security events
* Convenient platform for several internet functions that are not security related
* Can server as platform for VPN end-point

### Firewall limitations
  
* Cannot protect against attacks bypassing firewall
* May not protect fully against internal threats
* Improperly secured wireless LAN  can be accessed from outside the organization
* Laptop, phone, or USB drive may be infected outside the corporate network then used internally

### Types of firewalls
  
* Packet filtering: Accepts/Rejects packets based on protocol headers
* Stateful Packet Inspection: Adds state information on what  previously happened to a packet filtering firewall
* Application proxy: Relay for application traffic
* Circuit-level Proxy: Relay for transport connections

#### Packet Filtering Firewall
  
* Security policy implemented by set of rules
* Rules define which packets can pass through the firewall
* Firewalls inspects each arriving packet(all directions), compares to rule set, and takes actions according to those rules
* Default policies: Actions for packets for which no rule matches(Drop packet is recommended)

##### Packet filtering rules
  
* Packet Information
  * IP address
  * Port number
  * Protocol number
  * Firewall interface: Identifies immediate source/destination
  * Other transport, network, data link packet header fields

* Rules
  * Conditions defined using packet information, direction
  * Wildcards(*) support to match multiple values
  * Actions typically accept or drop
  * List of rules processed in order

#### iptables

* Linux
* Packet filtering firewall
* netfilter: module for filtering packets in Linux kernel
  * iptables: User space application to manipulate packet filters of netfilter
  * Administrator privileges needed for manipulating kernel packet filter

#### iptables concepts

* Different tables of filters(depending on kernel config)
  * Selected using -t options(filter, nat, mangle)
  * Tables contains chains

#### iptables Chains

* Different rules depending on how/where packet processed by the Linux kernel
  * INPUT
  * OUTPUT
  * FORWARD
  * PREROUTING
  * POSTROUTING

#### iptables rules

* Packet filtering rules
* Consists of:
  * **Matching conditions** desired packet characteristics
    * Protocol, source/destination address, interface
    * Protocol specific extensions
  * **Target** action to take if packet matches specified conditions
    * ACCEPT, DROP, RETURN ...
  * Packets are checked against rules in chain, from 1st to last
  * If rule does not match, check against next rule in chain
         If rule matches, take action as specified by target

#### Common iptables Syntax

* ```iptables -t tables -operation chain -p protocol -s srcip -d dstip-i inif -o otif -param1 value1 ... -j target```
  * tables: filter, nat, mangler
  * operation: Append, Delete, Insert, List, Flush, Policy
  * Chain: INPUT, OUTPUT, FORWARD, PREROUTING, POSTROUTING
  * Protocol: tcp, udp, all, ...
  * srcip, dstip: IP address 0.0.0.0/24
  * inif, outif: interface name
  * param, value: protocol specific parameter and value
  * target: ACCEPT, DROP, RETURN

#### Issues with Packet Filtering Firewalls

* Advantages
  * Simplicity
  * Transparent to users
  * Very fast

* Disadvantages
  * Cannot prevent attacks that employ application specific vulnerabilities or functions
  * Do not support advances user authentication
  * Vulnerable to attacks on TCP/IP protocol bugs
  * Improper configuration can lead to breaches

### Stateful Packet Inspection

* Traditional packet filtering firewalls makes decisions based on individual packets and does not consider past packets(stateless)
* Many applications establish a connection between client/server. Group of packets belong to a connection
* Often easier to define rules for connections, rather than individual packets
* Needs to store information about past behavior(stateful)
* Stateful packet inspection(SPI) is an extension of traditional packet filtering firewalls
* Issues: Extra overhead required for maintaining state information
* For connections accepted by packet filtering firewall, record connection information
  * src/dest IP address src/dest port, sequence number, connection state (e.g. Established closing)
* Packets arriving that belong to existing connections can be accepted without being processed by firewall

### Application proxy

* Application-level Gateway
* Acts as a relay of application-level traffic
  * User contacts gateway using a TCP/IP application
  * Gateway contacts application on remote hos and relays TCP segments between server and user
* Must have proxy code for each application, may restrict application features supported
* Tend to be more secure than packet filters
* Disadvantage is the additional processing overhead on each connection

### Circuit-level proxy

* Circuit-level Gateway
* Sets up TCP connections, one between itself and a TCP user on an inner host and one on an outside host
* Relays TCP segments from one connection to the other without examining contents
* Security function consists of determining which connections will be allowed
* Typically used when inside users are trusted
* May use application-level gateway inbound and circuit-level gateway outbound, lower overheads

### Firewall Architecture

* Firewalls can be located on hosts: end-users computers and servers
* In networks with a large number of users, firewalls are located on network devices that interconnect internal and external networks
* Common to separate internal network into two zones:
  1. Public-facing servers
  2. End-user computers and internal servers
* Public-facing servers are put in the DE-Militarized Zone (DMZ) 

### General Firewall Issues

* Complexity and human error
  * Writing firewall rules that implement the security policy is difficult for large networks
* Bypassing security policies using tunnels
* Bypassing firewalls using other networks or devices

## Authentication in Networks

### Overview of authentication
  
* Authentication is an important mechanism for access control
* Controls access/usage of resources in local and remote systems
* What to authenticate:
  * User authentication to get access to local/remote resource
  * Entity authentication communicating with each other and claiming tobe who they are

### Authentication in WPA2

* Phase 1 - Discovery
* Phase 2 - Authentication
* Phase 3 - Key management
* Phase 4 - Protected data transfer
* Phase 5 - Connection termination

### Entity authentication in networks
  
* Usually implemented by authentication protocols
* Designed for transfer of authentication data between two/multiple entities
* Allows the receiving entity to authenticate the connecting entity(client/server server/client)
* **The most important layer of protection for secure communication within networks**

### Types of authentication protocols
  
#### Secret info-based authentication

* Point-to-point protocols
* PAP(password-based authentication protocol)
* CHAP(Challenge-handshake authentication protocol)
* EAP(Extensible authentication protocol)

##### AAA architecture protocols

* Remote authenticate dial-in user service(RADIUS)
* Kerberos
  * Mostly for LAN
* Public info-based authentication
* TLS/SSL, PGP
  * Mostly for the internet

##### 892.1X(EAPOL)
  
1. EAP data is encapsulated in EAP over LAN (EAPOL)
2. Then re-encapsulated between the authenticator and thauthentication server using RADIUS/Diameter
3. The supplicant is approved/rejected to access resources

##### Extensible Authentication Protocol(EAP)
  
* Authentication framework
* Not a specific authentication mechanism
* Provides common features and negotiation of authentication methods
* Approximately 40 commonly used EAP methods(e.g EAP-TLS, EAP-TTLS, EAP-PSK, EAP-IKEv2)
* EAP peer:
  * Client computer/supplicant
* EAP authenticator:
  * An access point or NAS that requires EAP authentication prior to granting access to a network

* Authentication server:
  * A back-end server that negotiates the use of a specific EAP method with an EAP peer, validates the EAP peer's credentials, and authorizes access to the network
  * **EAP message may include:**
    * Code: identifies the type of EAP message
    * Identifier: Matches responses with requests
    * Length: Indicates the EAP message in octets(code, identifier, length and data fields)
    * Data:
      * Information related to authentication, often Type sub field for indicating the type of data carried and Type-Data field

##### RADIUS
  
* AAA(authentication, authorization and accounting) protocol that manages network access
* Two packet types to manage the full AAA process
  * Access-Requests manages authentication and authorization
  * Accounting-requests manages accounting
  * RADIUS server checks that the information is correct using authentication schemes such as PAP, CHAP
    * Decision:
      * Reject/Accept/Challenge/asking additional information from the user
    * RADIUS Roaming:
      * Realms: Identify where the RADIUS server should forward the AAA requests for processing
      * Proxy operation: Forward the request to the configured home server for the domain/realms information in the request

### Virtual Private Network (VPN)
  
* Allows remote users to access applications and resources outside of the physical network
* Goal:
  * Enable users to transfer data across public network as if they were directly connected to the private network
* Benefits:
  * Remote end system benefits from the functionality, security, and management of the private network
* Implementation:
  * Connection to private network is established using an encrypted layered tunneling protocol
  * VPN users use authentication methods, including passwords or certificates to gain access to the VPN

### Tunneling
  
* Communication protocol that allows for the movement of data from one network to another
* Involves allowing private network communications to be sent across a public network through a encapsulation process
  
### Network access server(NAS)
  
* Functions as an access control point for users in remote locations connecting to an enterprise's internal network
* May include own authentication services or rely on a separate authentication service from the policy server

### Network Access Enforcement Methods
  
* Enforcement methods are the action that are applied to ARs to regulate access to the enterprise network
* Common NAC enforcement methods:
  * IEEE 802.1X
  * Virtual local area network(VLANs)
  * Firewall: Provides a form of NAC by allowing or denying network traffic between an enterprise host and an external user
  * DHCP Management

## Public Key Certificates

### Distribution of Public Keys

* Public keys are made public by design
* Issue: How to ensure public key of A actually belongs to A
* For approaches for distributing public keys
  1. Public announcement
  2. Publicly available directory
  3. Public-key authority
  4. Public-key certificates

#### Public announcements

* Make public key available in open forum
* Problem: Anyone can announce a key pretending to be another user

#### Publicly Available Directory

* All users publish keys in central directory
* Users must provide identification when publishing key
* Users can access directory electronically
* Weakness: Directory must be secure

#### Public-Key Authority

* Specific instance of using publicly available directory
* Assume each user has already security published public-key at authority; each user knows authorities public key
* Problem: authority can be bottlenecked
* Alternative: public-key certificates

#### Public-Key Certificates

* Assume public keys sent to CA can be authenticated by CA; each user has certificate of CA
* A certificate is the ID and public-key of a user signed by CA
  * $C_A=E(PR_{auth},[T || ID_A || PU_a])$
  * Time-stamp T validates currency of certificate(expiration date)
* Common format for certificates is X.509 standard
  * S/MIME(mail)
  * IP security(network layer)
  * SSL/TLS(transport layer)
  * SET(e-commerce)

### X.509 Certificates

* Each user has a certificate, although it is created by the Certificate Authority(CA)
* Certificates are stored in a public directory
* Certificate format includes:
  * Version of  X.509
  * Serial number unique to the issuer (CA)
  * Signature algorithm
  * Issuer's name and unique identifier
  * Period of validity
  * Subject's name and unique identifier
  * Subject's public-key information: algorithm, parameters, key
  * Signature
* Certificates may be revoked before expiry
  * CA signs a Certificate Revocation List (CRL), which is stored in a public directory

#### Multiple Certificate Authorities

* Multiple CA's can be arranged in hierarchy

### Public Key Infrastructure

* Public-key certificates
* Chains of CAs up until root CA with self-signed certificate
* Certificate Revocation Lists (CRLs)
* ...

### PGP - Web of Trust

* Users trust other users with their public keys and shares accordingly