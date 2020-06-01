# INF140-Question Banks

## Multiple-Choice Questions (Multiple Correct Alternatives)

### Cybersecurity Attacks and Controls

1. Which of the following are common features of a computer virus and a trojan horse?
        residing in a software
        replicating itself in the infected system and network
        exploiting system flaws and vulnerabilities in a system
        running itself when certain condition is triggered
        sending message to a remote controller

2. Which of the following belong to the social engineering attack?
        an attacker uses a telephone system to gain access to private personal and financial information from the public
        an attacker sends an e-mail that appears to come from a legitimate business requesting “verification” of information
        an attacker pretends to be another person with the goal of gaining access physically to a system or building
        an attacker sends highly customized emails to few end users to obtain their private information
        an attacker sends an advertisement to a large number of recipents
        an attacker inserts a virus-infected USB stick to a file system

3. Which of the following are security controls of user authentication?
        an employee uses his/her employee card to enter an office
        a person provides user name and password when login to a website
        a person enters the letters from the image of ``I am not a robot" in a login page
        a person opens his/her mobile phone with fingerprint
        a user in a system is promted “Permission Denied” when he/she opens a file in the system
    
4. Which of the following processes use an access control list?
        a student logins mittuib with his/her student credentials
        a student downloads some lecture slides at mittuib
        a student check his/her grade for a course at mittuib
        a student wants to see a student fellow’s grade at mittuib but is rejected
        a lecture uploads lecture notes for his/her course at mittuib

5. Which of the following access control methods used in a compute system?
        manpower-based access control
        attribute-based access control
        role-based access control
        rule-based access control
        discretionary access control
    
6. Which of the following security controls heavily depend on cryptographic primitives?
        accountability
        authorization
        authentication
        availability
        integrity
    
7. Which of the following security controls are elements of access control?
        accountability
        authorization
        authentication
        availability

8. Which of the following are in the category of preventative security control?
        user authentication
        data encryption
        data backup
        firewall
        intrusion detection system
        anti-malware software
        least-privilege access control

9. Which of the following firewalls act as both client and server in controlling network traffic?
        packet filtering firewalls
        stateful packet inspection firewalls
        application-proxy firewalls
        circuit-proxy firewalls
    
10. Which of the following commands use the ICMP protocol?
        traceroute www.uib.no
        ping www.uib.no
        hping3 -S –flood -p 80 www.uib.no
        netstat www.uib.no
    
11. Which of the following attacks can be enabled by ARP spoofing?
        SYN Flooding
        DNS poisoning
        packet sniffing
        Denial of Service

12. Suppose a user’s password is hashed with SHA256 and the hash is then stored in a system. In practice, which of the following will significantly reduce the quality of the hash and may lead to a successful password cracking?
        the user’s password consists of only 20 lower-case letters
        upper-case letters in the user’s password are converted to lower-case letters before the password is hashed
        SHA256 is replaced with a fast hash function with 64-bit digest
        a dynamically varing salt is added the the calculation of the password hash
        the user’s password is a combination of lower-case letters, upper case letters, digits, punctuations and its length is 6

13. In a Linux system, suppose a user’s password is stored in /etc/shadow as:
    Password:$6$lM97wGbU5S.Funda$8HxX3gD5UjdwnXD7mHu7Foh9s6w.NCn5cxifoki7pr0m01Re5VG/yad86LjKmpJuXB/66ks1Y7T5y6cjV6.351:18313:0:99999:7::: Which of the following statements about the above password file are not correct?
        there is no login name in the file
        ‘Password’ is the user name
        ‘$6$’ indicates the number of bytes in the salt
        ‘$6$’ indicates the hash type used in the calculation
        ‘18313’ indicates the number of hash iterations in the file
    
14. Which of the following are security requirements of a cryptogrpahic Hash function?
        it has variable input length
        it has fixed output length
        it should be pre-image resistant
        it should be collision resistant
        it should have distinct outputs for any two different input
        it should be distingushible from randomly generated string

15. Which of the following can be used for protecting data integrity?
        user authentication
        symmetric encryption
        digital signature
        message authentication code
        hash function

16. Which of the following are entity authentications in network access control?
        firewalls
        WPA2 with IEEE 802.X
        IEEE 802.11
        RADIUS
        Password-based Authentication Protocol
        Virtual Private Network

17. Which of the following characteristics are provided by the series of Wi-Fi Protected Access?
        IEEE 802.1X, WEP, MAC
        IEEE 802.1X, EAP, TKIP
        IEEE 802.1X, EAP, WEP
        IEEE 802.1X, EAP, CCMP

18. Which of the following characteristics are provided by RADIUS?
        accountability
        authorization
        availability
        authentication
        anti-malware
    
19. Which of the following statements about HTTPS are correct?
        it provides data confidentiality and integrity in communcations
        it enables the web client to authenticate the web server by its X.509 public-key certificate
        it enables the web client to authenticate the web server by its PGP public-key certificate
        it helps the server prevent DDoS attack
        it enables the client to remotely login to the server in a secure manner

20. Which of the following statements about public-key certificate are correct?
        it is used to authenticate an entity in a network
        it is widely used because public-key ciphers are more secure than symmetric ciphers
        it is widely used because it makes key distribution more easily in the Internet
        it is used to prevent man-in-the-middle attack in a network

