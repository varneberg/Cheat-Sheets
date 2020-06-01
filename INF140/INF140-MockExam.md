# INF140 MockExam

## Part 1

1. Unexpectedly, you get an email from a colleague who requests you to urgently click on an email link which they have sent you.What is the safest option?

        A.  The link is from a known person therefore it’s safe to open.
        B.  If  the  link  was  malicious  the  organisation’s  firewall  would  haveflagged or blocked it, therefore it’s safe to open.
        C.  Reply to the sender to double-check if the link is safe to open asthey might have sent it accidentally.
        D.  Do not click the link. Phone the sender for verification

        Answer: D

2. Who are the targets of modern day hackers?

        A. Banks and finance companies who process a lot of payments.
        B. Any organisation or individual is liable to be the victim of hackers.
        C. Companies which hold a lot of proprietary information.
        D. Companies which hold credit card numbers of customers.

        Answer: B

3. According to the CIA Triad, which of the below-mentioned element is not considered in the triad?

        A.  Confidentiality
        B.  Integrity
        C.  Authenticity
        D.  Availability

        Answer: C 

4. Why are the elements confidentiality, integrity, authentication, authorization and availability are considered fundamental?

        A.  They help understanding hacking better
        B.  They help understanding threats better
        C.  They help understands security and its components better
        D.  They help to understand the cyber-crime better

        Answer: C

5. The integrity of data is not related to which of the following?

        A.  Unauthorized manipulation or changes to data
        B.  The modification of data without authorization
        C.  The intentional or accidental substitution of data
        D.  The extraction of data to share with unauthorized entities

        Asnwer: D

6. Existence of weakness in a system or network is called

        A.  Threat
        B.  Vulnerability
        C.  Exploit
        D.  Attack

        Answer: B

7. Suicide Hackers are those

        A.  who  break  a  system  for  some  specific  purpose  with  or  without keeping in mind that they may suffer long term imprisonment due to their malicious activity
        B.  individuals  with  no  knowledge  of  codes  but  an  expert  in  using hacking tools
        C.  who know the consequences of their hacking activities and hence try to prevent them by erasing their digital footprints
        D.  who are employed in an organization to do malicious activities on
        other firms

        Answer: A

8. The full form of Malware is

        A.  Malfunctioned Software
        B.  Multipurpose Software
        C.  Malicious Software
        D.  None of above

        Answer: C

9. Trojans normally do not do one of the following. What is that?

        A.  Deleting Data
        B.  Protecting Data
        C.  Modifying Data
        D.  Copying Data
        
        Answer: B 

10. A ____ is  a  method  in  which  a  computer  security  mechanism  is bypassed untraceable for accessing the computer or its information.

        A.  front-door
        B.  backdoor
        C.  clickjacking
        D.  key-logging

        Answer: B

11. Backdoors cannot be designed as(stupid question tho)

        A.  the hidden part of a program
        B.  as a part of Trojans
        C.  embedded code of the firmware(hardware backdoor)
        D.  embedded with anti-malware

        Answer: D

12. The intent  of a ____ is  to  overkill  the  targeted  server’s  band-width and other resources of the target website.

        A.  Phishing attack
        B.  DoS attack
        C.  Website attack
        D.  MiTM attack
        
        Answer: B

13. A DoS attack coming from a large number of IP addresses, making it hard to manually filter or crash the traffic from such sources is known as a

        A.  GoS attack
        B.  PDoS attack
        C.  DoS attack
        D.  DDoS attack

        Answer: D 

14. Which of the following is a type of transport layer DoS?

        A.  HTTP flooding
        B.  Ping flooding
        C.  TCP flooding
        D.  DNS query flooding

        Answer: C

15. ___is a naming system given to different computers which adapt to human-readable domain names.

        A.  HTTP
        B.  DNS
        C.  WWW
        D.  ISP

        Answer: B

16. ______ is a means of storing & transmitting information in a specific format so that only those for whom it is planned can understand or process it.

        A.  Malware Analysis
        B.  Cryptography
        C.  Reverse engineering
        D.  Exploit writing
        
        Answer: B

17. _________ are difficult to identify as they keep on changing their type and signature.

        A.  Non-resident virus
        B.  Boot Sector Virus
        C.  Polymorphic Virus
        D.  Multipartite Virus

        Answer: C

18. A _____ is a small malicious program that runs hidden in a legitimate like software.

        A.  Virus
        B.  Trojan
        C.  Shareware
        D.  Adware

        Answer: B

19. _____ is  not  an  attack  technique  where  numerous  TCP  segments are spoofed with a bogus source address which is then sent to a server.

        A.  SYN flooding attack
        B.  ACK flooding attack
        C.  Fin flooding attack
        D.  Ping flooding attack

        Answer: D

20. Which of the protocol is not used at the network layer of the TCP/IP model?

        A.  ICMP
        B.  IP
        C.  IGMP
        D.  HTTP

        Answer: D

## Part 2

1. Which of the following characteristics are provided by RADIUS(Remote authentication dial-in user service)?

        A. Accountability
        B. Authorization
        C. Availability
        D. Authentication
        E. Aggregation
        F. Anti-malware
        
        Answer: A, B, D

2. Which statements about public-key certificates are correct?

        A. It is used to authenticate an entity in a network
        B. It is widely used because public-key ciphers are more secure than symmetric ciphers
        C. it is widely used because it makes key distribution more easily in the Internet
        D. It is used to prevent man-in-the-middle attacks in a network

        Answer: A, D (?)

3. Which of the following firewalls act both client and server roles in controlling network traffic?

        A. Packet filtering network
        B. Stateful packet inspection firewalls
        C. Application-proxy firewalls
        D. Circuit-proxy firewalls

        Answer: C, D

4. Suppose a user’s password is hashed with SHA256 and the hash is then stored in a system.  In practice, which of the following will significantly reduce the quality of the hash and may lead to a successful password cracking?

        A.  the user’s password consists of only 20 lower-case letters
        B.  upper-case letters in the user’s password are converted to lower-case letters before the password is hashed
        C.  SHA256 is replaced with a fast hash function with 64-bit digest
        D.  The user’s password has length < 8
        E.  A dynamically varying salt is added the the calculation of the password hash
        F.  The user’s password is a combination of lower-case letters, uppercase letters, digits, punctuations and its length is 6

        Answer: B, C, D(Stemmer nok ikke, men bra praksis å ha allikevel), F

5. Which of the following are types of preventative security control?

        A. User authentication
        B. Data encryption
        C. Data backup
        D. Firewall
        E. Intrusion detection system
        F. Anti-malware system
        G. Least-privilege access control

        Answer: A, B, D, F, G

6. Which of the following are common features of a computer virus and a Trojan horse?

        A. Residing in a software
        B. Replicating itself in the infected system and network
        C. Exploiting system flaws and vulnerabilities in a system
        D. Running itself when certain condition is triggered
        E. Sending message to a remote controller
        
        Answer: A, D, E

7. Which of the following are security controls of user authentication?

        A. A person uses a room card to open a hotel room
        B. A person provides user name and password when login to a website
        C. A person enters the letters from the image of “I am not a robot”in a login page
        D. A person opens his/her mobile phone with fingerprint
        E. A user in a system is promted “Permission Denied” when he/she opens a file in the system

        Answer: A, B, D, E(Could be access control)

8. Which of the following belong to the social engineering attack?

        A. An attacker uses a telephone system to gain access to private personal and financial information from the public
        B. An attacker sends an e-mail that appears to come from a legitimate business requesting “verification” of information
        C. An attacker pretends to be another person with the goal of gaining access physically to a system or building 8 of 12
        D. An  attacker  sends  highly  customized  emails  to  few  end  users  to obtain their private information
        E. An attacker sends an advertisement to a large number of recipient
        F.  An attacker inserts a virus-infected USB stick to a file system

        Answer: B, C, D

9. Which of the following processes use an access control list?

        A.  a student logs in to mittuib with his/her student credentials
        B.  a student downloads some lecture slides at mittuib
        C.  a student check his/her grade for a course at mittuib
        D.  a student wants to see a student fellow’s grade at mittuib but is rejected
        E.  a lecture uploads lecture notes for his/her course at mittuib

        Answer: A, B, C, D, E

10. Which of the following security controls are based on cryptographic primitives?

        A. Accountability
        B. Authorization
        C. Authentication
        D. Availability

        Answer: C

## Part 3

### Question 1

* In a computer system, access is the flow of information between two entities.
* A/An [ **subject** ] is an active entity that requests access to a/an [ **asset**  ].
* A/An [ **object** ] is a passive entity that contains information or needed functionality.
* Access control is a broad term that covers several different types of mechanisms that enforce access control features on computer systems, networks,and information.
* When a user wants to access a system, progressively,there will be four security controls in the system: [ **cryptography** ], [ **security protocols** ], [ **firewall** ] and [ **access control** ].
* An access control mechanism dictates how subjects access objects.
* There are different access models.
* A system that uses [ **discretionary access control** ] enables the owner of the resource to specify which subjects can access specific resources.
* In, [ **mandatory Access Control** ] users do not have the discretion of determining who can access objects.
* Instead, this model greatly reduces the amount of rights, permissions, and functionality a user has for security purposes.

### Question 2

* The  Transmission  Control  Protocol/Internet  Protocol  (TCP/IP)  is  a suite of protocols that governs the way data travels from one device to another.
* Different from the Open Systems Interconnection (OSI) model, the TCP/IP model has five layers, which from bottom to top are[ **hardware** ], [ **Network interface** ], [ **internet** ], [ **(Host-to-Host) transport** ] and [ **application** ].
* Cryptography  plays  a  critical  role  in  secure  communications.    * In theTLS/SSL protocol suit, both RSA and Diffie-Hellman are used for key ex-change between the client and the server.
* Suppose the client and the server choose Diffie-Hellman for key  exchange.
* The  public  parameter  is  set  asp = 1013 with generator 2.
* Assume the client generates a private key Kc= 13 and the server generates a private keyKs = 11.
* Then the client’s public key is [ **2^(mod 1013)** ] and the server’s public key is [ **2^(mod 1013)** ].
* After they exchange these public keys, they share a secret information:[ **$2^{13+11} \mod 1013 = 2^{24} \mod 1013$** ]
* If the shared secret information, with ASCII encoding, is taken as the input for MD5 to generate a 128-bit encryption key for AES, then the encryption key in hexadecimal form is [ **63 34 30 31 35 62 37 66 33 36 38 65 36 62 34 38 37 31 38 30 39 66 34 39 64 65 62 65 30 35 37 39** ]

## Part 4

<img src="/INF140/INF140-summary-pictures/mock-4-1.png" width="50%">

### Part 4 - Question 1: Packet filtering rules

* Default policy as ACCEPT
* Firewall on node 3, i.e the router connecting the two subnets
* 1 and 2 are inside, while 4 and 5 are outside 

#### 4.1.a - Rule1: Block ping(icmp) between subnets

* ```iptables -A FORWARD -p icmp -i eth1:1.1 -d eth2:2.1 0.0.0.0/24 -j DROP```
* ```iptables -A FORWARD -p icmp -i eth2:2.1 -d 0.0.0.0/24 eth1:1.1 -j DROP```

#### 4-1.b - Rule 2: Block icmp packets coming into firewall

* ```iptables -A INPUT -p icmp -j DROP```

#### 4-1.c - Rule 3: Block ping packets coming out of firewall

* ```iptables -A OUTPUT -p icmp -j DROP```

#### 4-1.d - Rule 4: Prevent node 1 from SSHing to outside nodes

* ```iptables -A FORWARD -i eth1:11 -p tcp -dport 22 -d eth2:2.1 0.0.0.0/24```

#### 4-1.e - Rule 5: Inside hosts can access outside websites

* Change default policy as DROP and write packet filtering rules for the following goals
* ```iptables -F```
* ``` iptables -P INPUT DROP```
* ```iptables -A INPUT -p tcp -dport 80 -j ACCEPT```