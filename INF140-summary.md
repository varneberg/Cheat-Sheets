# INF140 Summary

## Overview of Cybersecurity

* What is cybersecurity?
  * U-S.Department of Commerce: The protection of information against unauthorized disclosure, transfer, modification, or destruction, whether accidental or intentional
  * Wikipedia: The protection of computer systems from the theft of or damage to their hardware, software, or electronic data, as well as from the disruption or misdirection of the services they provide
  * U.S.NIST: The protection afforded to an automated information system in order to attain the applicable objectives of preserving the integrity, availability and confidentiality of information system resources

* Key questions
  * What do we want to protect
  * Why do we need to protect them
  * How can we protect them

* CIA Triad
  * Confidentiality
    * Data cannot be read by unauthorized entities
    * Systems cannot be accessed by unauthorized entities
  * Integrity
    * Data integrity: Data cannot be modified in an unauthorized and undesired manner
    * System integrity: Performs its intended function in an unimpaired manner, free from deliberate or inadvertent unauthorized manipulation of the system
  * Availability
    * Systems work promptly and service is not denied to authorized user

* Pakerian hexad
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

* Security attributes
  * Assets
    * Confidentiality, integrity, availability
    * Utility, possession, authenticity
    * Accountability/Non-repudiation
    * Authentication
    * Privacy
    * Anonymity

* What can adversaries do?
  * Bot activity
  * Account credentials
  * Financial credentials
  * Hostage attacks
  * Reputation hijacking
  * Virtual goods
  * E-mail attacks
  * Web server

* Security vs privacy
  * Security as term covers several attributes of assets
  * Privacy is the control of what kind of information to be disclosed to whom/which entity to what extent

* Vulnerability
  * A weakness in a system that allows a threat source to compromise its security
    * e.g no encryption
    * weak password

* Security threats
  * Any potential danger that is associated with the exploitation of a vulnerability
    * Malware
    * Hacking tool kits
    * Remote access Trojans
    * Ransomware, spyware
    * Phishing
    * Mass surveillance

* Security risks (vulnerabilities x threats x impacts)
  * The likelihood of a threat source exploiting a vulnerability and the corresponding impact from compromise of security principles/attributes
    * e.g a weak password has a high likelihood of being easily cracked and data falls in the hands of unauthorized individuals

* Security controls(countermeasures, safeguard)
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

* Multi-layered defense
  * Makes it more difficult for adversaries to further penetrate into the network
  * Buys time to detect and mitigate the attack

* Security control protections
  * Preventive
  * Detective
  * Corrective
  * Deterrent
  * Recovery

* Risk management
  * A process of identifying and assessing risk, but also reducing it to an acceptable level and remaining at that level
  * Procedures:
    * Frame risk
    * Assess risk
    * Respond to risk
    * Monitor risk
  * Risks:
    * Physical damage
    * Human interaction
    * Equipment malfunction
    * Internal and external attacks
    * Misuse of data
    * Application errors

* Threat models
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
  
* Risk assessment
  * Risk = vulnerability x threat x impact
    * Detailed examination of the components of risk used to ensure that security is cost effective, relevant, timely and responsive to threats
    * Goals:
      * Identify assets and their value to the organization
      * Determine the likelihood that a threat exploits a vulnerability
      * Determine the business impact of these potential threats
      * Provide a resource balance between the impact of the threat and the cost of countermeasure
    * Ultimate goal: Provide cost-effective countermeasure according to risks
    * Quantitative and qualitative analysis
      * Quantitative: Each element in the analysis is quantified and entered into equations to determine total and residual risk
      * Qualitative: Assign ratings instead of numeric quantities to the risk
    * Residual risk = total risk - countermeasure

## Firewalls

* Why firewalls?
  * Effective for protecting LANs
  * Establishes a controlled link between the premises network and the internet
  * Used as a perimeter defense:
    * Single choke point to impose security and auditing
    * Insulates the internal systems from external networks

* Firewall characteristics
  * Design goals:
    * All traffic from inside to outside must pass through the firewall
    * Only authorized traffic as defined by the local security policy will be allowed to pass
    * The firewall itself is immune to penetration
  * General techniques:
    * Service control(e.g filter based on IP-address, port number)
    * Direction control(e.g internal LAN, to external internet)
    * User control(e.g student vs faculty)
    * Behavior control(e.g. filter emails)

* Firewall capabilities
  * Defines a single choke point
  * Provides a location for monitoring security events
  * Convenient platform for several internet functions that are not security related
  * Can server as platform for VPN end-point

* Firewall limitations
  * Cannot protect against attacks bypassing firewall
  * May not protect fully against internal threats
  * Improperly secured wireless LAN  can be accessed from outside the organization
  * Laptop, phone, or USB drive may be infected outside the corporate network then used internally

* Types of firewalls:
  * Packet filtering: Accepts/Rejects packets based on protocol headers
  * Stateful Packet Inspection: Adds state information on what previously happened to packet filtering firewall
  * Application proxy: Relay for application traffic
  * Circuit-level Proxy: Relay for transport connections

* Packet Filtering Firewall
  * Security policy implemented by set of rules
  * Rules define which packets can pass through the firewall
  * Firewalls inspects each arriving packet(all directions), compares to rule set, and takes actions according to those rules
  * Default policies: Actions for packets for which no rule matches(Drop packet is recommended) 

* Packet filtering rules
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

* iptables in Linux
  * Packet filtering firewall
  * netfilter: module for filtering packets in Linux kernel
  * iptables: User space application to manipulate packet filters of netfilter
  * Administrator privileges needed for manipulating kernel packet filter
    * Sudo
  * iptables concepts:
    * Tables:
      * Different tables of filters(depending on kernel config)
      * Selected using -t options(filter, nat, mangle)
      * Tables contains chains
    * Chains

## Authentication in Networks

* Authentication in WPA2
  * Phase 1 - Discovery
  * Phase 2 - Authentication
  * Phase 3 - Key management
  * Phase 4 - Protected data transfer
  * Phase 5 - Connection termination

* Overview of authentication
  * Authentication is an important mechanism for access control
  * Controls access/usage of resources in local and remote systems
  * What to authenticate:
    * User authentication to get access to local/remote resource
    * Entity authentication communicating with each other and claiming to be who they are

* Entity authentication in networks
  * Usually implemented by authentication protocols
    * Designed for transfer of authentication data between two/multiple entities
    * Allows the receiving entity to authenticate the connecting entity(client/server server/client)
    * **The most important layer of protection for secure communication within networks**

* Types of authentication protocols
  * Secret info-based authentication
    * Point-to-point protocols
      * PAP(password-based authentication protocol)
      * CHAP(Challenge-handshake authentication protocol)
      * EAP(Extensible authentication protocol)
    * AAA architecture protocols
      * Remote authenticate dial-in user service(RADIUS)
    * Kerberos
      * Mostly for LAN
  * Public info-based authentication
    * TLS/SSL, PGP
    * Mostly for the internet

* 892.1X(EAPOL)
  * Overview
    1. EAP data is encapsulated in EAP over LAN (EAPOL)
    2. Then re-encapsulated between the authenticator and the authentication server using RADIUS/Diameter
    3. The supplicant is approved/rejected to access resources

* Extensible Authentication Protocol(EAP)
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

* RADIUS
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

* Virtual Private Network (VPN)
  * Allows remote users to access applications and resources outside of the physical network
  * Goal:
    * Enable users to transfer data across public network as if they were directly connected to the private network
  * Benefits:
    * Remote end system benefits from the functionality, security, and management of the private network
  * Implementation:
    * Connection to private network is established using an encrypted layered tunneling protocol
    * VPN users use authentication methods, including passwords or certificates to gain access to the VPN

* Tunneling
  * Communication protocol that allows for the movement of data from one network to another
  * Involves allowing private network communications to be sent across a public network through a encapsulation process
  
* Network access server(NAS)
  * Functions as an access control point for users in remote locations connecting to an enterprise's internal network
  * May include own authentication services or rely on a separate authentication service from the policy server

* Network Access Enforcement Methods
  * Enforcement methods are the action that are applied to ARs to regulate access to the enterprise network
  * Common NAC enforcement methods:
    * IEEE 802.1X
    * Virtual local area network(VLANs)
    * Firewall: Provides a form of NAC by allowing or denying network traffic between an enterprise host and an external user
    * DHCP Managment