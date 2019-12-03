# INF226 Cheat Sheet

## Student Knowlegde

- The student has to:
  - Understand issues related to system development
  - Explain common weaknesses in software security
  - Identify common threats, risks and attack vectors
  - Know best practises to defend software

## Requirements, assumptions and mechanisms

### Security Definition

- Software security is the ability of software to function according
  to intentions in an adverserial environment.

#### Logical Arguments

- Conclusion
- Assumptions
- Deduction

#### Software Security Logic

- Identify security requirements
  - Capture the intentions of the software
  - Making requirements = spelling out our intentions
- Make assumptions about the enviroment the software until run
  - Making assumptions = spelling out our knowledge of the enviroment
- Design mechanisms satisfying the requirements given the assumptions

##### Examples of requirements

- Availability of the service
- Capacity
- Integrity of data
- Authenticity of data
- Recoverability

##### Examples of Mechanisms

- Choice of programming language
- Rate limiting
- Sanity checks on user inputs
- Access control lists
- Optimisation of algorithms
- Encryption

##### Examples of assumptions

- **Assumptions pointing towards problems:**

  - User input cannot be trusted to have property X
  - IP addresses can be spoofed
  - Computer resources are finite
  - Programmers write bugs

- **Assumptions pointing towards solutions:**
  - If the program checks the input, we know it has property X
  - An attacker cannot guess a random 128 bit number.
  - The semantics of the program.
  - The type checker is correct.
  - Internet routing is quite robust

## Vulnerabilities and Exploits

### Vulnerability Definition

- When software is in a cirumstance where the program fails to hehave according to intentions
- When the program fails to be secure

### Vulnerability Disclosure

- Should the vulnerability found be publicly disclosed?
  - How much detail?
  - Include an exploit?
  - Embargo period?
- **Stances:**
  - No disclosure: No details made public
  - Coordinated disclosure: Reveal details once the the fixes has been made
  - Full-disclosure: Full details should be publicly disclosed

### Exploit Definition

- Procedure which upon execution leads to a circumstance described a vulnerability, demonstrating the insecurity of the program

### Remote Code Execution(RCE)

- The most serious vulnerability
- Gives that attacker premission to execute code on the victims machine

### Buffer Overflow

#### The Call Stack

- Stores return address for function call
- On funciton call the pointer is pushed on the stack
- When function is down the pointer is popped from the stack

#### Buffer Overread

- Reading outside of the bounds of an array

#### Shell-Code exploit

- Fill the buffer with attackers code
- Overwrite return pointer to point to the array
- Often spawns a shell, giving the attacker RCE access to the machine

#### NO-OP sled

- When an attacker does not know the address of the buffer
- Attacker fills the buffer with NO-OPs and puts the shell at the end of buffer

#### Return Oriented Programming(ROP)

- Using preexisting code instead of uploading shell code

#### Prevention of Buffer Overflow

- Write better C code
- Static analysis
- Stack Canaries
- W^X
- Address space layout randomisation

#### Stack Canaries

- Secret value placed on the stack every time program is started
- When function returns the value, checks if return pointer has been modified
- If modified, program exits immeadiately

#### Address Space Layout Randomisation(ASLR)

- Practise of randomising the layout when allocating memory in the system
- Makes it more difficult, because attacker must guess the location of functions and libraries

#### W^X(Write XOR Executeable)

- Memory allocations gives the memory different properties

  - Writeable
  - Executeable

- OS enfoces that writeable memory cannot be executeable
  - Prevents loading shell code in writeable buffers
  - Does not prevent ROP

#### Best Practieses to Avoid Buffer Overflow

- Use memory-safe languages
- Use memory-safe abstractions in unsafe languages(e.g vectors and smart pointers in C++)
- Use the compiler
- Run Static analysers to identify bugs

#### Memory Safety

- Each part of the program is only given access to explicit memory locations they are permitted
- **Example**
  - Code from function could access:
    - Arguments from the caller
    - Local variables
    - Global variables
  - **Not** variabes of other functions
- **Breaking memory-safety:**

  - Pointer arithmetic
  - Unconstrained casting
  - No bounds-check on arrays access
  - Unsafe pointer de-allocation

- **Memory-Safe languages:**
  - Java/C#(counds check on arrays, runs in virtual machine)
  - Most scripting languages
  - Most functional Languages
- **Not Memory-Safe languages:**

  - Assembly
  - C
  - C++

- Achieving memory safety
  - Garbage collection
  - Resource allocation in initialisation(RAII) and borrows checker

### Undefined Behaviour

- When code behaves unspecified be the language standard
  - For example in C, dereffering Null

### SQL Injection

#### About SQL

- Relation databases
- Domain specific language
- Queries contructed for other languages
- Queries are constructed from user input

#### Problems with SQL

- Confusion between code and data
- Strings are used to represent data and queries

#### Preventing SQL Injections

- **Prepared Statements**
  - Statement with placeholders("?") where the user data will go later
  - Separates the user input and SQL queries sent to the server
  - Allows type checking arguments
  - Could lead to better performance

## Threats to Software

### STRIDE

- Sparks imagination when developing threat model

- **S**poofing
- **T**ampering
- **R**epudiation
- **I**nformation disclosure
- **D**enial of service
- **E**levation of priviledge

#### Spoofing

- Transmissions with intentialle mislabeled source
- When a person tricks the program to think he is someone else, giving him the credentiability of someone else

- URL spoofing
  - www.apple.com/ is actually www.xn--80ak6aa92e.com/
  - Browser displays as unicode characters, making it look like the apple website

#### Tampering

- Modification of persistend data or data in transport
- Examples
  - Injecting ads, malware etc in open wifi networks webpages
  - SQL injection to tamper with database

#### Repudiation

- Denial of perfoming unauthorized operations in systems where this cannot be tranced
- Repudiate: to refuse acknowledge
- For example a E-mails spoof, an untoward email was sent by a politician to another
- Does the sender have repudiation?

#### Information Disclosure

- Access data in an unauthorized fashiong
- Debug infor on production systems
- Passwords and other sensitive information logged as part of requests

#### Denial of Service

- Rendering a service unaccessible to intended users
- Flooding the service
- Exploiting vulnerability
- DNS hijacking

#### Elevation of Priviledge

- User gains more rights within a system then expected

### Ranking threats (DREAD)

- **D**amage potential
- **R**epoducibility
- **E**xploitation
- **A**ffected users
- **D**iscoverability

## Functional Decomposition and Threat Model

### Functional Decomposition

- An overview of components of the system
- A detailed map of comunication between componenents
- Description of the function of each of the components

### Threat Model

- Applicates our assumptions about a system
- What threats (Stride) applies to each component?
- Trust relationship between components?
- Which threats apply to each relationshipt?
- What motivates an attacker?
- What attack vectors can an attacker use?
- **To perform this analysis**:
  - Functional decomposition(diagram of software components)
  - An overview of trust-relationships between components
  - Good knowledge of security pitfalls(injectio, XSS, CSRF,..)

#### Threat Model Example Scenario

- **Assumption:** Some process on the system is misbehaving
  - e.g a buffer overflow in a service caused an attacker to gain RCE
- **Requirement:** Limit the impact of this break-in
- **Mechanisms:**

## Trusts and Boundaries

### Trust

- Is not binary
  - Can not trust HTTP requests with private info
- Is not linear
  - Different users, different relationships
- When data is communicated between component with different trust, it crosses a **boundary**

### Transport Security

- First level of security
  - E.g Sql injections can be sent over HTTPS
- Secrecy
- Authenticity
- Integrity

### Defence in Depth

- Analyse what happens when a security mechanism fails
- Are other parts affected?
- Linchpins?
- When mechanisms fails
  - Detect failure
  - Migitate failure

### Trusting Trust

- Should trusting trust be a part of threat model?
- At some point one must trust the people behind the software

#### Trusting Compilers

- Must trust the compiler to compile correctly
- A compiler could recognize code and compile backdoors
- To trust a compiler:
  - Read compiler source code
  - The circle of compilers:
    - Must trust the compiler who compiled the compiler
    - And the compiler who compiled that compiler and so on

##### Functional Equivalence

- Two programs are functionally equivalent if the output from the programs are same given the same input

##### Detection Strategy

- To test a compiler:
  - Requires independent compiler
  - ${S_{A}}$ is the source code of compiler ${A}$
  - ${E_{A}}$ the executeable of ${A}$
  - ${T}$ is a compiler independent of ${A}$
  - ${E_{T}}$ is the executeable of ${T}$
    1. Compile ${S_{A}}$ using ${E_{A}}$ to get an executable ${X}$
    2. Compile ${S_{A}}$ using ${E_{T}}$ to get an executable ${Y}$
    3. Compile ${S_{A}}$ using ${X}$ to get an executable ${V}$
    4. Compile ${S_{A}}$ using ${Y}$ to get an executable ${W}$
    5. Compare ${V}$ and ${W}$ bitwise
  - ${X}$ and ${Y}$ will be different binaries, but functionally equivalent

## OWASP Top 10

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

## CVE

    Common Vulnerabilities and Exposures

- Maintained be The Mitre Corporation
- Allows referencing vulnerabilities accross systems
- Easy to track and find vulnerabilities and fixes
- Entries consists of:
  - A unique number
    - CVE-YYYY-XXXX
  - Description
  - Public references

### CNAs

    Assigns CVE numbers

- Different scopes:
  - The Mitre Corporation(Primary CNA)
  - Distributed Weakness Filing Project(open-source projects)
  - Corporations(Google, Intel, Netflix,..)

### CVSS

    Common Vulnerability Scoring System

- Assigns score to vulnerability
- 0 to 10
- Metrics:
  - Base metrics, intrinsic properties
  - Temporal metrics, changes to the vulnerability over time
  - Enviromental metrics, specifics to the enviroment of the software

#### Base Metrics

- Access Vector
  - Local
  - Adjacent network
  - Network
- Attack complexity(High, Medium, Low)
- Authenticity(Multiple, Single, None)

#### Impact Metrics

- Rated on a scale from None/Partial/Complete impact
  - Confidentiality
  - Integreity
  - Availability

#### Temporal Metrics

     Metrics who changes over time:

- **Exploitability**
  - Unproven
  - Proof-of-concept
  - Functional
  - High
- **Remediation level**
  - Official fix
  - Temporary fix
  - Workaround
  - Unavailable
- **Report confidence**
  - Unconfirmed
  - Uncorroborated
  - Confirmed

## CWE

    Common Weakness Enumeration

- List of common weaknesses present in software
- More fine-grained then Owasp Top 10, but similar
- CWE's often given as outputs from security analysis tools
- Structured by:
  - Architecture concepts
  - Development concepts
  - Research conepts

## NVD

    National Vulnerability Database

- Contains analysis of known vulnerabilities
  - CVE numbers
  - CWE numbers
  - CVSS
  - Versions affected

## Security Tools

### Static analysis

    Inspects source code

- Program flow analysis
- Contraints analysis
- Logic tests
- Linting

### Dynamic analysis

    Inspects running software

- **Fuzzer**
  - Feeds random data in to the program to trigger anomalies
- **Crawlers**
  - Maps the attack surface of the program
- **Man-in-the-middle proxy**
  - Analyses data from normal usage

## Access Control

    Decides which users can do what

- Read/write to objects
- Perform operations(start processes, allocat memory,..)
- Grant/revoke access

### Access Control Aspects

- Physical
- Logical
- Cryptographic
- Social

### Mandatory Access Control(MAC)

    Access control policies are fixed by a central authority

- Central, non-transferable access
- Operating systems have mandatory access control over resources(cpu, memory, storage)
- In addition there are systems for implementing more MAC security:
  - SELinux
  - Linux Security Modules (AppArmor)
  - Mandatory Integrity Control on Windows (Extending ACLs)
  - Language based mechanisms (e.g. Java Security Manager)

### Discretionary Access Control(DAC)

    Users specifies premissions for their own objects

- At least some priviledges are transferable
- File systems
- E-mail
- WIFI passwords

### Access Control Models

- Access control lists
- Role based access control
- Capability based access control

### Access Control lists

- Premissions are given to each object, giving users different permissions with it
- Each object has a list of permissions assigned to different users
- Premissions structured according to **users and groups**

#### The Confused Deputy

- Typical faillure
- Priviledged process(deputy) is tricked to perform bad actions on behalf of less priviledged process
- Can for be e.g copilers, browsers acting as deputy on the behalf

#### Users and Groups

- User ID (UID)
- Group ID (GID)
- A program gets a Process ID(PID) when its run
  - Prevents users accessing eachothers memory
  - Files has Owner UID and Group GID
    - Read
    - Write
    - Execute
- **SUID**
  - Set UID(SUID)
    - Process is set to file owner
  - Set GID(SGID)
    - Process is set to file group
  - Sticky-Bit
    - File can only be renamed/deleted by the files owner or root
  - Can also apply for directories, not only files

### Rôle Based Access Control(RBAC)

    A set of roles abstract the permissions from the users

- Actions are always performed by a rôle
- Users must reauthenticate to change a rôle

```haskell
                    [Role0]         -->   [Permission0]
            -->                 |
[User0]                         |
            -->                 '->
                    [Role1]         -->  [Permission1]
            -->             |
[User1]                     |
            -->             '->
                    [Role2]         -->   [Permission2]
```

- Example of usage:
  - U = {alice, bob}
  - R = {doctor, patient}
  - P = {writePerscription, withdrawMedicine}
  - RôlePerm = {(doctor,writePerscription), (patient, withdrawMedicine)}
  - UserRoles = {(alice, doctor), (bob, patient), (alice, patient)}

#### Rôle of OS

- Ochestrate processes(software)
  - Provide abstract interface for hardware(drivers)
  - Communicate with programs through **system calls**
    - Interrupts and returns control to OS
- Different protections for different resources
- **Memory**
  - Virtual memory mapping
  - Limits
- **Cpu**
  - Scheduling policy
- **File systems**
  - Permissions
  - Chroot or other restrictions
  - Quotas
- **Open files/sockets/network connections**
  - File descriptors
  - Limits

### Capability Based Access Control

    Users has capabilities

- A capability is
  - A reference to an object
  - A set of permissions for that object
- Used whenever a resource is accessed

```haskell

[User0] --> [Capability0]
            [Object0    ]
            [Read       ]

[User0] ---------------->   [Capability2]
                            [Object0    ]
                            [Read       ]
                            [Write      ]


[User0] --> [Capability2]
            [Object1    ]
            [Read       ]
            [Write      ]
```

#### File Descriptors

        File descriptors are capabilities of accessing a file

- Each process has its own file-descriptor table
- Used also for:
  - stdout/stdin/stderr
  - pipes
  - sockets(network access)

- OS checks permissions when opening files and creating descriptor
  - Can be transferred between processes
  - Recipient processs does nt need to have permission to access the file to use the file-descriptor

## Memory Protection

### Virtual Memory Mapping

- Inconvenient to let programs use physical memory

- **With virtual memory:**
  - Each program gets their own virtual address space
  - Memory locations not decided at compile time
  - Memory fragmentation hidden from programs
  - Easy to page out to swap
- As a consequence processes cannot directly adress the memory of other processes

- **Exceptions:**
  - Processes can allocate shared memory
  - Processes can attach them selves as a debugger for another process

## File System Abstraction

### Unix File System

- Directories group the files into logical parts
  - /bin
  - /sbin
  - /etc
  - /dev
  - /home
  - tmp
  - ...

- Operating system can restrict access by changing root directory to a different directory with **Chroot**
  - Provides system virtualisation
  - Chroot does not however:
  - Restrict network access
  - Restrict usage of system resrouces
  - Prevent comunication between processes

## System Calls

### OpenBSD Pledge

    Mechanism restricting what system calls are allowed for each process

- Calling plegde with a list of system call groups, restricts the process from accessing most system calls not on the list

## OS Virtualisation

- In addition to manually separate priviledges using the OS's mechanisms we can:
  - Abstract away the the OS system calls
    - OS virtualization(Docker, FreeBSD..)
  - Abstract away hardware:
    - Full virtualization: run different ISA
    - Paravirtualization: Runs cpu instructions natively

### Linux Kernel namespaces

- Groups processes so each group has individual:
  - Filesystem mount tables
  - Process tables
  - Network stack
  - UID tables

### Docker

#### Containers

- Not virtual machines!
  - If resource not namespaced by linux kernel, it is global and can be affected by the container
- Containers are systematically separated using OS mechanisms
- Templated by images
  - Image constructs container
  - Predictable enviroment
- Construction and administration through container daemon

#### Separation mechanisms

- Chroot
- Namespaces
  - Gives each container individual:
    - Mount tables
    - Process tables
    - Network stack
    - UID tables
- Cgroups to limit resources of each container

#### Capabilities

- For each container
- Abstraction of OS level restrictions
- Whitelisted capabilities are allowed

#### Docker Security

- Divided in:
  - Underlying OS level separation mechanisms
  - Dockererd daemon attack surface
  - Security of container configuration

## Priviledge Separation

### Principle of Least Priviledge

        Every program and every user should operate using the least amount og priviledge necessary to complete the job

## Preventing Priviledge Escalation in SSH

- **OpenSSH**
  - Part of OpenBSD project
  - Found on most unix systems
  - Secure remote access (PKI)

### Privilegde Separation in SSH

- **Monitor**
  - Priviledged
  - Provides interface for slaves to perform priviledged operations
  - Validates requests
  - Finite state machine
  - Perform actions on slaves behalf

- **Slave**
  - Unpriviledged
  - Does most of the work
  - Calls on monitor when priviledged operations must be performed

- [Encryption keys] [File system] <--> [Monitor] <--> [Slave] <--> [Client]

### Implementing Monitor/Slave Pattern

- **Goal:** Limit the amount of code running in a priviledged process

#### Identifying Priviledged Operations

        Defines a service specific monitor/slave interface

- File access
- Accessing crypto keys
- Data base access
- Spawning pseudo-terminals
- Binding to a network interface

#### Request types

- Information
- Capabilities
- Change of identity

#### Phases

- **Pre authentication**
  - Slave has as little priviledge as possible 
  - Monitor only accespts authentication from slave

- **Post authentication**
  - Slave has normal user priviledges
  - Monitor validates requests requiring additional priviledges

#### Slave/Monitor Connection

- On connection, service spawns a seperate monitor/slave pair for that connection
- Slave is created by:
    1. Changing UID and GID to unused values
    2. Chrooted into an empty, unwriteable directory
    3. Marked as P-SUGID
    4. pledge("stdio, NULL)
- Slave is given the file descriptor for the connection

#### Slave/Master Communication

- Through IPC mechanisms
  - Pipe
  - Shared memory
  - Socket-pair

#### Change of Identity

- Slave should run as normal user when autheticated
- Unix does however not support changing UID of a rpocess without UID=0
  - Solution:
    1. Terminate slave and
    2. Monitor spawns a new process with correct UID/GID
- To continue, slave sessions must be retained

#### Retaining Slave State

- To retain a slave:
  - Serialize data structures and transfer to master
  - Allocate dynamic memory resources on memory shared with master

- When new slave is spawned:
  - Serialize data structures are passed through IPC
  - Memory shared with new slave

### Priviledge in SSHD

- **Allows:**
  - Access allow Diffie-Hellman
  - Signes a challenge with server private key to authenticate the connection
  - User validation
  - Password authentication
  - Public key authentication

- **Change of identity**
  - Data structures are serialized
  - Shared memory transferred

- **Priviledged operations in sshd**
  - In post-authentication phase:
    - Key exchange supports renewing crypto keys
    - Pseudo terminal creation (PTY)
      - Requires root permissions to change ownership of device
      - Passes file descriptor to the client

### SSH Attacker Scenario

- **Assumption**: RCE gives an attacker control over the slave
  - Possible Esclation paths:
    - **Taking over system processes**
      - Restricted by UID
      - Other slaves protected by P_SGUID
    - **System calls to change the file system**
      - Root file system empty and unwriteable
    - **Local network connections**
      - Not preventable by this mechanism
      - May abuse IP trust relationships
    - **Information Gathering**
      - System time
      - PID of process
    - **Using up system resources**
      - Fork bomb
      - Intensive computations

## Passwords

- By increasing alphabet, the length only grows constant with the size

- **Nist**
  - Require a minimum length of 8 or greater
  - Allow atleast 64 characters
  - Check lists of known passwords
    - Dictionairy words
    - Repetetive characters
    - Context specific words
    - Previous breached passwords

### Hasing password

- One way(given y, difficult to find x)
- Collision free(difficult to find x and x´ such that h(x)=h(x´))
- Small input yields large difference in output
- Quick to compute

### Uses of hash functions

- Checksumming data
- Data identifier
- Hashing passwords
- Signature verification/generation
- Building crypto primitives

### Hashing issues

- Same hash for same reused password
- Hashes can be computed in a dictionairy an attacker could use to brute force the password

### Rainbow tables

- Tool to derive passwords by looking only at hash value
- time-space tradeoff when creating look-up table for hash values -> plaintext
- Precomputed table for reversing cryptographic hash functions
- Mainly used for cracking passwords
- Uses less processing power than a brute force attack

### Salting

- Generates random string and store it in the hash
- Harder to crack
- Does not help againt brute force attack on single password
- Unix systems use 128-bit salts

### Key Derivation Functions

- Derives plaintext from hashs
- Requirements:
  - One-way
  - Collision free
  - Small input to large output
  - CPU intensive
  - Memory expensive
  - Sequential

#### Naïve key derivation

- Generate random byte-strings and store it before and after hash
- attacker must guess the second string
- The second string works as a cost parameter

#### SCrypt

- Previous key derivation is trivially computed in paralell at no additional memory cost
- SCrypt is maximally memory hard
- **Downside:** Due to its use in crypto-currencies, fast specialized circuits for scrpyt

- r block size parameter
- N CPU/Memory cost parameter
- p parallelism parameter

#### Other Password Guessing Prevention Measures

- Rate limiting password attempts
- Proof-of-work from client

## Authentication

    The act of verifying the identity of actors in the system

### Two Factor Authentication

- Additional authetication mechanism to passwords
- Examples:
  - SMS codes
  - Print out codes
  - Time based passwords (TOTP)
  - Approval from allready authenticated device
  - Public key crypto(U2F/FIDO, WebAuth)

- Could be vulnerable to phising
- Public-key systems in browsers can prevent proxy-attacks
- WebAuthn is a new W3C standard

### Password Recovery

- **Trust upon first use**
  - Man in the middle does not strike first
  - Trust upon first session and use that as authentication for the next sessions

### Centralized Certificate Authorities (CA)

- Trust a central authority to verify public keys
- Issues ceritificates for public keys

### Other schemes

- Preexisting shared secrets
- Out-of-band communication

### Verify Logged in Users

- How do we verify the requests from a logged in user is actually consistently from the authenticated user?

#### Session IDs

- **Requires:**
  - Entropy: Session ID must not be guessable
  - Secrecy: Session ID must not be leaked

- **Entropy**
  - Finite resource on any system
  - Not all random generators are suitabe for creating session ID
    - Java.util.random for examples, is guessable by only looking at a few bytes

## Stream Ciphers and Message Authetication Codes

### Stream Ciphers

- Most are based on block ciphers
  - Fixed input and output length
  - Same key gives same output
  - [Seed = key] --> [Crypto RNG] --> [ [Pseudo random stream] [Plaintext data stream] ]--> (XOR) --> [Cipher Stream]
  - Based on cryto pseudo-random generators
  - Proves safe extension to arbitrary inputs
  - **Are mallabe**

### Message Authetication Codes

#### Keyed Hash Function

- [[Key]  [Message]] --> [Keyed hash function] --> [MAC]
- Produces a hash dependent on key
- Used to autheticate keys
  - Derive a key from shared secret
  - Sender computes hash of encrypted message and attaches hash
  - Reciever computes keyed hash recieved message and compare with attached hash
- Provides authenticity and integrity

- **Message structure**
  - [MAC] --> [IV] --> [Encrypted message]

### TLS

- Transport Layer Security
- Version 1,3
- Provides:
  - Confidentiality
  - Authentication
  - Forward secrecy

- Uses AES and CBC-MAC
- ChaCha20 and Poly1305 MAC
- HTTPS

## Cross-Site Scripting

- When web-server unintentionally serves javasript from an attacker to client browser
- How to inject script:
  - User data from one user visible to another
  - URL variables
  - User data from post requests
  - Evaluating user data in client side script

### Samy Worm

- Spread MySpace
- Fastest worm
- Mostly harless
- Cross site scripting worm

#### How Samy Worm Works

- MySpace tried to protect by only allow < a >, < img > and < div > and strip javascript
- Javascript in CSS any tag who could be used
- Browsers accept javascript

### XML HTTPRequest

- Scripts make HTTP request to the current origin
- When injected, the attacker could do anything the user could do
  - GET pages
  - Post forms
- Samy used POST request to update profiles

### XSS Prevention

#### Filtering Input

- For simple things
- Disallow characters
- Can work for usernames or e-mail addresses

#### Escaping Output

- How to escape HTML depends on the context
- Important situations:
  - HTML body < div>DATA< /div>
  - Quoted attributs < div id = "DATA">< /div>
  - Unquoted attributed
  - Quoted Strings in javascript
  - CSS attribute values
  - JSON data
  - ...
- Do not implement youself!!
- For String places in HTML
  - " & → & amp; "
  - " < → & lt; "
  - " > → & gt; "
  - " " → & quot; "
  - " ' → & #x27; "
  - " / → & #x2F; "

- **Don'ts**
  - Some places to avoid place untrusted data
  - Tag names
  - Attribute names
  - Scripts
  - Directly in CSS

#### Text Formatting

- We want to let the user format their input, but worry about them getting to use HTML
- Solutions:
  - HTML sanitisers
  - User another markup language with safe conversion

## Cross-Site Request Forgery(CSRF)

- Tricks the browser to use its session cookie to approve actions initiated by a third party site
- Forces a user to execute unwanted actions on a site they are currently authenticated on
- Targets state change requests
- Browser requests automatically includes credentials
- Site can not distinguish between a forged request and legit request

### CSRF Protection

- What should be protected:
  - Links
  - Forms
  - All other POST/GET
- **Do not** put CSRF token in a cookie
  - Attacker could set the cookie from the domain, making him able to forge requests
  - Add anti-CSRF tokens on all forms
  - SameSite flag

## Securing The Session Token(Cookie)

- Three flags should be set
  1. Secure
  2. SameSite
  3. HttpOnly
- If site uses a lot of javascript, store it locally

### Cookies and Same-Origin

- Restricts script to only resources from the same origin
- Cookies are not covered by default by same-origin
- Solution = set secure flag on cookie

### The Secure Flag

- Sets the cookie to only transmit if the site is HTTPS

### The SameSite Flag

- Three values:
    1. **None**: cookie is always sent
    2. **Strict**: cookie is sent when the request is from the same origin
    3. **Lax**: cookie is only sendt only with GET request

### The HTTP Only Flag

- Prevents stealing user cookie with javascript
- Cookie is always sent with HTTP-header
- Making it not available to scripts

### Content Security Policy(CSP)

- Set in the HTTP header
- Control which sources content is allowed to come from
- Voilation reported to the server
- Limits inline scripts
- Limitations:
  - Correctly escaped HTML output is still needed
  - Difficult to get third party scrips to adhere policies
- Cannot rely on browser support for CSP
- Asset types
  - default-src: all assets
  - style-src: stylesheets
  - frame-src: iframe srouces
  - EventSource -font-src: font files(flash and others)

## Using Capabilities

- **Recap**:
  - Consists of:
    - Reference to an object
    - A set of permissions for the object
  - Used whenever a resource is accessed

- Give only the capabilities needed
- Decide what capabilites to give to different resrouces
- Capabilites should be **unforgeable**, otherwise it's a usesless security measure

### Approaces

1. **Enforced by supervisor(os, vm, compiler, ...)**
2. **Unguessable capabilites(random tokens, crypto signatures,...)**
     - Relies on entropy and cryptograhic security
     - Can be referenced by random number
     - Can be signed

### Capabilities Properties

#### Transferrable Capabilities

- Should be transferrable between users
  - Generally capabilites do not care who uses them
  - This prevents possibly confused deputies

#### Capabilites Abstraction

- The following properties are treated the same:
  - The capability of reading from a file
  - The capability of reading from a network connection

#### Memory Safe Capabilities

- Can be obtained by:
  - Endowment: a user might have intrinsic capabilities given at creation
  - Creation: User gets capability to access an object he creates
  - Introduction: User transfers a capability to another user
- Approach relies on memory safety of the language

#### Revokability

- The creator of a capability should be able to revoke it
- Can be temporal or partial

#### CSRF Capabilities

- CSRF-tokens can be viewd as capabilities
- Denotes and object and limits permissions to specified request types
- Unforgable(unguessable)

#### Capabilities for Collaboration

- Run a program with shared capabilities to access shared resources

#### Universal Persistence

- The state of a resource stay the same with the same capabilities
- E.g a program state stays the same so it's never restarted
- Problem:
  - How to retain capabilities when a program restarts?
    - A login manages could reconnect the user to their running programs

## Capsicum

- Design goals:
  1. Provide capability based security for Unix programs
  2. Extend, not replace Unix API's
  3. Performance comparable to already emplyed priviledge separation mechanisms

- Introduces a special capability mode for processes
- Provides new kernel primitives(cap_enter, cap_new, ...)
- Changing external primitives when in capability mode
- USerspace library

### Capsicum Capabilities

- Capabilities of file descriptors along with a set of access rights
  - Around 60 access rights
- New capabilities are created through cap_new by giving it a file descriptor and rights mask
  - Capabilities transferre through inter process communication(IPC) channels(e.g sockets)

### Enforcing Capabilities in Capsicum

- Capability modes restricts access to global name spaces such as:
  - Process ID
  - File paths
  - POSIX IPC(inter process-communication)
  - System clocks/timers

### Restricting existing kernel primitives

- In order to enforce these restrictives, man kernel primitives must be changed
- opennat(desc, path) opens a file located at relative path from the directory refrenced in desc
  - No " .. " allowed in capability mode to repent path traversal
- In capability mode, the only PID is the process's own PID
- Child processes can be accessed through capabilities

### Adopting Programs To Capsicum

- Typical strucutre of programs using capsicum:
  - Obtain resrouces(using system abient authorities)
  - Wrap resrouces in capabilities
  - Enter capability mode
  - Use resources
- Each program uses capability in isolation. The system itself is based on the traditional security model

#### tcpdump

- Outputs descriptions of network packets matching given filter

- Priviledges are aquired early
- Priviledged operations are separate from the messy parsing of packets
- DNS resolver relied on file access, therefor hade to be changed to external daemon

#### dhclient

- Is OpenBSD's DHCP client and is already using priviledge separation

#### gzip

    Command-line-compression tool

- Priviledge separation through chroot/unprivildged UID is stupid
- Modifying gzip to use libcapsicum
  - Three critical functions are put in capability mode
  - 409 lines added to gzip

#### Chromium

- Open souce siblig of Chrome browser
- Has different sandboxing with different implementations on different platforms
  - Each tab is a rendered platform
  - Resources already forwarded through file descriptors
- Before capsicum, the FreeBSD port of chrome did not use any sandboxing

## Serialization

- **Serialization**: The process of turning objects of a programming language into byte arrays for transport

- **Deserialization**: The process or turning byte stack back into objects

- Java serialization
  - Has reflection, gives dunamic method invocation
    - Takes a method name string, ang argument strings
    - Applies it to an object
- JSON
- Pickle(Python)
  - Pickle library is dangerous
- Protocol buffers

### Incorrect Deserialization

- The code deserialating is at the forefront of the program security
- Bugs could lead to RCE

## Security Trough The Software Development Cycle

- Definition: The ability of software to function according to intentions in an adverserial enviroment
- Assumptions -> Security mechanisms -> Security requirements

### Software Development Cycle
  
  1. Requirements
      - Map security and privacy requirements
  2. Design
       - Threat Modeling
       - Security design review  
  3. Implementations
       - Static analysis
       - Peer review
  4. Testing
      - Security test cases
      - Dynamic analysis
  5. Deployment
      - Final Security review
      - Application security monitoring and response plan  

### Non-Functional Requirements

- Security and privacy
- Availability, capacity, performance and efficiency
- Extensibility, maintainability, portability and scalability
- Recoverability
- Manageability and serviceability
- Cohesion

#### Availability

    The proportion of time a system spends in a functional state

- Causes for downtime:
  - Malicous attacks
  - Software bugs
  - Hardware failures
  - Failure of service
  - Excessive usage

- Increasing availability
  - Write secure software
  - Not having bugs
  - Redundance
  - Less reliance of service
  - Testing
  - Scalability

#### Capacity

    The maximum number of simulaneous users/transactions

#### Scalability

    The ability to increase capacity

- What are the bottle-necks?
  - Load balancing
  - Location
  - Secure communicaton between instances
  - Secure communication between instances
  - Eventual consistency

#### Performance

- Responsiveness of the software to users
- Rate of transaction processing

#### Effiency

    The ability to make use of scarce resources

- Memory/cache
- CPU power
- Storage
- Network bandwidth
- Latency

#### Maintainability and Extensibility

- How easy it is to develop and deploy fixes and new features
- How easy is it to maintain the code?
  - Readability
  - Structural properties
  - Documentation
- Merging
  - How often?
  - How to ensure quality?
- How easy is it to develop a new version?
  - Malicous updates?

#### Portability

    The ability of the software to run on different systems with little adaptation

#### Recoverability

    The time to recover from disruptive events

- Backups
- Failover systems
- Update deployment

#### Cohesion

    The degree to which parts of a system/module belong together

- Strong cohesion: Each module is robust and reusable

### Security Review

- Security design review
- Peer review
  - Reviweing commits
  - Pair programming
- Final security review before deployment

### Logging

- Error messages should:
  - Be logged to a separate safe storage
  - be append only
- What to log:
  1. Authentication events
  2. Attempted instrusions
  3. Violations of invariants
  4. Unusual behaviour
  5. Performance statistics

- What not to log:
  1. Sensitive information
  2. Keys
  3. Passwords
  4. User data

### Monitoring

- To respond to an ongiong threat:
  1. Detection
  2. Logging
  3. Monitoring
  4. Response

## State

### Program State

- Program state consists of:
  - Variables
  - File descriptors
  - Cookies
  - Client Storage

- Some states control the flow of the program
- Some state is just data being passed around
- Controlling the state of a program is essential to security
  - Bugs can occur if the program reaches an unanticipated state

- An object is the combinations of a representation and interface
- **Preservation of invariants**: The methods of an object ensures the internal state is a valid representation

- Problem:
  - If you pass reference to a mutable objevt, you give permission to mutate the object
  - If you accept a reference to a mutable object, you must also accept it mutates beyond your control

## Immutability

    An object cannot be changed after creation

### Immutability in Java

#### Strings in Java

- String interning: Every copy is only stored once
- String doesnt change, so we never have to recompute hashcode
- Thread safe
- Security

#### Sum Types in Java

- Any reference in Java can be null
- Every reference behaves like A + 1 (where 1 represents null value)

#### Making Immutable classes

- An immutable class can hide a muteable object by
  1. Keeping the only reference to this object
  2. Not modifying the object
  3. Not providing setters
  4. Declare the class as final

### Expressivity

- Which types the language can express
- Different types for different languages
- **Rich expressivity** allows:
  - More checks to be performed by type-checker
  - Easier to read code
  - Better code reuse

- Common type formers:
  - Parameterised types (generics)
  - Record ttpes/product types
  - Sum types
  - Function types
  - Dependent types

### The Maybe Type

- Used to throw exceptions to prevent NullPointerExceptions

#### Null Reference

- Often given special meanings by functions or classes
  - No elements found
  - No parameter present
- Important to remeber null checks

#### NullPointerExceptions

- Leads to unexpected control flows
- Unexprected states could be unsecure

## CERT Top 10 Secure Coding Practises

1. **Practise defence in depth**
   - Keep the number of linchpins down
   - Plan for failure of individual components
   - Program defensively

2. **Validate Input**
   - Regard all input with suspicion
   - Map the surface of the program to detemine the input points
   - Formualte explicit descriptions of all possible inputs(protocol, format,...)
   - Validate inputs according to theses descriptions

3. **Sanitize Data to Other Systems**
   - Covers
     - SQL Injections
     - XSS
     - Command injection
     - File paths

   - Whenever a astring is transferred:
     1. Idenetify protocol of format
     2. Identify which parts come from unstrusted sources
     3. Sanitize the data appropriately

4. **Deny by Default**

5. **Adhere the principle of least priviledge**

6. **Architect and design for policy enforcement**

7. **Keep it simple**

8. **Adopt a secure coding standard**
     - How to make programs secure and correct programs vary from language and platform
     - Make yourself familiar with how security challenges are handled on your platform

9. **Heed compiler warnings**

10. **Use effective quality assurance tools**
    - Fuzzers
    - Property bases checking

## Privacy and Legal Rights

### Privacy

    The ability of the individual to control their personal information

- **Threats to privacy**
  1. Collection of information
  2. Aggregation of information
     - To combine existing data to infer new information
  3. Dissemination of information
     - Spreading personal information

### Legal Protection

- **EU directive**
  - GDPR
- **Norwegian law**
  - Personopplysnings loven
  - Datatilsynet is the norwegian supervisory authority related to privacy issues

### GDPR

- General data protection regulation
- The rights of individuals
- Obligations of data processors

- Fundamental principles:
  1. Lawfullness
  2. Fairness
      - The data processing should not exceed what the data subject can reasonably expect
  3. Transparancy
      - Information about what is collected must be clearly stated

- Rights
  1. Right of access
  2. Right to rectification
  3. Right to erasure
  4. Right to data restriction
  5. Right to data portability
  6. Right to object

- Should have a "Forget me" function
- See data collected
- Be carefull about third part access to data

### Minimise data collection

- Do not collect the data you do not need
- Keep the data log only for as long as you need

### Consent

- Must be demonstratable
- Must be formulated clear and in plain language
- Must be specifc to each kind of data
- Must be possible to withdraw

- **Aquiring consent**
  - Divide into categories
  - Ask for consent for each category upon registration of users
  - Store separate consents as field in a database
  - Interface for chaning consent settings
  - No prefilled checkboxes

### Obligations of the Controller and Processor

- Data protection by design and by default
- Security of processing
- Communication of a personal data breach to the data subject
- Notification of a personal data breach to the supervisory authority
  - Not later than 72 hours
- Data protection impact assessment
- Position of the data protection officer
  - Meant to ensure that the organization complies with privacy laws
  - Shall have direct communication with leaders who make decisions in privacy matters
  - Must perform audits of compliance
  - Protection from being layed-off

- The processor shall implement
  1. The pseudonymation and ecryption of personal data
  2. The ability to ensure the ongoing:
     - Confidentiality
     - Integrity
     - Availability and
     - Resilience of processing systems and services
  3. The ability to restore the availability and access to personal data in a timely manner in the event of physical or technical incident
  4. A process for regularly testing, assessing the evaluating the effectiveness of technical and organisational measures for ensuring the security of the processing
  
### Onion Routing

- Mixed network
  - Communication is redirected through several hosts before reaching its destination
  - Not usefull if the data reveals information about source/destination
  - Solved by onion routing through encryption

- An onion has encryption layers
  - On layer can only be decrypted by a specific relay
  - Relay forwards message to next relay until it has reached its destination

#### TOR

- Based on firefox
- Can reveal hidden services living in the network
- Node network
  - Client
  - Relay
  - Out-proxy
- Attacks on Tor
  - Timing attacks
  - Browser fingerprinting
  - Avoiding proxy
  - Malicous exit nodes
  - ...

#### I2P

- Garlic routing
- Peer to Peer
- Undirectional routing
- All nodes participate routing for other nodes
- Each peer has a fixed number of client tunnels
- Services have public input tunnels

## Mobile Security

- Attack vectors
  - SMS
  - Telephone
  - Base Stations
  - WiFi

- Mobile applications can access
  1. Sensors
     - Can be used for sureveillance
  2. Network
  3. Storage
- Runs bytecode as OS process
- Can communicated with other devices
- Can have Two-factor authetication tokens 

### Mobile Threats

- Mobiles are increasingly valuable targets
- Stores a lot of personal data
  - Advertisment
  - Phising
  - Extorrsion
- Stores organisational data
  - Contacts
  - Calendar
  - Documents(trade secrets)
- Session cookies on phone
- Can be coin mined
- Connected to bill systems(NFC, phone bills)

### Mobile Network Security

- Networks are encrypted from phones to the base station
  - A5 block ciphers
  - Encryption can be turned off
- Rogue base stations can MITM mobile signals
- Important that applications use TLS or other application layer encryption

### Android Security

- Based on linux
  - Each app has its own UID
  - Each app has its own Lonux process
- Java as application platform
  - Each app as its own VM

- Android are centered around components
  1. Activities
  2. Services
  3. Content providers
  4. Broadcast providers
- Each component implemented by a class in Java
- Components communicate through an Inter Component Communication(ICC) system called intents
  - Intents consists of:
    - Action string
    - Data to operate on (URI)

#### Intent Permission

- Intent listeners are either exported or private to the application
  - Exported are accessible from any app
  - Private are only accessible from components within the app

#### Android Activities

- User interface components displayed when the user interacts with the application
- Activities recieve intents, and in response interacts with the user

#### Universal Cross-Site Scripting (UXSS)

- Chrome and firefox have been vulnerable on android through intents

#### SQL Injection in Content Providers

- Content providers resolve URI's and extract data for activities and services
- Stores in SQLite databases, but interface provides no prevention of SQL injection attacks

#### Sandoxing and Encryption

- Android processes are separated using usual Linux mechanisms
  - **SELinux** provides Mandatory Access Control(MAC)
    - Each application runs in its own SELinux sandbox
  - **Seccomp** filters system calls

#### Android Storage

- Android uses dm-crypt to encrypt its 
- Provides confidentiality, but not integrity
- Provides encrypted storage of encryption keys through Android KeyStore
  - Hardware based through trusted execution enviroment or
  - Software based

#### Malware on Android

- Dangerous permissions
  - Give the application permissions to resources on phone
- Preinstalled software
  - Sets up backdoors
  - Exfiltrate personal information
  - Install TLS root certificates
  - Some preinstalled apps contained malware
- Collusion found in third party libraries

### iOS

- Developed in-house from hardware to native applications
- Heavy investment in security 
- Remote iOS jailbrakes
- The slides for this topic were horrible :( 