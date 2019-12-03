# INF226 QUIZ ANSWERS

1. What is the definition of software security?
   * When a program functions according to the intentions in an adverserial enviroment

2. What does software security logic consist of? And what are some examples of these?
   * Requirements
     * Capture the intentions of the software
     * Spelling out our intentions
     * Examples:
       * Availability of the service  
       * Capacity
       * Integrity of data
       * Authentication of data
       * Recoverability
   * Assumptions
     * Spelling out our knowlegde of the software until it runs
     * Examples:
       * Assumptions pointing towards problems:
         * User input cannot be trusted to have a property X
         * IP adresses can be spoofed
         * Computers has finite resources
         * Programmers write bugs
       * Assumptions pointing towards solutions:
         * Checking the input so we know it has a desired property
         * An attacker cant guess a random 128 bit number
         * Semantics of a program
         * Correct type checker
         * Robust internet routing
   * Mechanisms
     * Satisfying the requirements given the assumptions
     * Examples:
       * Choice of programming language
       * Rate limiting
       * Sanity checks on user inputs
       * Access control lists
       * Optimisation of algorithms
       * Encryption
  
3. What is a vulnerability?
   * A circumstance where the program fails to behave as intended. When the program fails to be secure.

4. What are the vulnerability disclosure and what stances are there?
   * Information given to the public about a security related problem
   * No disclosure
     * No details are given to the public
   * Coordinated disclosure
     * Some details are given to the public once fixes has been made to the software
   * Full disclosure
     * All details are given public

5. What is an exploit?
   * A procedure taking advantage of a vulnerability, demonstrating the vulnerability of the program

6. What is an RCE vulnerability?
   * Remote Code Execution. When an attacker gets permission to run code on a victims machine
  
7. How does the call stack work?
    * The stack stores return addresses for function call
    * On call the pointer is pushed on the stack
    * When function closes, the pointer is popped from the stack

8. How does an attacker use an shell-code exploit?
   * By filling the buffer with hes own code and overwriting the return pointer to point to hes own code. This can spawn a shell, giving the attacker RCE access to the machine
  
9. For what reasong could an attacker use NO-OP sled?
    * When the attacker does not know the adress of the buffer.

10. What is ROP?
    * Return oriented programming. When the attacker uses prexisting code in the program instad of uploading a shell

11. How can a programmer prevent a buffer overflow attack?
    * Write better C code(self explaining)
    * Static analysis
    * Stack canaries
      * Secret value placed on the stack every time the program is run
      * Checks if the number from pointer has been modified on function returning
      * Terminates if modification is detected
    * W^X
      * OS enforcing writeable memory cannot be executed
      * Prevents loading shell in writeable buffers
    * Address space layout randomisation
      * Randomising the layout when allocating memory in the system
      * Makes the attacker guess the locations of functions and libraries

12. What are some of the best practises to avoid buffer overflow?
    * Use memory safe languages
    * Memory safe abstractions in unsafe languages(e.g vectors and smart pointers in C++)
    * Use the compiler to find vulnerabilities
    * Run static analysis to identify bugs
  
13. What is memory safety?
    * Each part of the program is only given access to the memory locations they are permitted

14. What should and shouldn't a function access in a program?
    * A function should access:
      1. Arguments from the caller
      2. Global variables
      3. Local variables
    * A functions should not access variables from another function

15. How does one break memory-safety?
    * Using:
      * Pointer arithmetics 
      * Unconstrained casting
      * No bounds-check on array access
      * Unsafe pointer de-allocation

16. Name some memory safe and not memory safe languages
    * Safe:
      * Java, C#, most scripting languages
    * Unsafe:
      * Assembly
      * C
      * C++

17. How does theses languages achieve memory safety?
    * Garbage collection (Lisp, JAVA, Haskell,..)
    * Resource allocation in RAII and borrows checker (Rust)
  
18. What is undefines behaviour?
    * When code does not behave according to language standard

19. What are some problems with sql?
    * Confusing between data and queries
    * Strings are used to represent data and queries

20. How do you prevent SQLi attacks?
    * Prepared statments

21. What is STRIDE?
    * Used for developing threat models
    * Spoofing
    * Tampering
    * Repudiation
    * Information disclosure
    * Denial of service
    * Elevation of privilegde

22. What is DREAD?
    * Used for ranking threats
      * Damage potential
      * Reproducibility
      * Exploitation
      * Affected users
      * Discoverability

23. What is functional decomposistion?
    * An overview of the components in a system
    * A detailed map over comunication between components
    * Description of the function of each of the components

24. What is a threat model?
    * Applicates our assumptions about a system
    * What threats apllies to the system?
    * Trust between components?
    * Which threats apply where?

25. What is a trust boundary?
    * When data is comunicated between components, it crosses a trust boundry

26. How do you analize defence in depth?
    * Find out what components are affected
    * Are there any linchpins?
    * Detect failures
    * Migitate failures

27. What is trusting trust?
    * Trusting someone else on something because they claim it is to be trusted
    * At one point we have to start trusting the people making the software

28. Why is it important to trust a compiler and what can you do trust a compiler?
    * A compiler could recognize code and compile backdoors without the user knowing
    * To trust a compiler:
      * Read the source code
      * Trust the compiler who compiled the compiler

29. How do you test a compiler?
    * Get an independent compiler to compare with the test compiler
    * Compile the source code using both compilers and copile the executeables
    * Compare the results
    * The binaries for each of the executeables will be different, but if they are functionally equivavalent, one can trust the compiler

30. What is the OWASP top 10 project?
    * A list of the top 10 most common vulnerabilities present on the internet
        1. Injection
        2. Broken Authentication and Session Management
        3. Cross-Site Scripting
        4. Insecure Direct Object References
        5. Security Misconfiguration
        6. Sensitive Data Exposure
        7. Missing Function Level Access Control
        8. Cross-Site Request Forgery
        9. Using Components With Known Vulnerabilities
        10. Unvalidated Redirects And Forwards

31. What is CVE?
    * Common Vulnerability Exposures
    * A CVE is an entry stored in the CVE database consiting of a:
      * unique number
      * description
      * at least one public reference

32. What is CNA's?
    * CVE numbering authorities
    * Assigns numbers to CVE's

33. What is CVSS?
    * Common Vulnerability Scoring System
    * Scores CVS from 1 - 10

34. What are the metrics in CVSS?
    1. Base metrics
       * Access vectors
         * Local, network or adjacent network
    2. Impact metrics
       * Rates impact on a scale from None/Partial/Complete based on:
         * Confidentiality
         * Integrity
         * Availability
    3. Temporal metrics
        * Metrics who changes overtime
        * Rated from:
          * Exploitability(Unproven, Proof-of-concept, Functional, High)
  
35. What is CWE?
    * Common Weakness Enumeration
    * List of common weaknesses present in software 
    * More fine grained than OWASP's Top 10, but similar
    * Structure:
      * Architecture components
      * Development concepts
      * Research concepts

36. What is NVD?
    * National Vulnerability Database
    * Contains analysis of known vulnerabilities 
      * CVE number
      * CWE numbers
      * CVSS
      * Versions affected

37. What is a static analysis and how do you perform it?
    * Inspection of source code
      * Program flow analysis
      * Constraints analysis
      * Logic tests
      * Linting
  
38. What is a dynamic analysis and how do you perform it?
    * Inspection of running software
      * Fuzzers
      * Crawlers
      * Man-in-the-middle proxy

39. What is access control and what are the aspects of it?
    * The decisions of what users are allowed to do within a system
      * Physical
      * Logical
      * Cryptographic
      * Soscial

40. What is MAC?
    * Mandatory Access Contorl
    * Access control policies decided by a central authority
    * For example OS's have MAC access over resources(CPU, memory, storage,...)

41. What is DAC?
    * Discretionary Access Control
    * Users specifies permissions for their own objects

42. What is a capability?
    * A method of only giving capabilities needed for each object

43. What are the access control models and how do they work?
    1. Access Control Lists
         * Permissions given to each object, giving different users different permissions for it
         * Each object has its own set of permissions for each user
         * Structured according to users and groups
    2. Rôle based access control
         * A set of roles abstract the permissions from the users
         * Actions are always performed by a rôle
         * Users must reauthenticate to change rôles
    3. Capability based access control
         * Users has their own capabilities  
         * A capability is a reference to an object and a set of permissions for that object
         * A capability is used whenever the resrouce is accessed

44. What is the rôle of the OS?
    * Orchestrate software
    * Communicate with programs through system calls
    * Different protections for different resources(memory, CPU, file systems, files/sockets/network connections)

45. What is the confused deputy problem?
    * A priviliedged process(deputy) is tricked by a prcoess with lower permissions, to do actions on behalf of it
    * For example comilers and browser acting as a deputy

46. What defines users and groups?
    * Each user has a UID
    * Each user is in a group that has a GID
    * Prevents users to access each others memory
    * Each file has a owner UID and a group GID

47. What are file descriptors?
    * The capabilities of accessing a file
    * Each process has its own file-descriptor table
    * OS checks permissions when opening files and creating descriptor

48. What is, and why do we use Virtual Memory Mapping?
    * Virtualize physical memory into pages and devide among processe
    * Its inconvenient to let programs use physical memory
    * Virtual memory is not decided at compile time, making guessing memory locations harder
    * Memory fragmentations gets hidden from the program

49. How does the UNIX file system devide directories?
    * Into logical parts

50. What is chroot?
    * Changing of root directory
    * Provides system virtualization

51. What is the OpenBSD pledge?
    * Mechanisms for restricting what system calls are allowed for each process

52. What is OS virtualization?
    * Abstracting away OS system calls, hardware or both to not be run directly on the OS's hardware

53. What is Linux kernel namespaces?
    * Grouping of processes so each groupt has individual:
      * Filesystem mount tables
      * Process stables
      * Network stack
      * UID tables

54. What is Docker and what mechanisms does it provide?
    * Containers
      * Runs programs separated from the OS using OS mechanisms
      * Templated by images
      * Construced and administrated through container daemon
    * Separation mechanisms
      * chroot
      * Individual namespaces to containers
      * CGroups to limit resources to containers
    * Capabilities
      * For each container
      * Abstraction through OS level restrictions
      * Only whitelisted capabilities allowed
    * Security configuration
      * Underlying OS level separation mechanisms
      * Dockered daemon attack surface
      * Security of container configuration

55. What is the principle of least priviledge?
    * No user or program should operate using the least amount of priviledge necessary to complete the job

56. How does SSH practice priviledge separation?
    * With monitors and slaves:
      * **Monitors**
        * Priviledged
        * Provides interface for slaves to perform priviledged actions
        * Validated requests
        * Performs actions on slaves behalf
      * **Slaves**
        * Unpriviledged
        * Does most of the work
        * Calls monitor when priviledged operations must be performed

57. How does one implement a Monitor/Slave pattern?
    1. Identifying priviledged operations
         * eg file access, accessing crypto keys, databases,...
    2. Separate request types
         * Information
         * Capabilites
         * Change of identity
    3. Devide into phases
         * Pre authentication
         * Post authetication
    4. Define Slave/Monitor connection
         * On connection, the service spawns a new connection between slave/monitor pair
    5. Define Slave/Master communication
         * Communicate through IPC mechanisms
           * Pipe
           * Shared memory
           * Socket-pair
    6. Mechanisms for changing of identity
    7. Retain slave state

58. What priviledged does SSHD have?
    * Diffie-Hellman
    * User validation
    * Password authentication
    * Public key authentication
    * Transferrable shared memory
    * **Priviledged operations in SSHD**:
      * Renewing crypto keys
      * Pseudo terminal creation (PTY)

59. Why doesn't increasing the password alphabet, increase security?
    * The length only grows constant with the size of the alphabet

60. What is NIST?
    * Standard for password creation
    * Allows atleast 64 characters
    * Compares passwords with lists of known password

61. What are the uses of a hash function?
    * Checksumming data
    * Data identifier
    * Hashing passwords
    * Signature verification/generation
    * Building crypto primitives

62. What is the ideal hash function?
    * Small input = large output
    * Collision free
    * One way
    * Quick to compute

63. What is a rainbow table?
    * Tool to derive password by looking at hash
    * Time-space tradeoff when creating look-up table for hash values to plaintext
    * Precomputed table for reversing crypographic functions
    * Used for cracking passwords

64. What is hashing salt?
    * A randomly generated string stored in the password hash making it harder to crack

65. What is a key derivation function?
    * Functions to derive plaintext passwords from hashes

66. What is naïve key derivation?
    * Generated byte strings placed before and after hash
    * Making the attacker guess the second string
    * Second strings works as cost parameter
  
67. What is SCrypt?
    * A maximum memory hard key derivation function

68. What is authetication?
    * The act of verifying the identity of actors in the system
  
69. What is 2FA authentication?
    * Additional authentication measures to passwords

70. What "is trust upon first use"?
    * Trust user first time they log in because it is unlikely there is a man-in-the-middle on inital authentication
    * Use this authetication for the next sessions

71. What is a CA?
    * A Central Authority trusted to verify public keys and issue certificated for the keys

72. What are the requirements for a session ID?
    * Session ID must not be guessable
    * Session ID must not be leaked

73. Why is a stram cipher mallabe?
    * Fixed input and output length
    * Same key gives same output

74. What is a keyed hash function?
    * A function producing a hash dependent on a key
    * Used to authenticate keys
    * Provides autheticity and integrity

75. What is TLS?
    * Transport Layer Security
    * Provides confidentiality, authetication and forward secrecy
    * Uses HTTPS

76. What is cross-site scripting?
    * When an attacker gets a users browser to unintentionally serve javascript to the users session

77. How can an attacker inject malicous scripts?
    * With user data visible for other users
    * URL variables
    * User data from post requests
    * Evaluating user data in client side script

78. How did the Samy Worm work?
    * MySpace protections only covered common HTML tags
    * Samy spread through CSS through any useable tag
    * Used post request to update user profiles

79. How does XSS through XML HTTP requests work?
    * Malicous scripts makes HTTP request to the current origin
    * When sucessfully injected, the attacker has the same rights as the user hijacked

80. How do you prevent XSS?
    1. Filtering input
        * Only for simple things
        * Dissallow characters
    2. Escaping output
        * HTML bodies
        * Quoted attributes
        * Unquoted attributes
        * Quoted strings in javascript
        * CSS attribute values
        * JSON data
        * Use libraries for this, do not implement yourselves
    3. Text formatting
        * HTML sanitisers
        * Use markup languages with safe conversion

81. What is CSRF?
    * Cross-site-request forgery
    * Tricks the broswer to use its session cookie to approve actions initiated by a third party site
    * Forces user to execute actions to another site than they are currently autheticated on
    * Targets state changes
    * Browser requests automatically include credentials
    * Sites have a hard time distinguishing between a forges request and a legitimate request from a user

82. What requests should be protected from CSRF?
    * Links
    * Forms
    * Pretty much all other GET/POST

83. Why should a developer not set a anti-CSRF token in a cookie and where should he place it instead?
    * Attacker could set the cookie from within the domain
    * Place token on all forms

84. What flags should be set to secure the session token?
    1. Secure
        * Sends the cookie through HTTPS only
    2. SameSite
        * Cookie is either always sent(None)
        * Only sent when the request is from the same origin(Strict)  
        * Only sendt with GET request(LAX)
    3. HttpOnly
        * Prevents stealing cookie with javascript
        * Cookie is always sendt in HTTP header, making it not available to scripts

85. What is CSP?
    * Content Security Policy
    * Set in HTTP header
    * Controls which sources content is allowed to come from
    * Limits inline scripts

86. What approaches can be used to define capabilities?
    * Enforced be a supervisor
    * Unguessable capatilities(random tokens, crypto signature,..)

87. What properties can a capability have?
    1. Transferable
       * Should be transferable between users
       * Capabilities generally dont care who uses them
    2. Abstraction
    3. Memory Safe
       * Endownment: A user might have instrisic capabilities given at creation
       * Creation: User gets capabilities to access an object he creates
       * Introduction: User transers a capability to another user
    4. Revokability
       * The creator of a capability should be able to revoke it
    5. anti-CSRF
       * Limits permissions to a specifies request type
    6. Collaboration
       * Run a program with shared capabilities to access shared resources
    7. Universal persistence
       * The state of the resource stays the same so it is never restarted

88. What is Capsicum?
    * Provides capability based security based security for UNIX programs
    * Extends the UNIX api's without replacing them or compromise performance

89. What capabilities does Capsicum provide?
    * Capabilities of file descriptors with a set of access rights
      * Around 60

90. What does capability mode in Capsicum do?
    * Restricts access to global name spaces
      * PID
      * File paths
      * POSIX IPC
      * System clocks/times

91.  How does Capsicum enforce the restriction in capability mode?
    * By restricing kernel primitives
    * In capability mode, the only availabe PID is the process's own PID
    * Child processes can only be accessed through capabilities

92.  What is serialization and deserialization?
    * Serialization: The process of turning objects of a programming language into byte arrays for transport
    * Deserialization: Turning transported byte arrays back into objects

93.  Why is incorrect deserialization dangerous?
    * The deserialized code is at the forefront of the program. Without is being properly deserialized, it could lead to bugs and give an attacker RCE access

94.  What are the entries in the secure software development cycle?
    1. Requirements
       * Map security and privacy requirements
    2. Design
       * Threat modeling
       * Security design preview
    3. Implementations
       * Static analysis
       * Peer review
    4. Testing
       * Security test cases
       * Dynamic analysis
    5. Deployment
       * Final Security review
       * Application security monitoring and response plan

95.  What are the non functional requirements and what does each entry contain?
    6. **Security and privacy**
          * The program functions according to the intentions in an adverserial enviroment
    7. **Availability, capacity, performance and efficiency**
          * *Availability*
            * The proporting of time a system spends in a functional state and not in downtime
            * Do decrease downtime and increase availability:
            * Write secure software
            * Not having bugs
            * Redundance
            * Rely less on service
            * Testing
            * Scalability
          * *Capacity* 
            * The Maximum number of simultanious users/transactions*
          * *Performance and effiency*
            * The ability to increase capacity and make use of scarce resources
    8. **Extensibility, maintainability, portability and scalability**
          * *Portability*
            * The ability of the software to run on different systems with little adaptation
    9. **Recoverability**
         * How easy it is for the system to recover from disruptive events
    10. **Manageability and serviceability**
         * How easy it is to develop, deploy and maintain the code
    11. *Cohesion*
       * The degree to which parts of system/module belong together

96.  What should be reviewed during a security review?
    * Security design
    * Peer review
    * Final security review before deployment

97.  What aspects of program should be logged?
    * Authenticated events
    * Attempted intrusions
    * Violations of invariants
    * Unusual behaviour
    * Performance statistics

98.  What is a program state and why is it important to security?
    * Program state consists of:
      * Variables
      * File descriptors
      * Cookies
      * Client storage

    * If a program reaches an unanticipated state, bugs could occur

99.  What is preservation of invariants?
    * The methods of an object ensures the internal state is a valid representation

100. What is immutability?
    * An object can not be changed after creation
    * Provides security since an attacker could not change objects to alter the state

101. What properties does an immutable class have?
     1. Keeping tue only reference to an object
     2. Not modifying the object
     3. Not providing setters
     4. Declare class as final

102. What is expressivity and rich expressivity?
     * Which types the language can express
     * Rich expresivity allows:
       * More checks to be performed by a type-checker
       * Easer to read code
       * Better code reuse

103. What are CERT's top 10 Secure conding practises?
     1. Pratice defence in depth
     2. Validate input
     3. Sanitize data to other systems
     4. Deny be default
     5. Adhere the principle of least priviledge
     6. Architect and design for policy enforcement
     7. Keep it simple
     8. Adopt a secure coding standard
     9. Heed compiler warnings
     10. Use effective quiality assurance tools

104. What is privacy a
     * The ability of the individual to control their personal data
  
105. What are the threats to privacy?
     1. Collection of information
     2. Aggreation of information(combining existing data to infer new information)
     3. Dissemination of information(spreading personal information)

106. What legal protections do we have in Norway?
     * EU diretive
       * GDPR
     * Norwegian law
       * Personopplysnings loven

107. What is GDPR?
     * General Data Protection Regulation
     * The right for individuals and obligations of data processors

108. What are the fundamental principles in GDPR?
     1. Lawfullness
     2. Fairness
     3. Transparancy

109. What rights does GDPR provide?
     1. Right of access
     2. Right of rectification
     3. Right to erasure
     4. Right to data restriction
     5. Right to data portability
     6. Right to object

110. What MUST consent be?
     1. Demonstratable
     2. Formulated clearly
     3. Specific to each kind of data
     4. Possible to withdraw

111. How must a service do to aquire consent?
     1. Divide into categories
     2. Provide the ability to ensure confidentiality, integreity, availability and resilience
     3. The ability to restore the availability, assessing the evaluating of the effectiveness of technical and organisational measures for ensuring the security of the processing  

112. What is onion routing?
     * Provides anonymity
     * Communication redirected through several hosts before reaching its destination
     * Each node in the network has an encryption layer that can only be decrypted by specific key

113. What is the TOR?
     * A network based on onion routing accessed from the TOR browser
     * Reveals hidden services living in the network

114. Is the TOR network safe from attacks and privacy intervention?
     * Nope
     * Timing attacks, browser fingerprinting, avoidance of proxies and malicous exit nodes pose a threat on the users using TOR
     * NSA also owns most of the exit nodes so...

115. What is I2P?
     * Garlic routing
     * Based on the peer to peer protocoll
     * All nodes in the network participates routing for all other nodes

116. What are some mobile threats and attack vectors?
     * **Attack vectors**
       * SMS
       * Telephone
       * Base Stations
       * WiFi
     * **Threats**
       * Mobiles stores a lot of personal and organistaional data
       * Session cookie can be stolen from phone
       * Phones can be used for crypto mining
       * NFC, phone bills etc

117. How are phones encrypted and how could an attacker exploit mobile networks?
     * Phone networks are encrypted from phones to the base stations
       * A5 block ciphers
     * An attacker could set up a rogue base station and MITM the mobile signals

118. What is Android components?
     * Applications are Java based
       * Each app with its own VM
     * Centered around components
       1. Activities
       2. Services
       3. Content providers
       4. Broadcast providers
     * Each component with its own class in Java
     * Components communicate through ICC systems called intents
       * Intents has an action string and data to operate on (URI)

119. What are Android activities?
     * User interface component displayed when the user interacts with the application
     * Activities recieve intents and in response interacts with the user

120. What are some vulnerabilies present on Android?
     1. Universal cross-site scripting(UXXS) through chrome and firefox through intents
     2. SQL injection in content providers. Providers resolve URI's and extract data for activities and services. The data is stored in SQLite databases. Interface provides no defence

121. How does most malware exploit Android?
     * By recieving dangerous permissions from the user
     * Preinstalled software
       * Sets up backdoors
       * Exfiltrate personal information
       * Installs its own TLS root certificates
     * Many collusions found in third party libraries