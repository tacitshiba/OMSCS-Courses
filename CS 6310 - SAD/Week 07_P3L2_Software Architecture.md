# Lesson 15

The second major topic in this course is software architecture. In this lesson we will examine software architecture as well as diagrams that go along with software architecture.

## [Informal Definition](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#informal-definition)

**Software architecture** is the organization of a system into component subsystems or modules. It can be iteratively refined into multiple layers and often makes use of the stereotypical architectural style.

### Quiz

Analysis models ..

- can adapt well to changes in customer requirements <T>
- should represent the approach that will be taken in design <F> (we actually want to avoid mixing analysis and design together or else we might bias the design approach that is taken.
- are resilient to changes in hardware <T>
- includes all components required by a system <F>

## [USP Definition](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#usp-definition)

The set of significant decisions about the organization of a software system, the selection of the structural elements and their interfaces by which the system is composed, together with their behavior as specified in the collaborations among those elements, the composition of these structural and behavioral elements into progressively larger subsystems, and the architectural style that guides this organization: these elements and their interfaces, their collaborations, and their composition. Software architecture is concerned not only with structure and behavior but with usage, functionality, performance, resilience, reuse, comprehensibility, economics and technology constraints and trade-offs, and aesthetic concerns.

Software architecture is concerned not only with structure and behavior but with usage, functionality, performance, resilience, reuse, comprehensibility, economics and technology constraints and trade-offs, and aesthetic concerns.

## [Other Definitions](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#other-definitions)

For representing architectures we have the following:

- Component: computational or data element interface to the rest of the system
- Connector: communication protocols among components
- Configuration: components hooked up with connectors

## [Selecting Components](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#selecting-components)

What are some steps to selecting components? We typically look for

- Required functionality
- Existing reusable components
- Physical machine architecture
- Expertise of staff
- Conway's Law
- Projected evolution trajectories

## [APIs](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#apis)

**APIs (Application Programming Interface)**:

- Include names of access ports, arguments, types
- Can be described in a specific programming language; language binding
- Might be described in OCL
- Can be described using ADLs (Architectural Description Language)

## [Architectural Views](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#architectural-views)

The architecture of a system comprises all of the decisions controlling how a specified problem solution is realized. Because this set of decisions may be quite large and eclectic, various architectural diagrams are used to convey some portion of them.

## [Architectural Styles](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#architectural-styles)

Different architectural styles might offer the following benefits:

- Encoded experience
- Standards (validation, selection criteria, etc.)
- Reuse
- Support of process

Component-based: reusable modules communicating through well-defined interfaces

Coroutines:  symmetric interaction

Data centric: Use of stored databases procedure

Domain Driven Design (DDD)

Implicit invocation: events, callbacks, registration-broadcast

Layered: virtual/abstract machines, limited visibility

…

## [Style Issues](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#style-issues)

There are various issues when it comes to architectural styles however:

- Some systems have more than one style (heterogeneous)
- Other systems might include DSSA (domain-specific software architecture) or reference architecture
- Semantics could become an issue with multiple styles

## [Architecture Description Language](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#architecture-description-language)

**ADL** is a notation for describing architecture as discussed earlier. It includes formality and precision and is a prerequisite for tool support.

## [Architectural Evaluation](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#architectural-evaluation)

Architectural evaluation is a systematic assessment of architecture properties and includes:

- Architecture review boards
- SAAM (Software Architecture Assessment Method)
- ATAM (Architecture Tradeoff Analysis Method)

## [Summary](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#summary)

The ultimate goal is to increase the quality of delivered systems and reduce the cost of producing them.

## [Section Quizzes](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#section-quizzes)

### [Analysis To Components Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#analysis-to-components-quiz)

*Assume we want to determine the components of a software system based solely on an analysis model. Given this scenario, select true or false for each statement*.

Analysis models...

- Can adapt well to changes in customer requirements
- Should **NOT** represent the approach that will be taken in design
- Are resilient to changes in hardware
- Do **NOT** include all components required by a system

### [UML Diagram Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#uml-diagram-quiz)

*Recall at least 3 kinds of UML diagrams that can be used to convey architectural views*.

We can use class model, sequence, communication, etc.

### [Arch Style Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2015%20(P3L2)%20-%20Overview%20of%20Architectural%20Styles.md#arch-style-quiz)

*What style is defined by the list of decisions (given in lecture)*?

Client server

## Quiz

- What is Conway's law?   Organizations design systems that mirror their own communication structure
- Selecting a component should account for reusable existing components <T>
- Define software architecture → The organization of a system into subsystems or modules
- Selecting a component should not account for a team's expertise <F>
- Which of the following architecture styles describe asynchronous message passing with independent threads of control?    [peer-to-peer]x
- Which of the following describe the "Production systems" architectural style? Rule based, conditional firing
- Which of the following architectural styles allow for multiple service providers to dynamically emerge in order to load balance?   Client server
- A monolith arises from the lack of architectural styles   <T>
- Which architectural style enables asynchronous message passing over a common data highway?   Message Bus
- Which of the following is a characteristic of software architecture?    It is iterative and multi-layered
- Which of the following architecture styles describes a one-way, sequential, stdin-stdout stream?  Pipe and filter
- What is an example of a connector?  A procedure call/return
- The software architecture of a deployed software is determined by those aspects that are hardest to change <T>
- What is a software component?   An architectural entity that encapsulates a system's functionality and/or data
- What is a software architecture's configuration?  A specific set of associations between components and connectors
- What is a heterogeneous system?   A system that has more than one architectural style