# INF140-Question Banks

1. Which of the following are common features of a computer virus and a trojan horse?

        A.      residing in a software
        B.      replicating itself in the infected system and network
        C.      exploiting system flaws and vulnerabilities in a system 
        D.      running itself when certain condition is triggered
        E.      sending message to a remote controller

        Answer: A, D, E

2. Which of the following belong to the social engineering attack?

        A.      an attacker uses a telephone system to gain access to private personal and financial information from the public
        B.      an attacker sends an e-mail that appears to come from a legitimate business requesting “verification” of information
        C.      an attacker pretends to be another person with the goal of gaining access physically to a system or building
        D.      an attacker sends highly customized emails to few end users to obtain their private information
        E.      an attacker sends an advertisement to a large number of recipients
        F.      an attacker inserts a virus-infected USB stick to a file system

        Answer: B, C, D

3. Which of the following are security controls of user authentication?

        A.      an employee uses his/her employee card to enter an office
        B.      a person provides user name and password when login to a website
        C.      a person enters the letters from the image of ``I am not a robot" in a login page
        D.      a person opens his/her mobile phone with fingerprint
        E.      a user in a system is promted “Permission Denied” when he/she opens a file in the system

        Answer: A, B, D, E 

4. Which of the following processes use an access control list?

        A.      a student logs in to mittuib with his/her student credentials
        B.      a student downloads some lecture slides at mittuib
        C.      a student check his/her grade for a course at mittuib
        D.      a student wants to see a student fellow’s grade at mittuib but is rejected
        E.      a lecture uploads lecture notes for his/her course at mittuib

        Answer: A, B, C, D, E

5. Which of the following access control methods used in a compute system?

        A.      manpower-based access control
        B.      attribute-based access control
        C.      role-based access control
        D.      rule-based access control
        E.      discretionary access control

            Answer: B,C,E

6. Which of the following security controls heavily depend on cryptographic primitives?

        A.      accountability
        B.      authorization
        C.      authentication
        D.      availability
        E.      integrity

        Answer: C, E

7. Which of the following security controls are elements of access control?

        A.      accountability
        B.      authorization
        C.      authentication
        D.      availability

        Answer: A, B, C

8. Which of the following are in the category of preventative security control?

        A.      user authentication
        B.      data encryption
        C.      data backup
        D.      firewall
        E.      intrusion detection system
        F.      anti-malware software
        G.      least-privilege access control

        Answer: A, B, D, F, G

9. Which of the following firewalls act as both client and server in controlling network traffic?

        A.      packet filtering firewalls
        B.      stateful packet inspection firewalls
        C.      application-proxy firewalls
        D.      circuit-proxy firewalls

        Answer: C, D 

10. Which of the following commands use the ICMP protocol?

        A.      traceroute www.uib.no
        B.      ping www.uib.no
        C.      hping3 -S –flood -p 80 www.uib.no
        D.      netstat www.uib.no

        Answer: A, B, C

11. Which of the following attacks can be enabled by ARP spoofing?

        A.      SYN Flooding
        B.      DNS poisoning
        C.      packet sniffing
        D.      Denial of Service

        Answer:  C, D

12. Suppose a user’s password is hashed with SHA256 and the hash is then stored in a system. In practice, which of the following will significantly reduce the quality of the hash and may lead to a successful password cracking?

        A.      the user’s password consists of only 20 lower-case letters
        B.      upper-case letters in the user’s password are converted to lower-case letters before the password is hashed
        C.      SHA256 is replaced with a fast hash function with 64-bit digest
        D.      a dynamically varing salt is added the the calculation of the password hash
        E.      the user’s password is a combination of lower-case letters, upper case letters, digits, punctuations and its length is 6

        Answer: B, C, E

13. In a Linux system, suppose a user’s password is stored in /etc/shadow as:
    Password:
         $6$lM97wGbU5S.Funda$8HxX3gD5UjdwnXD7mHu7Foh9s6w.NCn5cxifoki7pr0m01Re5VG/yad86LjKmpJuXB/66ks1Y7T5y6cjV6.351:18313:0:99999:7:::
        Which of the following statements about the above password file are not correct?

        A.      there is no login name in the file
        B.      ‘Password’ is the user name
        C.      ‘$6$’ indicates the number of bytes in the salt
        D.      ‘$6$’ indicates the hash type used in the calculation
        E.      ‘18313’ indicates the number of hash iterations in the file

        Answer: A, C, B(apparantly?)

14. Which of the following are security requirements of a cryptographic Hash function?

        A.      it has variable input length
        B.      it has fixed output length
        C.      it should be pre-image resistant
        D.      it should be collision resistant
        E.      it should have distinct outputs for any two different input
        F.      it should be distingushible from randomly generated string

        Answer: A, B, C, D, 

15. Which of the following can be used for protecting data integrity?

        A.      user authentication
        B.      symmetric encryption
        C.      digital signature
        D.      message authentication code
        E.      hash function

        Answer: C, D

16. Which of the following are entity authentications in network access control?

        A.      firewalls
        B.      WPA2 with IEEE 802.X
        C.      IEEE 802.11
        D.      RADIUS
        E.      Password-based Authentication Protocol
        F.      Virtual Private Network

        Answers: B, D, E

17. Which of the following characteristics are provided by the series of WiFi Protected Access?

        A.      IEEE 802.1X, WEP, MAC
        B.      IEEE 802.1X, EAP, TKIP
        C.      IEEE 802.1X, EAP, WEP
        D.      IEEE 802.1X, EAP, CCMP
        
        Answer: B, D

18. Which of the following characteristics are provided by RADIUS?
        accountability
        authorization
        availability
        authentication
        anti-malware

19. Which of the following statements about HTTPS are correct?

        A.      it provides data confidentiality and integrity in communcations
        B.      it enables the web client to authenticate the web server by its X.509 public-key certificate
        C.      it enables the web client to authenticate the web server by its PGP public-key certificate
        D.      it helps the server prevent DDoS attack
        E.      it enables the client to remotely login to the server in a secure manner

        Answer: A, B, E

20. Which of the following statements about public-key certificate are correct?

        A.      it is used to authenticate an entity in a network
        B.      it is widely used because public-key ciphers are more secure than symmetric ciphers
        C.      it is widely used because it makes key distribution more easily in the Internet
        D.      it is used to prevent man-in-the-middle attack in a network

        Answer: A, C, D