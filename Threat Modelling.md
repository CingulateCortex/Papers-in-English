# Threat Modelling

To begin proper threat modelling, you first collect background information about your application. Collecting background information is kind of essential thing for every kind of analysis such as penetration testing, threat modelling, political discussion, sociological discussion, criminal analysis, incident investigation etc. In that manner, this essential point is throughly so important. This background information can be used throughout the entire iterative threat modelling process.

There are four main sources of background information

1. **Specification:** Specifications include customer requirements, intended purposes and use cases. Specifications define the primary functionality of the system. You can use the specification to the list the features that may increase the attack surface of the system and to define mitigations to particular threats.
2. **Implementation Assumptions:** Implementation assumptions are the decisions made before code development or during architectural or project revisions. These assumptions capture the basic architectural and design assumptions that may raise security issues.
3. **External Dependencies:** An external dependency is a list of software components on which the system relies for proper functioning. External dependencies can be used to construct dependency contracts to capture third party security concerns. For example, in some cases, the assets of hosting environment may raise attack surface.
4. **Security Notes:** Include internal and external notes. These notes detail the hidden security concerns and steps taken against them. You can use these notes to capture the security assumptions from architectural point of view. These notes aid in defining mitigations for threats discovered during modelling.

## Decomposing the application

The second step of threat modelling is decomposing the application. In this phase, you define the main elements of a threat model. Decomposing provides a structured, formal approach to threat modelling, and is an effective exercise to understand the inner workings of the software being modelled. Decomposing the application helps you find threats during the discovery phase

* **Identifying Entry Points** *

To identify entry points, you need to find the sources of input to your application and list all the points which your system receives data from outside

Next, list all components that are receive hidden sources of input, such as components that interact with the file system, registry and memory. Finally, collect entry points by looking at the background information. Use cases or external dependencies reveal entry points for threat model.

For example, in an online store application, you may assume that the entry points are, front end web server, merchandise database, interface with a third party credit card processing system and interface with inventory system.

