
#ZBI Phases Versus Features
|Phase			| Area 				|Attribute / Feature						|
|-----------------------|-------------------------------|---------------------------------------------------------------|
|POC1			| Phase Definition		| Experimental / Iterative base starting from zero		|
|POC2			| Phase Definition		| POC Exit with definitive froof of capability for next phase	|
|Embeded Service	| Phase Definition		| ZBI within one consumer POD (e.g. Omnia) and is not leveraged	|
|Leveraged Service	| Phase Definition		| ZBI within its own POD(s) serviving more than one consumer	|
|POC1			| Access Network		| In POC Network with 1 VLAN per Tin 				|
|POC2			| Access Network		| In POC Network with several down selected potential VLANs per Tin with some context specialisation e.g. Tin#1 in VLAN1 for Type1 workload vs Tin# in VLAN2 for Type2 workload|
|Embeded Service	| Access Network		| In POD Network with several VLANs per Tin with required level of context specialisation	|
|Leveraged Service	| Access Network		| In ZBI's own POD Network serving more than one consumer with suitable context specialisatin	|
|POC1			| Access Network Segregation	| None first then later 1 VLAN per Tin (Different Tins having different VLANs). Very basic. |
|POC2			| Access Network Segregation	| Segregation by Server Role (which already includes Zone) quite possibly requiring coordinated segregation of disk storage. A two tier control is proposed. Switch-port profile controls which subset of VLANs a Tin MIGHT become (via host level VLAN tagging). Tin instantiation time decides which VLAN (one only) the TIN is tagged into. (Another less likely idea is to see if it is pragmatic to have multiple VLANs in the Tin and fiddle intensively with virtual adapters and static routes and expose only one VLAN at Container level. This is assuming the full power of programming can be applied at both Tin and Container instantiation times. But this is quite likely to be difficult for forensics/debugging. Possibly a throw-away.) Options of bridging and virtualisation at container level should be investigated further. However again if complexity becomes too high, security/network peer-review would become difficult. |
|Embeded Service	| Access Network Segregation	| Same as POC2	with opportunistic simplification e.g. skipping server role where sensitivity is lower				|
|Leveraged Service	| Access Network Segregation	| Same as POC2 but much less likely to relax any available means of segregation because of multiple consumers	|
|POC1			| Server Role Support		| Initially not required					|
|POC2			| Server Role Support		| Fully demonstrated/validated capability to support Server Role (Server Tier + Environment + Site in the Security Zone of the Server Tier)	|
|Embeded Service	| Server Role Support		| Same as POC2, with some possibility of simplification especially if (and only if) sensitivity is not a concern|
|Leveraged Service	| Server Role Support		| Same as POC2 and strictly enforced				|
|POC1			| Disk Storage Services		| Epmemeral Storage 						|
|POC2			| Disk Storage Services		| Epmemeral Storage plus persistent storage with segregation duly demonstrated. This may have to be in tandem with Network Segregation.	|
|Embeded Service	| Disk Storage Services		| Epmemeral Storage plus persistent storage with proper segregation, which is very likely to be linked with network segregation	|
|Leveraged Service	| Disk Storage Services		| Epmemeral Storage plus persistent storage with proper segregation, which is very likely to be linked with network segregation	|
|POC1			| Storage Back-up Service	| None first then incrementally being built	|
|POC2			| Storage Back-up Service	| Unresolved yet. How will this be done??? Capabiliy of Back-up and restoration of persistent storage on elective basis (not wholesale). Back-up Client, back-up server side onboarding. Long term corelation of which back-up belongs to which ZBI workload.... Big topic to be explored	|
|Embeded Service	| Storage Back-up Service	| Same as POC2 							|
|Leveraged Service	| Storage Back-up Service	| Same as POC2							|
|POC1			| VLAN/subnet/switch port profile	| Manually predefined 					|
|POC2			| VLAN/subnet/switch port profile	| Control Pane defined Via API to Switch.					|
|Embeded Service	| VLAN/subnet/switch port profile	| Manually predefined (customer PODs unlikely to yield control)		|
|Leveraged Service	| VLAN/subnet/switch port profile	| Fully Control Pane defined				|
|POC1			| POD Firewall			| 10 DFA Firewall (Manually predefined to protect the Bank. Untouchable by POC	|
|POC2			| POD Firewall			| unresolved yet. 10 DFA Firewall (Manually predefined to protect the Bank. FW POC details to be discussed with Jon Whitear and likely require separate exercise.	|
|Embeded Service	| POD Firewall			| Customer POD Firewall (e.g. Omnia FW) with manually predefined rules (customer PODs unlikely to yield control because firewall is often in itselv a leveraged service	|
|Leveraged Service	| POD Firewall			| ZBI POD's own Firewall with Control Pane defined firewall rules (if and only if the firewall is dedicated/autonomous).Big topic!		|
|POC1			| ZSS Firewall			| To be devised. The potential inefficiency of switch based ACL should be highlighted as a potential concern. Alternatives like host based firewall or a proper stateful firewall should also be evaluated. Big topic!|
|POC2			| ZSS Firewall			| Same as POC1 but fully demonstrated/validated			|
|Embeded Service	| ZSS Firewall			| Case by Case adaptation to POD configuration of each Internal customer. May sometimes needs retrofit (based on a ZBI standard pattern/equipment list)	|
|Leveraged Service	| ZSS Firewall			| Unresolved yet. ZBI central control with a future solution.	|
|POC1			| The Other Side Firewall rules	| No need to demonstrate					|
|POC2			| The Other Side Firewall rules	| No need to demonstrate					|
|Embeded Service	| The Other Side Firewall rules	| Changes done outside ZBI in legacy world			|
|Leveraged Service	| The Other Side Firewall rules	| Changes done outside ZBI in legacy world			|
|POC1			| Network Switch		| Switch to be chosen for compatibility with intended cloud provisioning features |
|POC2			| Network Switch		| Full ZBI required features to be demonstrated		|
|Embeded Service	| Network Switch		| Case by Case adaptation to POD configuration of each Internal customer. May sometimes need retrofit (based on a ZBI standard pattern/equipment list)	|
|Leveraged Service	| Network Switch		| ZBI choice within ZBI POD					|
|POC1			| TCPIP Version			| V4 only. Explicitly disable all V6 		 		|
|POC2			| TCPIP Version			| V4 only. Explicitly disable all V6 		 		|
|Embeded Service	| TCPIP Version			| V4 only. Explicitly disable all V6 		 		|
|Leveraged Service	| TCPIP Version			| V4 only. Explicitly disable all V6 		 		|
|POC1			| Consumable Tin		| Ironic instantiated (basic)					|
|POC2			| Consumable Tin		| Dynamic Tin reallocation with role specific specialisation (at Ironic or upper layer images)	|
|Embeded Service	| Consumable Tin		| Same as POC2							|
|Leveraged Service	| Consumable Tin		| Unresolved yet. ZBI POD itself may have some smarts for alters to humans or semi-auto or auto Tin reallocation	|
|POC1			| Control Pane 			| Firstly hand built then increasingly complies to End State (Inputs required???). Initially minimal security/audit/lock down	|
|POC2			| Control Pane			| End State features demonstrated/validated including security/audit/lock down							|
|Embeded Service	| Control Pane			| End State (with investigation on possibility of ONE centralised Control Pane for different Embeded Service Consumers) 	|	
|Leveraged Service	| Control Pane			| Inside ZBI POD. It may or may not (future decision) ALSO controll other Embedded Server Clients 	|
|POC1			| Compute service		| Basic Mesos cluster ephemeral container service on Tin and the whole thing incrementally being built	|
|POC2			| Compute service		| Full Mesos cluster features on dynamically reallocatable Tin service for both ephemeral and persistent (storage) demo workloads. Hadoop support also demonstrated	|
|Embeded Service	| Compute service		| Same as POC2							|
|Leveraged Service	| Compute service		| Same as POC2 but Hadoop workload should only be small because huge ones should be embeded (Ephemeral huge demands may cause either stability/financial concerns)	|
|POC1			| Dynamic Scale-up/down (Tin)	| Incremental experimentation.					|
|POC2			| Dynamic Scale-up/down (Tin)	| Fully demonstrated of API/Administrator capability to add/remove Tin when requested. No automatic self-decisioning 	|
|Embeded Service	| Dynamic Scale-up/down (Tin)	| Same as POC2 							|
|Leveraged Service	| Dynamic Scale-up/down (Tin)	| Load sensing and (semi-) auto dynamic capacity shifting may be investigated in the longer future	|
|POC1			| Dynamic Scale-up/down (SW)	| None.								|
|POC2			| Dynamic Scale-up/down (SW)	| Software instances level dynamic scale up/down is consumer responsility. ZBI povides only the API|
|Embeded Service	| Dynamic Scale-up/down (SW)	| Software instances level dynamic scale up/down is consumer responsility. ZBI povides only the API|
|Leveraged Service	| Dynamic Scale-up/down (SW)	| Software instances level dynamic scale up/down is consumer responsility. ZBI povides only the API|
|POC1			| Consumer Security		| Unresolved. From none to AUT01 based Kerberos and LDAP with the whole incrementally being completed. For run and for admin/API. (Big topic!)	|
|POC2			| Consumer Security		| Unresolved. Fully demonstrated capabilities			|
|Embeded Service	| Consumer Security		| Unresolved. Same as POC2 but may have to be tailored for individual internal customers (More thoughts are required!) |								|
|Leveraged Service	| Consumer Security		| Unresolved. Same as POC2 and should accommodate for more likely use case patterns across different internal customers (More thoughts are required)	|
|POC1			| Core Security			| Unresolved. None								|
|POC2			| Core Security			| Unresolved. Autidability / DLP / Encryption / HSMs / KMP / integrity management / configuration lock down or assurance 	|
|Embeded Service	| Core Security			| Unresolved. Autidability / DLP / Encryption / HSMs / KMP / integrity management / configuration lock down or assurance 	|
|Leveraged Service	| Core Security			| Unresolved. Autidability / DLP / Encryption / HSMs / KMP / integrity management / configuration lock down or assurance 	|
|POC1			| Network Services Consumed	| A block of IP address requested in IPNet for POC. NTP, Active Directory, some DNS entries, forwarders, delegations from CBA Internet network. Do we need outbound Internet access?	|
|POC2			| Network Services Consumed	| Same as POC1							|
|Embeded Service	| Network Services Consumed	| IP Address Block from Customer POD. All other services are likely to vary to some degree for each the consumer)	|
|Leveraged Service	| Network Services Consumed	| Will be based on ZBI centric requirements			|
|POC1			| Network Services Provided	| Unresolved. Incrementally built: Load balancing, Service Discovery, DNS, Proxying, SSL termination/offloading, cross site fail-over (emulated with 1 site) 	|
|POC2			| Network Services Provided	| Unresolved. Full list as POC1 fully demonstrated/validated		|
|Embeded Service	| Network Services Provided	| Unresolved. Customer specific, chosen from a ZBI standard check-list	|
|Leveraged Service	| Network Services Provided	| Unresolved. Will be based on ZBI defined service definitions		|
|POC1			| Security Compliance		| Protection of the Bank's Networks from the POC. No sensitive data.	|
|POC2			| Security Compliance		| Compliance Scans of images (not instances)=> Demo of when/how to triger it. SIEM, DLP (???), security fix (demo pipeline), Security hardenning of host and network, no anti-virus for Linux, provision of suitable security features like encryption and secret key management	|
|Embeded Service	| Security Compliance		| Same as POC2 but for real					|
|Leveraged Service	| Security Compliance		| Will be based on ZBI centric requirements			|
|POC1			| DR of Persistent disk Storage	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|POC2			| DR of Persistent disk Storage	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|Embeded Service	| DR of Persistent disk Storage	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|Leveraged Service	| DR of Persistent disk Storage	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|POC1			| DR of processing tiers	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|POC2			| DR of processing tiers	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|Embeded Service	| DR of processing tiers	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|Leveraged Service	| DR of processing tiers	| Upfront specified as responsibility of application layer under POD model and not by ZBI	|
|POC1			| DR site jump (inbound flows)	| None								|
|POC2			| DR site jump (inbound flows)	| Unresolved. If network services include suitable DNS based facilities, demo in same site in the POC	|							|
|Embeded Service	| DR site jump (inbound flows)	| Unresolved. If network services include suitable DNS based facilities, yes|
|Leveraged Service	| DR site jump (inbound flows)	| Unresolved. Mandatory unless this is explicitly delegated to components outside the ZBI POD	|							|
|POC1			| Stretched VLANs		| None and never under POD model				|
|POC2			| Stretched VLANs		| None and never under POD model				|
|Embeded Service	| Stretched VLANs		| None and never under POD model				|
|Leveraged Service	| Stretched VLANs		| None and never under POD model				|
|POC1			| Cross Site Networking		| None								|
|POC2			| Cross Site Networking		| Unresolved							|
|Embeded Service	| Cross Site Networking		| Unresolved							|
|Leveraged Service	| Cross Site Networking		| Unresolved							|
|POC1			| Disk storage Encryption at rest	| None							|
|POC2			| Disk storage Encryption at rest	| Unresolved						|
|Embeded Service	| Disk storage Encryption at rest	| Unresolved						|
|Leveraged Service	| Disk storage Encryption at rest	| Unresolved						|
|POC1			| Monitoring			| None								|
|POC2			| Monitoring			| Unresolved							|
|Embeded Service	| Monitoring			| Unresolved							|
|Leveraged Service	| Monitoring			| Unresolved							|
|POC1			| CI/CD Tooling			| Gradual build							|
|POC2			| CI/CD Tooling			| Fully functional demo.					|
|Embeded Service	| CI/CD Tooling			| Unresolved. One per consumer or fully leveraged?		|
|Leveraged Service	| CI/CD Tooling			| Unresolved. Does it also serve Embeded consumers?		|



