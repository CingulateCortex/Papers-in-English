# Threat Modelling

To begin proper threat modelling, you first collect background information about your application. Collecting background information is kind of essential thing for every kind of analysis such as penetration testing, threat modelling, political discussion, sociological discussion, criminal analysis, incident investigation etc. In that manner, this essential point is throughly so important. This background information can be used throughout the entire iterative threat modelling process.

There are four main sources of background information

1. **Specification:** Specifications include customer requirements, intended purposes and use cases. Specifications define the primary functionality of the system. You can use the specification to the list the features that may increase the attack surface of the system and to define mitigations to particular threats.
2. **Implementation Assumptions:** Implementation assumptions are the decisions made before code development or during architectural or project revisions. These assumptions capture the basic architectural and design assumptions that may raise security issues.
3. **External Dependencies:** An external dependency is a list of software components on which the system relies for proper functioning. External dependencies can be used to construct dependency contracts to capture third party security concerns. For example, in some cases, the assets of hosting environment may raise attack surface.
4. **Security Notes:** Include internal and external notes. These notes detail the hidden security concerns and steps taken against them. You can use these notes to capture the security assumptions from architectural point of view. These notes aid in defining mitigations for threats discovered during modelling.

## Decomposing the application

The second step of threat modelling is decomposing the application. In this phase, you define the main elements of a threat model. Decomposing provides a structured, formal approach to threat modelling, and is an effective exercise to understand the inner workings of the software being modelled. Decomposing the application helps you find threats during the discovery phase

* **Identifying Entry Points** 

To identify entry points, you need to find the sources of input to your application and list all the points which your system receives data from outside

Next, list all components that are receive hidden sources of input, such as components that interact with the file system, registry and memory. Finally, collect entry points by looking at the background information. Use cases or external dependencies reveal entry points for threat model.

For example, in an online store application, you may assume that the entry points are, front end web server, merchandise database, interface with a third party credit card processing system and interface with inventory system.

* **Identifying Assets**

To identify assets, you need to consider what the attacker will target. This phase is extremely important. Because you need to evaluate your assets maybe make some prioritisation in order to know which assets will be a critical target and required attention to protect.

Of course it is not an easy task. There are some cases that your asset is not that critical individually but is brutal in terms of the place where it is in interaction. So it is important to consider all the possibilities.

When evaluating threats, you will see that most threats relate to an attacker exploiting and stealing asset. While identifying assets, you might start encountering threats and record them for further use.

For example, in an online storing system, customer data, checkout cart, merchandise, inventory system and web application are main assets.

When you consider about customer data it may end up a mess. Because, protecting customer data is not always protecting the database you are storing these information. Sometimes you need to consider client side attack protection depends on your application or the criticality of the data being stored.

* **Identifying Roles**

Roles reflect the set of privileges included in your application. Roles usually translate to the types of users of the system. But can also refer to privilege levels without an associated role such as user mode versus kernel mode. Each entry point and asset has an associated list of roles. Recording the roles for each entry point or asset might reveal escalation of privilege or sensitive information disclosure threats.

Please note that, automated scanners does not capable to identify threats of logical flow in roles.

For example, in an online storing system, web customer, third party payment processing system, admin, power users, content creators etc are main roles.

## Building the Threat Profile

* **Identifying Threats**

Threats are negative impacts on an asset of interest to an attacker. Threats have the fallowing characteristics.

 * They are usually expressed as verbs 
 * They involve at leas one asset
 * They are written in fallowing format "Attacker verb to\from/with/etc asset for goal"

For example, continuing with the example of an online store application, some of the threats from the online storage activity matrix include

 * Attacker steals customer information
 * Attacker deletes information from the merchandise database
 * Attacker compromise the operating system or penetrate into internal network
 * etc.

* **Classifying Threats**

Threats are classified based on the STRIDE rule

For example,

    Attacker steal customer information -> Sensitive Information Disclosure

A threat categorization such as STRIDE is useful in the identification of threats by classifying attacker goals such as:

    Spoofing
    Tampering
    Repudiation
    Information Disclosure
    Denial of Service
    Elevation of Privilege.

A threat list of generic threats organized in these categories with examples and the affected security controls is provided in the following table:

|                                       |
|Type   |Example   |Security Control   |
|:---:|:---:|:---:|
|Spoofing   |Threat action aimed to illegally access and use another user's credentials, such as username and password.   |Authentication   |
|Tampering   |Threat action aimed to maliciously change/modify persistent data, such as persistent data in a database, and the alteration of data in transit between two computers over an open network, such as the Internet.   |Integrity   |
|Repudiation   |Threat action aimed to perform illegal operations in a system that lacks the ability to trace the prohibited operations.   |Non-Repudiation  |
|Information Disclosure   |Threat action to read a file that one was not granted access to, or to read data in transit.   |Confidentiality   |
|Denial of Service   |Threat aimed to deny access to valid users, such as by making a web server temporarily unavailable or unusable.   |Availability   |
|Elevation of Privilege   |Threat aimed to gain privileged access to resources for gaining unauthorized access to information or to compromise a system.   |Authorization   |

