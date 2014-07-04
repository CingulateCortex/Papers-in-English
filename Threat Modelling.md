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


|Type   |Example   |Security Control   |
|:---:|:---:|:---:|
|Spoofing   |Threat action aimed to illegally access and use another user's credentials, such as username and password.   |Authentication   |
|Tampering   |Threat action aimed to maliciously change/modify persistent data, such as persistent data in a database, and the alteration of data in transit between two computers over an open network, such as the Internet.   |Integrity   |
|Repudiation   |Threat action aimed to perform illegal operations in a system that lacks the ability to trace the prohibited operations.   |Non-Repudiation  |
|Information Disclosure   |Threat action to read a file that one was not granted access to, or to read data in transit.   |Confidentiality   |
|Denial of Service   |Threat aimed to deny access to valid users, such as by making a web server temporarily unavailable or unusable.   |Availability   |
|Elevation of Privilege   |Threat aimed to gain privileged access to resources for gaining unauthorized access to information or to compromise a system.   |Authorization   |


* **Building Threat Trees**

The root node is the threat and child nodes are the conditions necessary for the threat to be realized. Threat trees are used during penetration testing to construct test cases from the condition nodes.  Below chart a simple example for a threat tree

![alt text](http://cingulatecortex.com/wp-content/uploads/2013/11/Screen-Shot-2013-11-10-at-14.44.35.png "Title")

* **Identifying Vulnerabilities**

Threat and conditions can be mitigated or unmitigated. Attack paths can be built by identifying unmitigated routes from the leaf conditions to the root threat. Unmitigated attack paths yield vulnerabilities, which inherit the root threats STRIDE classifications.

For example. consider the vulnerability from the previous example of the online store threat three. Here, the SQL injection vulnerability in the query fields allows an attacker to obtain access to an account without proper credentials. This vulnerability can be classified as sensitive information disclosure.

The fifth and final step in threat modelling is analyzing the risks. In application, vulnerabilties give rise to risks, and the more serious vulnerability the higher risk you have. You can asses a vulnerability by using DREAD ratings. For ever vulnerability, a rating between zero and ten is assigned for each of the DREAD categories.

Dread stands for Damage, Reproducibility, Exploitability, Affected Users and Discoverability.

####Applying Threat Modelling

    Describe the application using diagrams
    Identify the threat types by using STRIDE
    Identify appropriate mitigation techniques
    Recognize the role of the threat model documents
    Identify the tools that help with threat modelling

####Important Questions for Applying Threat Modelling

    What security guarantees will be made to end users?
    What security expectations will end users have?
    In what environments do you expect the release product to be used?
    Who will be using it?
    How do you expect the final product to be used?
    Can you think of any ways the product might be abused?
    What id one those users intended harm?
    What damage might such an adversary be able to cause?
    What design level mitigations might work for your product?
    What feature level mitigations might work for your product?


* **Components of a Diagram**

Processes: are shown by a circle and the list is given below includes processes

    DLLs
    EXEs
    COM Objects
    Components
    Services
    Web Services
    Assemblies
    Etc.

Data Flows: Arrows represents the data flows such as function call, network traffic, RPC, etc.

Data Stores: Horizontal Bars represent the data stores such as Database, Files, Registries, Queues, Stacks, etc.

External Entities: Rectangular represents external entities such as people, other systems, data feeds, events, notifications, etc

Trust Boundary: Trust Boundaries are logical separations for elements that are at different trust levels, or are mutually distrustful. They are key to a threat model since they help identify points of attacks. Everything on the attack surface is a trust boundary; however trust boundaries can exist within the attack surface since no filter could possibly validate all data for all possible uses.

* **Sample Diagram**

![alt_text](http://cingulatecortex.com/wp-content/uploads/2013/11/Screen-Shot-2013-11-10-at-15.50.16.png " ")

* **Key Points for Diagram**
 * Diagram should not be as detailed as a flowchart, class diagram or call graph
 * Each diagram should contain at least one trust boundary. Otherwise why are drawing it?
 * Are items in the diagram numbered? If not it is easy to miss some as you transfer data to other documents
 * Does data flow magically between databases? There needs to be a process between them
 * Does data magically appear? Data originates from external actors, not from data stores
 * Are there data sinks? Data is placed in a data store for a reason. Either data used by external actors or it is wasting disk space
 * Are all elements on the diagram clearly labeled?
 * Are any data flow labeled with generic terms such as read, write or query? if so give them a more descriptive name
 
