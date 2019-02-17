## Week 5 - Network Security           
### Introduction
This week's material focuses on topic of Network Security. It discusses various types of security threats 
and defenses against them. 

### Why Do We Need Network Security?
It seems like an obvious question but here a couple reasons
*	Help Host-based protections
    *	Keep dangerous hosts/data out  / Create a safe space 
    *	Prevent exfiltration of critical data
*	Threats come in from the network, companies need to defend themselves against them
    *	DDoS and atttacks from network in (e.g., Stack overflow, Morris Worm)
*	Keep threats out ON the network: Worms, Botnets, and misc  

#### Network-based Protection Stategies
*	Positive policy (whitelists)
*	Firewalls / Security Zones (blacklists)
*	Defense in Depth (layered-defense) – if any layer fails, the other layers might not allow threat to pass through
*	Intrusion Detection 
*	Honeynets / Intrusion Deception
*	Quarantine
*	Reputation (also host-based)

#### Robustness principle
At every layer of the protocols, there is a general rule whose application can lead to enormous benefits in robustness and interopability.
*   Be liberal in what you accept, and conservative in what you send.
*   Host software should be prepared to survive other mis-behaving hosts

This principle applies to many well-known protocols like TCP/IP, etc. It is still relevant today, I think, if one wants to create a robust protocol that doesn't rely
on hosts transmitting data with perfect compliance to protocol. It's difficult to anticipate all combinations of packets that can be received but the protocol can still
choose to ignore some invalid packet structures without choking on the packet.

### Network Security Threats
In this section, we'll focus on discussing major types of security threats
and how we can deal with them in order to protect networks.

#### Man in the Middle (MITM)
***MITM*** -  A <=> B and M is in the middle, intercepting and (possibly) changing messages

***Blackhat MITM Examples***
*	ARP poisoning - Flood network with ARP responses
*	TCP hijacking - inject, Delete or change data into a TCP stream 

#### Hidden Data Transmissions
*   Covert Channels
    *	Leverages channels to transmit information that weren’t intended to do so.
*	Legitimate Channel Misuse
    *	Payload tunneling:	HTTP CONNECT Tunneling, TCP over UDP
    *	Overlapping IP segments and Data at end of datagram or file

#### Reconnaisance
***Active***

*	Attacker wants to attack vulnerable machines on a network
*	Attacker needs to find addresses for services that can be attacked

***Passive***
*	Attacker is able to see data on the network (wiring closet, ISP)
*	Attacker wants to learn about people

#### Resource Consumption Attacks (DOS)
***Types of DOS***
*	Network exhaustion: Flooding the network so that the service is unreachable or is reachable with such high latency that it is useless
*	CPU exhaustion: Make CPU so busy, legitimate traffic cannot be served. 
*	Memory exhaustion: Cause server to run out of memory and slow down/crash
*	Storage exhaustion: Cause server to run out of disk space 
*	Application vulnerability exploitation: making the application unavailable by crashing it or the OS.
*	Other finite resources: sockets, TCP listen queue, connection pool, etc

### Defenses
After discussing some of the major network threats, next is how we can defend
against them.
*   Packet Filtering
    *	Basic first step toward protecting your network
    *	Policy driven whitelisting to allow only expected traffic to cross network boundary
*   Proxying
    *	MITM: Terminate TCP connections and establish new ones
    *	Inspect and sometimes modify application data to prevent attacks
    *	Provide nuanced and granular access control based on application specific information.
*   NextGen Firewalls(NGFW) - use stronger links between endpoints and firewalls to identify threat source
*   NIPS(Network Intrustion Prevent System) - evaluates packet data against known and unknown attacks


[Go Home](../index.md) 
