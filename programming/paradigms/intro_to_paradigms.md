---
id: intro
aliases: []
tags: []
---

# Programming Paradigms

<dl>
    <dt>
        Programming paradigm
    </dt>
    <dd>
        a relatively high-level way to conceptualize and structure the implementation of a computer program. A programming language can be classified as supporting one or more paradigms.
    </dd>
</dl>

Paradigms are separated along and described by different dimensions of pragramming. Some paradigms are about implications of the [execution model](https://en.wikipedia.org/wiki/Execution_model), such as allowing _side effects_, or whether the sequince of operations is defined by the execution model. Other paradigms are about the way code is organized, such as grouping into units that include both state and behavior. Yet others are about syntax and grammar.

Some common programming paradigms include (shown in hierarchical relationship):

- [Imperative](https://en.wikipedia.org/wiki/Imperative_programming) – code directly controls [execution flow](https://en.wikipedia.org/wiki/Control_flow) and state change, explicit statements that change a program state
    - [procedural](https://en.wikipedia.org/wiki/Procedural_programming) – organized as [procedures](https://en.wikipedia.org/wiki/Function_(computer_programming) that call each other
    - [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming) – organized as [objects](https://en.wikipedia.org/wiki/Object_(computer_science)) that contain both data structure and associated behavior, uses data structures consisting of data fields and methods together with their interactions (objects) to design programs
        - [Class-based](https://en.wikipedia.org/wiki/Class_(computer_programming)) – object-oriented programming in which inheritance is achieved by defining classes of objects, versus the objects themselves
        - [Prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming) – object-oriented programming that avoids classes and implements inheritance via cloning of instances
- [Declarative](https://en.wikipedia.org/wiki/Declarative_programming) – code declares properties of the desired result, but not how to compute it, describes what computation should perform, without specifying detailed state changes c.f. imperative programming (functional and logic programming are major subgroups of declarative programming)
    - [functional](https://en.wikipedia.org/wiki/Functional_programming) – a desired result is declared as the value of a series of function evaluations, uses evaluation of mathematical functions and avoids state and mutable data
    - [logic](https://en.wikipedia.org/wiki/Logic_programming) – a desired result is declared as the answer to a question about a system of facts and rules, uses explicit mathematical logic for programming
    - [reactive](https://en.wikipedia.org/wiki/Reactive_programming) – a desired result is declared with data streams and the propagation of change
- [Concurrent programming](https://en.wikipedia.org/wiki/Concurrent_programming_language) – have language constructs for concurrency, these may involve multi-threading, support for distributed computing, message passing, shared resources (including shared memory), or [futures](https://en.wikipedia.org/wiki/Futures_and_promises)
    - [Actor programming](https://en.wikipedia.org/wiki/Actor_model) – concurrent computation with actors that make local decisions in response to the environment (capable of selfish or competitive behavior)
- [Constraint programming](https://en.wikipedia.org/wiki/Constraint_programming) – relations between variables are expressed as constraints (or constraint networks), directing allowable solutions (uses constraint satisfaction or [simplex algorithm](https://en.wikipedia.org/wiki/Simplex_algorithm))
- [Dataflow programming](https://en.wikipedia.org/wiki/Dataflow) – forced recalculation of formulas when data values change (e.g. [spreadsheets](https://en.wikipedia.org/wiki/Spreadsheet))
- [Distributed programming](https://en.wikipedia.org/wiki/Distributed_computing) – have support for multiple autonomous computers that communicate via computer networks
- [Generic programming](https://en.wikipedia.org/wiki/Generic_programming) – uses algorithms written in terms of to-be-specified-later types that are then instantiated as needed for specific types provided as parameters
- [Metaprogramming](https://en.wikipedia.org/wiki/Metaprogramming) – writing programs that write or manipulate other programs (or themselves) as their data, or that do part of the work at compile time that would otherwise be done at runtime
    - [Template metaprogramming](https://en.wikipedia.org/wiki/Template_metaprogramming) – metaprogramming methods in which a compiler uses templates to generate temporary source code, which is merged by the compiler with the rest of the source code and then compiled
    - [Reflective programming](https://en.wikipedia.org/wiki/Reflective_programming) – metaprogramming methods in which a program modifies or extends itself
- [Pipeline programming](https://en.wikipedia.org/wiki/Pipeline_programming) – a simple syntax change to add syntax to nest function calls to language originally designed with none
- [Rule-based programming](https://en.wikipedia.org/wiki/Rule-based_programming) – a network of rules of thumb that comprise a knowledge base and can be used for expert systems and problem deduction & resolution
- [Visual programming](https://en.wikipedia.org/wiki/Visual_programming_language) – manipulating program elements graphically rather than by specifying them textually (e.g. [Simulink](https://en.wikipedia.org/wiki/Simulink)); also termed diagrammatic programming
