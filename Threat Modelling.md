To begin proper threat modelling, you first collect background information about your application. Collecting background information is kind of essential thing for every kind of analysis such as penetration testing, threat modelling, political discussion, sociological discussion, criminal analysis, incident investigation etc. In that manner, this essential point is throughly so important. This background information can be used throughout the entire iterative threat modelling process.

There are four main sources of background information

1. Specification: Specifications include customer requirements, intended purposes and use cases. Specifications define the primary functionality of the system. You can use the specification to the list the features that may increase the attack surface of the system and to define mitigations to particular threats.
2. Implementation Assumptions: Implementation assumptions are the decisions made before code development or during architectural or project revisions. These assumptions capture the basic architectural and design assumptions that may raise security issues.
3. External Dependencies: An external dependency is a list of software components on which the system relies for proper functioning. External dependencies can be used to construct dependency contracts to capture third party security concerns. For example, in some cases, the assets of hosting environment may raise attack surface.
4. Security Notes: Include internal and external notes. These notes detail the hidden security concerns and steps taken against them. You can use these notes to capture the security assumptions from architectural point of view. These notes aid in defining mitigations for threats discovered during modelling.

## Decomposing the application