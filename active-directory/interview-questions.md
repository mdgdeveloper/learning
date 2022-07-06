
# Interview Questions v1
**1. What do you mean by Active Directory?**

An active directory is an index structure used on Microsoft Windows-based servers and computers to stock up data and information about domains and networks.

**2. Name the default protocol used in directory services?**

The non-payment protocol utilized in directory services is LDAP (Lightweight Directory Access Protocol).

**3. Define SYSVOL?**

The SysVOL file keeps the server’s copy of the domain’s public files.  The fillings such as users, group policy, etc. of the SysVOL folders are simulated to all area controllers in the domain.

**4. Define the term FOREST in AD?**

Forest is used to describing a congregation of AD domains that split a separate schema for the AD.  All DC’s in the forest share this plan and is practical in a hierarchical fashion among them.

**5. What is Kerberos?**

Kerberos is a verification protocol for the network.  It is built to present secure verification for client applications by using secret-key cryptography.

**6. What do you mean by lingering objects?**

Lingering objects can exist if a field controller does not duplicate for a gap of time that is longer than the gravestone lifetime.

**7. Define Active Directory Schema?**

Schema is a lively directory constituent describes all the objects and attributes that the directory service uses to amass data.

**8. Name the components of AD?**

The components of AD are:

• Physical Structures: Domain controller and Sites

• Logical Structure: Trees, Forest, Domains and OU

**9. Define Infrastructure Master?**

Infrastructure Master is answerable for updating information about the customer and group and universal catalogue.

**10. Define the domain?**

A domain is a place of network resources for a collection of users. The user needs only to log in to the domain to increase access to the resources, which may be situated on a number of several servers in the network.

**11. Explain subnet?**

In computer networks based upon the Internet Protocol Suite, a subnetwork is a piece of the network’s computers and network campaign that have a widespread elected IP address routing prefix.

**12. What do you mean by organizational units?**

The Organizational Unit is a serious design factor impacting policy, security, competence and the charge of administration. Organizational Units are a kind of LDAP (X.500) pot. It can be a reflection of as a sub-domain element with comparable properties to domains.

**13. What do you mean by Active Directory Recycle Bin?**

Active Directory Recycle bin is a characteristic of Windows Server 2008 AD. It helps to re-establish by chance deleted Active Directory objects without using a backed-up AD database, rebooting area controller.

**14. Tell me the purpose of replication in AD?**

The reason for replication is to share out the data stored within the index throughout the organization for amplified availability, performance, and data defense. Systems administrators can tune duplication to occur based on their physical network communications and other constraints.

**15. Define Mixed Mode?**

Allows domain controllers operation both Windows 2000 and previous versions of Windows NT to co-exist in the area. In mixed mode, the domain features from preceding versions of Windows NT Server are still enabled, while some Windows 2000 features are disabled. Windows 2000 Server domains are installed in mixed mode by non-payment.  In a mixed way, the field may have Windows NT 4.0 backup domain controllers at hand.

**16. Explain stale?**

Stale refers to references to objects that have been stimulated so that the local copy of the distant object's name is out of date.

**17. Define SID?**

Security Identifier is an exceptional variable-length identifier used to recognize a trustee or refuge principal.

**18. Do we use clustering in Active Directory? Why?**

No one installs Active Directory in a bunch. There is no need for clustering a field controller.  Active Directory provides total joblessness with two or more servers.

**19. What is RID Master?**

RID master refers for Relative Identifier for conveying exceptional IDs to the object shaped in AD.

**20. What is child DC?**

Child DC is a sub-area controller under the root domain controller which share a namespace.

**21. What is the port no of Kerbrose?**

The port no is 88

**22. What is the port number of Global catalog?**

The port number of the global catalog is 3268

**23. Tell me the port no of LDAP?**

The port no of LDAP is 389

**24. If I try to look schema, how can I do that?**

List schmmgmt.dll using this command:

c:\windows\system32>regsvr32 schmmgmt.dll

Open mmc --> add snapin --> add Active directory schema

name it as schema.msc

Open administrative tool --> schema.msc

**25. Define Native Mode?**

When all domain controllers in a given area are consecutively Windows 2000 Server, this way permits organizations to take the lead of new Active Directory features such as worldwide groups, inter-domain group membership and nested group membership.
