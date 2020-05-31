# INF140 Summary

* [INF140 Summary](#inf140-summary)
  * [Overview of Cybersecurity](#overview-of-cybersecurity)
    * [What is cybersecurity](#what-is-cybersecurity)
    * [Key questions in cybersecurity](#key-questions-in-cybersecurity)
    * [CIA Triad](#cia-triad)
    * [Pakerian hexad](#pakerian-hexad)
    * [Security attributes](#security-attributes)
    * [What can adversaries do](#what-can-adversaries-do)
    * [Security vs privacy](#security-vs-privacy)
    * [Vulnerabilities](#vulnerabilities)
    * [Security threats](#security-threats)
    * [Security risks (vulnerabilities x threats x impacts)](#security-risks-vulnerabilities-x-threats-x-impacts)
    * [Security controls(countermeasures, safeguard)](#security-controlscountermeasures-safeguard)
    * [Multi-layered defense](#multi-layered-defense)
    * [Security control protections](#security-control-protections)
    * [Risks](#risks)
      * [Risk management](#risk-management)
      * [Risk assessment](#risk-assessment)
      * [Quantitative and qualitative analysis](#quantitative-and-qualitative-analysis)
    * [Threat models](#threat-models)
  * [Identification and Authentication](#identification-and-authentication)
    * [Identification](#identification)
    * [Requirements on Identification](#requirements-on-identification)
    * [Authentication](#authentication)
      * [User Authentication](#user-authentication)
      * [Means of Authentication](#means-of-authentication)
      * [Password Bases Authentication](#password-bases-authentication)
        * [Storing Passwords in Clear Text](#storing-passwords-in-clear-text)
        * [Storing Passwords as Encrypted text](#storing-passwords-as-encrypted-text)
        * [Storing Passwords as Hashed Text](#storing-passwords-as-hashed-text)
        * [Cracking passwords](#cracking-passwords)
        * [Salting Passwords](#salting-passwords)
        * [Password Storage Best Practice](#password-storage-best-practice)
        * [Passwords Vulnerabilities and Countermeasures](#passwords-vulnerabilities-and-countermeasures)
        * [Other Common Characteristics of Passwords](#other-common-characteristics-of-passwords)
        * [Password Selection Strategies](#password-selection-strategies)
        * [Passwords:  Do’s and Don't s](#passwords-dos-and-dont-s)
      * [Token-Bases Authentication](#token-bases-authentication)
        * [Memory Cards](#memory-cards)
        * [Smart Cards](#smart-cards)
      * [Bio-metric Authentication](#bio-metric-authentication)
  * [Access Control](#access-control)
    * [Access Control and Other Security Functions](#access-control-and-other-security-functions)
  * [Malicious Software](#malicious-software)
    * [Malware (Malicious software/code)](#malware-malicious-softwarecode)
      * [Classification of malware](#classification-of-malware)
    * [Viruses](#viruses)
      * [Compression Virus](#compression-virus)
      * [Types of Viruses By target](#types-of-viruses-by-target)
      * [Propagation of viruses](#propagation-of-viruses)
      * [Types of Viruses by Concealment Strategy](#types-of-viruses-by-concealment-strategy)
    * [Worms](#worms)
      * [Worm Replication](#worm-replication)
    * [Trojan Horses](#trojan-horses)
    * [Types of Malware Damage](#types-of-malware-damage)
      * [Zombies and Bots](#zombies-and-bots)
        * [Use of Botnets](#use-of-botnets)
      * [Information Theft](#information-theft)
      * [Phishing](#phishing)
      * [Other Malware](#other-malware)
    * [Comparison of Malware](#comparison-of-malware)
    * [Malware Countermeasure Approaches](#malware-countermeasure-approaches)
      * [Development of Anti-virus Software](#development-of-anti-virus-software)
      * [Generic Decryption](#generic-decryption)
      * [Host-Based Behavior](#host-based-behavior)
    * [Malware Security Issues](#malware-security-issues)
  * [Firewalls](#firewalls)
    * [Why firewalls](#why-firewalls)
    * [Firewall characteristics](#firewall-characteristics)
    * [Firewall capabilities](#firewall-capabilities)
    * [Firewall limitations](#firewall-limitations)
    * [Types of firewalls](#types-of-firewalls)
      * [Packet Filtering Firewall](#packet-filtering-firewall)
        * [Packet filtering rules](#packet-filtering-rules)
      * [iptables](#iptables)
      * [iptables concepts](#iptables-concepts)
      * [iptables Chains](#iptables-chains)
      * [iptables rules](#iptables-rules)
      * [Common iptables Syntax](#common-iptables-syntax)
      * [Issues with Packet Filtering Firewalls](#issues-with-packet-filtering-firewalls)
    * [Stateful Packet Inspection](#stateful-packet-inspection)
    * [Application proxy](#application-proxy)
    * [Circuit-level proxy](#circuit-level-proxy)
    * [Firewall Architecture](#firewall-architecture)
    * [General Firewall Issues](#general-firewall-issues)
  * [Authentication in Networks](#authentication-in-networks)
    * [Overview of authentication](#overview-of-authentication)
    * [Authentication in WPA2](#authentication-in-wpa2)
    * [Entity authentication in networks](#entity-authentication-in-networks)
    * [Types of authentication protocols](#types-of-authentication-protocols)
      * [Secret info-based authentication](#secret-info-based-authentication)
        * [AAA architecture protocols](#aaa-architecture-protocols)
        * [892.1X(EAPOL)](#8921xeapol)
        * [Extensible Authentication Protocol(EAP)](#extensible-authentication-protocoleap)
        * [RADIUS](#radius)
    * [Virtual Private Network (VPN)](#virtual-private-network-vpn)
    * [Tunneling](#tunneling)
    * [Network access server(NAS)](#network-access-servernas)
    * [Network Access Enforcement Methods](#network-access-enforcement-methods)
  * [Public Key Certificates](#public-key-certificates)
    * [Distribution of Public Keys](#distribution-of-public-keys)
      * [Public announcements](#public-announcements)
      * [Publicly Available Directory](#publicly-available-directory)
      * [Public-Key Authority](#public-key-authority)
      * [Public-Key Certificates](#public-key-certificates-1)
    * [X.509 Certificates](#x509-certificates)
      * [Multiple Certificate Authorities](#multiple-certificate-authorities)
    * [Public Key Infrastructure](#public-key-infrastructure)
    * [PGP - Web of Trust](#pgp---web-of-trust)

## Overview of Cybersecurity

### What is cybersecurity
  
* U-S.Department of Commerce:
  * The protection of information against unauthorized disclosure, transfer, modification, or destruction, whether accidental or intentional

* Wikipedia:
  * The protection of computer systems from the theft of or damage to their hardware, software, or electronic data, as well as from the disruption or misdirection of the services they provide

* U.S.NIST:
  * The protection afforded to an automated information system in order to attain the applicable objectives of preserving the integrity, availability and confidentiality of information system resources

### Key questions in cybersecurity
  
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
  * Physical
    * Locks
    * Security guards
    * Badge systems
    * Biometric systems
    * Mantrap doors
  * Administrative
    * Security policy
    * Separation of duties
    * Information classification
    * Personnel procedures
    * Testing
    * Security awareness training
  * Technical
    * ACLs
    * Encryption
    * Antivirus software
    * Smart cards
    * Dial-up-call-back systems

* Detective
  * Physical
    * Motion detectors
    * Closed-circuit TV's
  * Administrative
    * Monitoring and supervising
    * Job rotation
    * Investigations
  * Technical
    * Audit logs
    * IDs

* Corrective
  * Physical
    * None
  * Administrative
    * None
  * Technical
    * Server images

* Deterrent
  * Physical
    * Fences
    * Lighting
  * Administrative
    * None
  * Technical
    * None

* Recovery
  * Physical
    * Off site facility
  * Administrative
    * None
  * Technical
    * Data backup

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
* Identity(ID) :
  * Determine whether the user is authorized to gain access
  * Determines privileges of user(e.g normal or superuser)
  * User in access control to grant permissions to resources for user

##### Storing Passwords in Clear Text

* *ID,P*
* Insider attack: Normal user reads the database and learns other users passwords
  * Countermeasure: Access control on password database

* Insider attack: Admin user reads the database and learns other users passwords
  * Countermeasure: non-admin users must not be trusted.

* Outsider attack: Attacker gains unauthorized access to database and learns all passwords
  * Countermeasure: Do not store passwords as clear text 

##### Storing Passwords as Encrypted text

* *ID,E(K,P)*
* Encrypted passwords are stored
* When user submits password, it is encrypted and compared to the stored value
* Drawback: Secret key, K, must be stored somewhere. If an attacker can read the database, then they might also be able to access and read the key as well

##### Storing Passwords as Hashed Text

* *ID, H(P)*
* Hashed of passwords are stored
* When user submits password, it is hashed and compared to the stored value
* Practical properties of hash functions:
  * Variable sized input
    * Produce a fixed length, small output
  * No collisions
  * One way function
* If an attacker gains database access, practically impossible to take a hash value and directly determine the original password

##### Cracking passwords

* **Brute force attack**
  * Duration = size of password space / speed of hash

* **Dictionary attack**
  * Speeds up brute force attack
  * Uses common passwords from a dictionary of know passwords
  
* **Rainbow table attack**
  * Pre-calculated hashes by someone else
  * Possible passwords and corresponding hashes stored in database
  * Attacker performs lookup on database for target hash
  * Could be 100s and 1000s of terabytes big
  * Trade-off between time and memory cost
    * Reduce search time, but increase storage space
  * Countermeasures:
    * Longer passwords
    * Slower hash algorithms
    * Salting passwords before hashing

##### Salting Passwords

* *ID, Salt, H(P || Salt)*
* When ID and password initially created, generate random s-bit value (salt), concatenate with password and then hash
* When user submits password, the salt from the password database is concatenated, hashed and compared
* If attacker gains database access and they get to know the hash
  * Same effort to fine password as a brute force attack
* Rainbow tables are no longer feasible
  * Space required increased by a factor of $2^s$

##### Password Storage Best Practice

* When storing user login information, always store a hash of a salted password
* Password policies
* Salt: Random, generated when ID/password are first stored
  * 32 bits or longer
* Hash function: Slow, adaptive speed(work factor)
  * E.g bcrypt/scrypt, PBKDF2
* Design for failure: Assume password database will eventually be compromised

##### Passwords Vulnerabilities and Countermeasures

* Offline Dictionary Attack  
  * Attacker obtains access toID/password (hash) database 
    * Use dictionary to find passwords
  * Countermeasures:  
    * Control access to database
      * Reissue passwords if compromised
      * Strong hashes and salts

* Specific Account Attack
  * Attacker submits password guesses on specific account
  * Countermeasure:  
    * Lock account after too many failed attempts 

* Popular Password Attack  
  * Try popular password with many IDs
  * Countermeasures:
    * Control password selection
    * Block computers that make multiple attempts

* Password guessing against single user
  * Gain knowledge about user and user that to guess password
  * Countermeasure
    * Control password selection
      * Train users in password selection

* Computer hijacking
  * Attacker gains access to computer that user currently are logged in to
  * Countermeasure:
    * Auto-log out

* Exploiting user mistakes
  * User writes down password, shares with friends, and is tricked into revealing passwords, user pre-configured passwords
  * Countermeasures:
    * User training
      * Passwords + other authentication

* Salt Implementation
  * short salt length, hard coded salt value
  * Countermeasures
    * Personnel training

* Exploiting Multiple Password Use
  * Passwords re-used across different systems/accounts, make easier for attacker to access resources once one password discovered
  * Countermeasures
    * Control selection of passwords on multiple account/devices

* Electronic Monitoring
  * Attacker intercepts passwords sent across network
  * Countermeasures
    * encrypt communications that send passwords

##### Other Common Characteristics of Passwords

* Most use only alphanumeric characters
* Most are in (password) dictionaries
* Many users re-use passwords across systems
* Some very common passwords:  123456, password,12345678, qwerty, abc123, letmein, iloveyou, . . .
* When forced to change passwords, most users change a single character

##### Password Selection Strategies

* User education
  * Ensure users are aware of importance of hard-to-guess passwords
    * Advise users on strategies for selecting passwords

* Computer-generated passwords
  * Generate random or pronounceable passwords (but poorly accepted by users)
  
* Reactive password checking
  * Regularly check user’s passwords, inform them if weak passwords
  
* Proactive password checking
  * Advise user on strength when selecting a password

##### Passwords:  Do’s and Don't s

* Passwords Do’s
  * Choose Long and Complex Passwords
  * DO use passwords of at least eight characters or longer if set by a person
  * DO use passwords of at least six characters or longer if set by a system or service
  * DO allow support for at least a 64 character length
  * DO use a combination of all ascii character types
  * A Good Strategy:
    * Manipulate a personal, memorable sentence/poem with numbers and symbols
      * E.g.:“Tobeornottobe, itisaquestion!” byo→0,b→6,s→$
  
  * **Secure Practices**
    * DO create distinct passwords for different accounts
    * DO check strength of passwords:https://howsecureismypassword.net/
    * DO verify your password is not listed in known password dictionaries:  https://haveibeenpwned.com/Passwords

* Passwords DO NOT’s
  * Password Selection
    * DO NOT use dictionary words
    * DO NOT use pets, people, places, events, etc
    * DO NOT reuse passwords
    * DO NOT use adjacent keyboard strings:  qwerty1234
  * Password Usage
    * DO NOT write down your passwords, stick to your screen, hide under your keyboard
    * DO NOT reuse passwords
    * DO NOT change your password often
    * DO NOT completely share your strategy with others

#### Token-Bases Authentication

* Objects that a user possesses for purpose of user authentication are called tokens

##### Memory Cards

* Can store but do not process data
* Most common is magnetic stripe card
* Can include internal electronic memory
* Can be used alone for physical access
  * Hotel room, ATM ...
* Provides significantly greater security when combined with a password or PIN
* Drawbacks
  * Required a special reader
  * Loss of token
  * User dissatisfaction

##### Smart Cards

* Physical characteristics
  * Include an embedded microprocessor
  * A smart token that looks like a bank card
  * Can look like calculators, keys, small portable objects
* Interface
  * Manual interfaces include a keypad and display for interaction
  * Electronic interfaces communicate with a compatible reader/writer
* Authentication protocol
  * Static
  * Dynamic password generator
  * Challenge-response

#### Bio-metric Authentication

* Attempts to authenticate an individual based on unique physical characteristics
* Based on pattern recognition
* Technically complex and expensive when compared to passwords and tokens
* Physical characteristics used include
  * Facial characteristics
  * Fingerprints
  * Hand geometry
  * Retinal pattern
  * Iris
  * Signature
  * Voice

## Access Control

* The prevention of unauthorized use of a resource, including the prevention of use of a resource in an unauthorized manner

### Access Control and Other Security Functions

* Identification
  * A claim of an entity's identity
* Authentication
  * Verification that the credential of a user or other entity are valid
* Authorization
  * Granting of a right or permission to a system entity to access a resource
* Access control
  * Gran access right or permission at a more granular level
* Audit
  * Independent review of system records and activities in order to test for adequacy of system control
  * Ensure compliance to policy
  * Detect breaches and recommend new changes
  *(Security administrator) -> (Authorization database) -> (Access control function) -> (System resources) | (Access control function) <- (Authentication function) <- (User)

## Malicious Software

### Malware (Malicious software/code)
  
* Software or firmware intended to perform an unauthorized process that will have an adverse impact on the confidentiality, integrity, or availability of an information system
* A virus, worm, Trojan horse, or other code-based entity that infects a host. Spyware and some forms of adware are also examples of malicious code

#### Classification of malware
  
* Propagation
  * How the malware spreads
  * Virus
  * Worms

* Payload
  * Actions malware takes when reaching its victim
  * System corruption
  * Zombies and bots
  * Information theft
  * Stealthing

* Countermeasure
  * Anti-virus software

### Viruses

* A computer virus is computer program that:
  * Hides inside another program
  * Propagates itself to other programs and/or other computers
  * Often includes some destructive code

* Phases of a virus
  1. Dormant
     * Virus is is idle and waiting for some event to be activated
  2. Propagation
     * Virus copies itself into other programs or areas of operating system
  3. Triggering
     * Virus is activated to perform some function
     * Similar triggers to logic bombs, but also number
  4. Execution
     * Main function is performed(harmless/destructive)

#### Compression Virus

* This simple virus can be detected because file length is different from original program
* This detection can be avoided using compression
  * Assume program P1 is infected with virus CV1.
    1. For each uninfected file P2, the virus compresses P2 to produce P2’
    2. Virus CV is pre-pended to P2’ (so resulting size is same as P2)
    3. P1’ is uncompressed and (4) executed

#### Types of Viruses By target

* Boot Sector Infector
  * Infects a master boot record or boot record and spreads when a system is booted from the disk containing the virus

* File Infector
  * Infects files that the operating system or shell considers to be executable

* Macro Virus
  * Infects files with macro or scripting code that is interpreted by an application

* Multipartite Virus
  * Infects files in multiple way

#### Propagation of viruses

* Randomly select *.exe to insert itself to the target when it’s executed by other program
* Resides in memory and attaches itself to the target when an external drive is inserted to the computer
* Spread through infected software that appears to be useful and free software publicly available
* An email attachment
* A macro virus spreads when users share files

#### Types of Viruses by Concealment Strategy

* Encrypted Virus
  * A portion of the virus creates a random encryption key and encrypts the remainder of the virus

* Stealth Virus
  * A form of virus explicitly designed to hide itself from detection by anti-virus software

* Polymorphic Virus
  * A virus that mutates with every infection

* Metamorphic Virus
  * A virus that mutates and rewrites itself at each iteration and may change behavior as well as appearance

### Worms

* A computer worm is a computer program that
  * Can run independently
  * Can propagate a complete working version of itself onto other hosts in a network
  * May consume computer resources destructively

* Program that actively seeks out more machines to infect and each infected machine
* Serves as an automated launching pad for attacks on other machines
* Exploits software vulnerabilities in client or server programs
* Can use network connections to spread from system to systems
* Spreads through shared media (USB drives, CD, DVD or other data disks)
* E-mail worms spread in macro or script code included in attachments and instant messenger file transfers
* Upon activation the worm may replicate and propagate again
* Usually carries some form of payload

#### Worm Replication

* E-mail or instant messaging
  * Worm e-mails a copy of itself to other systems
    * Sends itself as an attachment via an instant message service

* File sharing
  * Creates a copy of itself or infects a file as a virus on a removable media

* Remote execution capability
  * Worm executes a copy of itself on another system

* Remote file access capability
  * Worm uses a remote file access or transfer service to copy itself from one system to the next

* Remote login capability
  * Worm logs onto a remote system as a user ant then uses commands to copy itself from one system to the other

* Propagation by social engineering
  * Tricking user to assist in the compromise of own systems
  * Spam email
  * Trojan Horses
    * Useful software that also performs harmful functions

### Trojan Horses

* A Trojan horse is a useful or seemingly useful program that contains hidden code of a malicious nature that executes when the program is invoked
* It does not propagate itself as viruses or worms
* It will be eliminated if the host program is deleted
* Can take advantage of security flaws
  * Anonymizer proxy (Google chrome, Internet Explorer)

### Types of Malware Damage

* Action taken by malware on system - Corrupt the system
* Data destruction
  * Delete
  * Overwrite data
    * Encrypt data and then demand payment to decrypt

* Real world damage
  * Corrupt BIOS code so the computers cannot boot
  * Control industrial systems to operate such that they fail

* Logic bomb
  * Activate when certain conditions are met
    * Presence/absence of files
    * Date/time
    * Particular software or user

#### Zombies and Bots

* Take over another internet attached computer and uses that computer to launch or manage attacks
* Botnet
  * Collection of bots capable of action in coordinated manner

##### Use of Botnets

* Distributed denial-of-service(DDOS) attacks
* Spamming
* Traffic sniffing
* Keylogging
* Spreading new malware
* Installing advertisement add-ons and browser plugins
* Attacking IRC chat networks
* Manipulating online polls/games

#### Information Theft

* Keyloggers
  * Captures keystrokes to allow attacker to monitor sensitive information
  * Typically uses some form of filtering mechanism that only return information close to keywords

* Spyware
  * Subverts the compromised machine to allow monitoring of a wide ranger of activity on the system
  * Monitoring history and content of browsing activity
  * Redirecting certain web page requests to fake sites
  * Dynamically modifying data exchanged between the browser and certain web sites of interest

#### Phishing

* Exploits social engineering to leverage the user's trust by masquerading as communication form a trusted source
* Include an URL in a spam e-mail that links to a fake web site that mimics the login page of a banking site, gaming site, or similar site
* Suggests that urgent actions is required by the user to authenticate their account
* Attacker exploits their account
* Spear-phishing
  * Recipient are carefully researched by the attacker
  * E-mail is crafted to specifically suit its recipient, often quoting a range of information to convince them of its authenticity

#### Other Malware

* Backdoor
* Trapdoor
* Mobile code
* Drive-by-downloads
* Flooders
* Rootkit

### Comparison of Malware

* Virus
  * Hides inside another program
  * Propagates itself into other programs and systems
  * Potentially causes destruction against assets in information systems

* Worm
  * An independent program
  * Propagates itself into other programs and systems
  * Potentially causes destruction against assets in information systems

* Trojan Horse
  * Hides inside another program
  * Potentially cause destruction against assets in the information systems

### Malware Countermeasure Approaches

* Prevention is the ideal solution, but almost always impossible
  * Elements of prevention
    * Policy
    * Awareness
    * Vulnerability mitigation
    * Apply access controls
    * User awareness and training
* Detection, identification and removal
* Requirements of countermeasures
  * Generality
  * Timeliness
  * Resiliency
  * Minimal denial-of-service costs
  * Transparency
  * Global and local coverage
* Multiple approaches to meet requirements
  * Host-based scanner
  * Perimeter scanning
  * Distributed intelligence gathering

#### Development of Anti-virus Software

* 1st generation - Simple scanners
  * Requires a malware signature to identify the malware
  * Limited to the detection of known malware

* 2nd generation - Heuristic scanners
  * Uses heuristic rules to search for probable malware instances
  * Another approach is integrity checking

* 3rd generation - Activity traps
  * Memory-resident programs that identify malware by its actions rather than its structure in an infected program

* 4th generation - Full-featured protection
  * Packages consisting of a variety of anti-virus techniques used in conjunction
  * Include scanning and activity trap components and access control capability

#### Generic Decryption

* A polymorphic  virus must decrypt itself to activate
* Generic decryption runs executable code in a virtual machine and monitors instructions
  * CPU emulator - Virtual machine software
  * Virus signature scanner - Scans for signatures
  * Emulation control module - Controls execution of target code

* If decryption is performed, the malware is exposed and detected
* Enables anti-virus program to easily detect complex polymorphic viruses and other malware while maintaining fast scanning speeds
* How long to run each interpretation?
  * Too long - Systems performance is degraded
  * Too short - Malware might not be spotted

#### Host-Based Behavior

* Integrates with OS and monitors program behavior in real-time
* Blocks potentially malicious actions before the affect the system
  * Attempts to open , view, delete and modify files
  * Attempt to format disks
  * Modifications to logic of executable files
  * Modification of critical system settings
  * Scripting of email or IM clients to send executable files
  * Initiation of network connection
* Does not depend on signatures of fingerprinting
* Allows malicious code to run, some actions may be undetected

### Malware Security Issues

* Cat and mouse
  * Many countermeasures rely on knowledge of existing malware, producers of malware try to defeat countermeasures

* Performance degradation and denial-of-service
  * Countermeasures often affect normal system behavior

* What can you actually trust?

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