# The Path to Becoming a Software Architect

## Sources
- https://medium.com/@nvashanin/the-path-to-becoming-a-software-architect-de53f1cb310a
- https://medium.com/@nvashanin/types-of-software-architects-aa03e359d192

## Definition
A software architect is a software expert who makes high-level design choices and dictates technical standards, including software coding standards, tools, and platforms. The leading expert is referred to as the chief architect. [Wiki](https://en.wikipedia.org/wiki/Software\_architect)

## Skills
- Communicability
- Broad and deep technical knowledge
- Responsibility
- Stress resistance
- Management skills
- Analytic skills
- Responsible for everything

## Some tasks
- Identifying the stakeholders on the project
- Identifying business requirements and requirements of the stakeholders on the project
- Designing the entire system based on the received requirements
- Choosing the system architecture and each component of this system at high level
- Choosing the technologies for the implementation of each component and connections between the parts
- Architectural review
- Code review
- Writing project documentation and support it
- Creating unified development standards in the company
- Controlling the architecture during the next iteration of the system release
- Full technical support of the project

## Deal with stakeholders
> The code itself, no matter how ideal it is, is not worth a penny. What matters is the business functionality that this code implements.

> A stakeholder is a person or organization that has rights, shares, claims, or interests concerning the system or its properties meeting their needs and expectations.

> In software development, it’s worth focusing not on end users, but entirely on stakeholders.

—> The last part may be true for financial success in the industry, but this is not the way of the [[2021-02-23-the-software-craftsman | Software Craftsman]].

### Stakeholder types
- Involved in the project and work on it
	- Project team
	- Management team
	- Third-party companies
	- Supporting team
- Affected by the project and use it and its artifacts
	- Customers
	- Heads and employees of functional units
	- End users
- Not involved in the project, but position allows to influence it
	- Top-managers of the company
	- Owners of the company
	- Shareholders and creditors
	- Regulatory structures

### Theory of stakeholder management
0. Identify stakeholders
0. Identify stakeholders requirements
0. Analyze stakeholders influence and importance
0. Working plan for control stakeholders
0. Plan integration
0. Analyze results

### Identifying all stakeholders
Questions helping identification:
- Whose actions can result in failing to meet the project goals ?
- Who has the most interest in developing this project ?
- Was there a project like this before ? If so, was it successful ?
- Is it necessary for all departments to participate in this project ?
- What issues need to be solved during the project ?
- Who knows this data better than everyone else, and can design it independently ?

The benefits:
- Identifying the interests of stakeholders
- Identifying the potential difficulties
- Identifying the key persons to inform
- Identifying the groups of people to involve
- Evaluating the means, rules and principles of communication
- Planning actions to reduce negative impact

## Types of architects
### System architect
- Affects one system and builds connections within it
- Focuses on the technical component of the development
- Helps the project manager to make management decisions
- Has a deep knowledge of the technologies

### Solution architect
- Participates in discussions of business
- Creates connections between several systems
- Provides communication between several systems
- Designs connections between systems
- Codes independently only solution prototypes
- Acts as a universal soldier of business and technology

### Enterprise architect
- Affects all development of the company
- Works with high-level abstractions of the created systems
- Provides technical communications throughout the company
- Does not interact with the code
- Focuses on the business component
- Has a broad technological horizon
- Owns several domains

\--> Domain architect

  

  

  

« The goal of the architect’s career development is the formation of the ‘m’ — multiplatform & multi domain specialist. »

  

  

Quality attributes / non-functional requirements in Software Architecture

  

- Performance

- Interoperability

- Usability

- Reliability

- Availability

- Security

- Maintainability

- Modifiability

- Testability

- Scalability

- Reusability

- Supportability

  

Documentation in Software Architecture

  

Goals

- Knowledge sharing

- Communication

- Analyses

  

Formula whether the documentation is worth the effort:

  

(Cx — Cy) > Cdiff

where

Cx = The cost of the project without documentation,

Cy = The cost of the project with the documentation,

Cdiff = The cost of maintaining documentation.

  

Types of diagrams

  

- Informal: the most common but needs detailed description for understanding

- Semiformal: UML, C4, architectural view model

- Formal: architecture analysis design language

  

Tips for writing documentation

  

- Avoid repetition

- Recognize for whom you are writing

- Avoid ambiguity

- Maintain relevance

- Review documentation

  

Books in Software Architecture

  

Software Architecture in Practice (3rd Edition) (SEI Series in Software Engineering)

by Len Bass, Paul Clements, Rick Kazman

  

Domain-Driven Design: Tackling Complexity in the Heart of Software

By Eric Evans

  

Stakeholder Theory: The State of the Art

by R. Edward Freeman, Jeffrey S. Harrison, Andrew C. Wicks, Bidhan L. Parmar, Simone de Colle

  

Software Estimation: Demystifying the Black Art

by Steve McConnell

  

System Design Cheat Sheet

  

1\. Understand Problem and Scope

- Recognize stakeholders and prioritize them. Create a RACI matrix

- Understand business drivers of the project

- Recognize end-users of the project and understand how they use that system

- Check functional requirements

- Define external dependencies

- Suggest additional features

- Remove items that interviewer considers out of scope

  

2\. Think about constraints and non-functional requirements

- (use PASS ME if you do not remember all of NFRs)

- Recognize the number of users

- Estimate users growth rate (for the next year/next five years)

- Define average response time

- Understand database size (current / for the next year/ for the next five years)

- Understand storage size (current / for the next year/ for the next five years)

- Recognize security needs

- Define acceptable downtime of the system

- Recognize the number of requests (per month/per second)

- Estimate reads vs. writes operations percentage

- Define time to market

- Check customer related NFR: legacy/proprietary soft, etc

  

3\. Detect Architecture Significant Requirements

- Mix between FRs and NFRs to detect ASRs

  

4\. Abstract Design

- Choose which architectural views to define based on the stakeholders’ matrix. Use common C4/4+1/etc otherwise

- Choose Architecture Style (Monolith, SOA — microservices, layered architecture, etc.)

- Choose between cloud solution or on-premise servers

- Consider authentication/authorization and privacy

- Suggest security rules and protocols

- Define infrastructure: load balancing, messaging

- Make a rough overview of any critical algorithm that drives the service

- Consider bottlenecks and determine solutions

- Choose storage type (SQL or NoSQL)

- Understand what data should be cached and how to improve performance/security/availability with caching

- Choose monitoring system and logging. Analytics and automatically reboot the system in case of exceptions

- Define separation between public and restricted areas