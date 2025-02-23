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

## Chapter 04: Making Authorization Decisions

## Chapter 05: Trusting Devices

## Chapter 06: Trusting Identities

## Chapter 07: Trusting Applications

## Chapter 08: Trusting Traffic

## Chapter 09: Realizing a Zero Trust Network

## Chapter 10: The Adversarial View

## Chapter 11: Zero Trust Architecture Sta

## Chapter 12: Challenges and the Road Ahead

