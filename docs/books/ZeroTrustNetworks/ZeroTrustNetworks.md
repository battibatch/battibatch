# Zero Trust Networks 2 ed.
Rais, Razi et al.
March 2024

## Chapter 01: Zero Trust Fundamentals
What is Zero Trust Network
- Network is always assumed to be hostile
- external and internal threats exist on the network at all times
- network locality alone is not sufficient for deciding trust
- every device, user, and network flow is authenticated and authorized
- policies must be dynamic nd calculated from as many sources of data as possible

![alt text](image.png)
disadvantages
- lack of intra-zone traffic inspection
- lack of flexibility
- single points of failure

![alt text](image-1.png)
control plane; everything else is the data plane

Evolution of perimeter model
- private IP address
- Private networks connect to public networks
![alt text](image-2.png)
- NAT: Network address translator
![alt text](image-3.png)

Evolution of threats
![alt text](image-4.png)

Perimeter has too many shortcomings
- trust
![alt text](image-5.png)
![alt text](image-6.png)

before starting w/ ZTA, you must know where trust lies in apps

ZTA does not use walls like perimeter
3 key ZTA components
- User/app Auth and authz
- device auth and authz
- trust score - computed


## Chapter 02: Managing Trust

operator to manage trust
![alt text](image-7.png)

Threat models are great to start w/ for ZTA
Categories of attacker listed in increasing capabilities
1. opportunistic attackers
2. targeted attackers
3. insider threats
4. Trusted Insider
5. State level actor

ZTA's Threat model
- RFC 3552 describes the internet threat model; ZTA follows
- ZTA does not defend against everything, by types of adversaries that are common in hostile networks

Strong authentication is required
- X.509, TLS/SSL
![alt text](image-8.png)
- Certs are not enough
    - Public Key Infrastructure (PKI) like Certificate authorities (CA)
    - Provides identity through the ZTA network for
        - devices, users, apps
- Public PKI is not recommended for ZTA
    - hard to fully trust public infra
    - Better than nothing
        - Automate to improve
- Least privilege
- Dynamic trust
    - pools of trust, like VPN access are not great
![alt text](image-9.png)
    - Trust score challenges
        - can an attacker increase their score over time 
    - policy on the control plane to limit data access and bandwidth
    ![alt text](image-10.png)


## Chapter 03: Context Aware Agents
An Agent is a combination of data known about the actors in the request
- user
- device
- app

ZTA recognize the combo in the request

Some fields of the agent are available specifically to mitigate against active attack, and thus change quickly
Agent Data fields examples
- agent trust score
- user trust score
- user role or entitlements
- user groups
- user location
- user auth method
- device trust score
- device manufacture
- host Operating system
- hardware security module
- trusted platform module 
- device location
- IP Address

the agent is what is authz'ed in ZTA 
NOTE the agent is not for authentication; auth is prereq to agent authz
- If compromised, revoke authz first, then creds

Agents need to be fluid and rigid at the same time
- like a DB schema
- Standardize data format for an agent
    - Simple Network Mgmt protocol (SNMP)
![alt text](image-11.png)
- There is no OID equivalent for private IPs

Agent standardization is an implementation task
- JWT is common

## Chapter 04: Making Authorization Decisions
AuthZ is the most important ZTA process
ZTA Authz has 4 components
![alt text](image-12.png)
- enforcement
    - Front line
    ![alt text](image-13.png)
- policy engine
    - has the power to make the decision
    - has storage for the rules; must be version controlled
    - ZTA policy is not standardized
        - best practice is to define in terms of logical network components (services, device endpoint classes, user roles)
    - Typically JSON or YAML 
- trust engine
    - system that performs risk analysis against a particular request or action
    - What entities should be scored?
        - Network agents
        - Devices
- data stores
    - Used to make authz decisions, the source of truth for current and past states of the system
![alt text](image-14.png)

![alt text](image-15.png)
![alt text](image-16.png)
![alt text](image-17.png)

## Chapter 05: Trusting Devices
trusting devices is critical

Bootstrapping Trust
- golden images
- certify what software is running on the device

Generating and Securing Identity
- Signed certificates for the device
- HSM or TPM

automate the provisioning of a new device when possible
but with human is involved, use TOTP
![alt text](image-18.png)

Authenticating Control Plane devices
- X.509 is the standard
    - Note OU has be deprecated
    - Storing the private key can be a challenge
- TPMs
![alt text](image-19.png)
    - TPMs is good, but cumbersome and slow and cannot be used for TLS
    - Cannot be used for remote attestation
    - attack vectors
        - ROCA - calculated the endorsement key (EK) 
        - SIde-channel - physical attack to obtain EK by measuring the electrical characteristics of TPM
        - Fault injection

Inventory management
![alt text](image-20.png)

Knowing what to expect in a ZTA
- trusted entities can psh expectations into the system
- inventory Database helps
- servers are easy, clients are hard
    - client certs help

Secure Introduction of a new device is precarious
- 1st system is important
- what makes a good, secure intro system? 
    - Single user creds
    - short lived creds
    - 3rd party to enable separation of duty

Renewing and measuring device trust
- Local measurement
    - software measurement is less secure and less reliable, but unlimited
    - hardware measurement is better, but limited in capability
- Remote Measurement
    - better than local, b/c it enables separation of duties
- Unified endpoint Management
    - software based remote Mgmt
- continuous monitoring is critical

Software config Mgmt
- puppet, ansible, Chef, etc.
- helps manage change to devices
- focused on security of software running on devices
- Use CM based inventory
    - can be searchable
    - Enables secure source of truth

Using Device Data for User Authz
- Auth has happened successfully
- Trust Signals
    - time since image: over time, compromise increases
    - Historical access
    - Location
    - Network Comm Patterns
    - Machine Learning

## Chapter 06: Trusting Identities
user trust is not the same as device trust

Identity Authority
- informal identity: good only in small groups
- Authoritative identity: Enterprise

Bootstrapping ID in a private system
- Gov issued IDs
- In person is best, but remote can be done

Storing ID
- User directories
    - requires maintenance

When to Authenticate
- Avoid constant auth
- Auth for trust
    - use trust score to determine further auths
- Use multi channels
    - push notifications, 1 time codes, etc. 
- Cache the sessions

How to Auth ID? 
- something they know (password)
- something they have (Badge, TOTP)
- something they are (biometrics)
- behavioral (ML to analyze how they type)

SSO
- SAML
- OAuth
- OpenID Connect

See something, Say something
- be an active participant of the security of the organization

## Chapter 07: Trusting Applications
trusted device is a prereq to trusting code it will run

to establish trust
- people producing code are trusted
- secure coding practices are followed
- code is scanned for vulnerabilities
- trusted apps are properly designed
- trusted app are properly deployed
- continuous monitoring

Know the app pipeline
- dependencies, SBOMs
- NIST Secure software development Framework
![alt text](image-21.png)
- Secure the repo
- Audit trails
- Code reviews
- signed commits
- Reproducible Builds
- decouple release and artifact
- trusted the software distro network
- SAST and DAST
- Confidential computing
    - create a trusted execution environment
- COntinuos Improvement
- Continuous QA

## Chapter 08: Trusting Traffic
traditional network filtering still has a place in ZTA

Encryption vs Auth
- Encryption enables confidentially
- auth enables a receiver to validate the identity
- encryption is possible w/o auth, but bad practice. 
- important aspects
    - Secure key Management
    - forward secrecy: ensure the compromise of a single key doesn't compromise all comms
    - MFA
    - postquantum crypto
- Auth w/o Encryption? 
    - bad practice
    - use encryption every where

Bootstrapping trust
- first packet is hard b/c no truste
- mitigate w/ pre-auth
    - receiver is waiting on signed UDP packet
    - UDP doesn't expect a response
    - Single packet auth (SPA)
    - Firewall Knock Operator (fwknop)
        - OSS tool uses SPA and integrates w/ firewalls
        - Short lived exceptions created in firewall
        - SPA payload
            - 16 byte of random, local username, timestamp, fwknop version, SPA message types, access request, SPA Message digest
        - can use HMAC or other encryption

WHere should ZTA be in the network model? 
- TLS or IPsec


## Chapter 09: Realizing a Zero Trust Network

## Chapter 10: The Adversarial View

## Chapter 11: Zero Trust Architecture Sta

## Chapter 12: Challenges and the Road Ahead

