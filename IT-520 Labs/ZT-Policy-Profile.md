**Lab 03: Zero Trust Policy Profile**

**1. ZTA Component Definitions**
	1. Policy Engine (PE): A policy engine is a software program which makes decisions about security scenarios which have been set by the policy administrator. In the brain/rule setter/gatekeeper analogy, the PE is the brain, as it is the one making the decisions, not creating or enforcing them. They receive the input in the form of requests for access and determine the outcome (access granted or denied) based on the rules set by the PA. Examples of PEs include some firewalls, API gateways, and many identity and access systems. 
	2. Policy Administrator (PA): A PA is the rule setter, in that it is the vehicles through which security architects implement their rules for who can access what in the network. It is the device or software that stores policies for access, but does not make decisions (the job of the PE) or physically enforce them (the job of the PEP). A PA could be a firewall, wherein the sysadmin sets white lists for remote access, open ports on routers and switches, and which devices can communicate with each other. Firewalls are interesting in that they actually can fulfill all three roles, but do not have to. Another example of a PA could be an Identity and Access Management system (IAM), such as Active Directory. These are used to store security policies, such as what individuals or groups have access to which folders and devices in the network.
	3. Policy Enforcement Point (PEP): A policy enforcement point is where the decision regarding rules is physically enforced, which makes it the gatekeeper. The rules are stored in the PA, which the PE references when making rulings on whether to grant access, and the PEP enforces that ruling. In a legal analogy, the PE is the law, the PA is the judge, and the PEP are law enforcement. An example of a PEP could also be a firewall, which automatically enforces rules for network traffic stored within itself. I.e. an external TCP connection over port 80 is attempted, but the firewall rules have closed port 80 from the outside, and does not respond with the remainder of the TCP handshake.

**2. Core Principle Application**
	-The Policy Engine enforces the principle of "use least privilege" by checking with the PA's policies when a user attempts to access any resources. In the example of the water treatment facility, the PA likely has policies and rules that allow only users in an IAM's HR group to access HR data. For example, the PE could be something like Open Policy Agent (OPA), which can reference lightweight directory access protocol (LDAP) or active directory (AD) rules/policies/groups to check whether a user belongs to the HR group, and rules whether they are allowed to access the water treatment facility's HR data. Anyone not falling into that group would be denied access by the PE, as they do not have sufficient privilege, and thus prevents unauthorized access to personally identifiable information (PII).

**3. Simplified Policy Table**

|Policy Requirement|Condition to be Met by User|Action if Condition is Met|
|------------------|---------------------------|--------------------------|
|User Identity|User belongs to HR group in IAM|Grant Access|
|Device Posture|Device operating system has latest security patch|Grant Access|
|Network Context|User must be connected by VPN from white-listed IP address|Grant Access|


---
# Git Repository Metadata
Project: Lab 03 - Zero Trust Policy
Filename: ZT-Policy-Profile.md
Commit Message: Submitted Lab 03: Zero Trust Policy Profile
Due Date: March 02, 2026
---
