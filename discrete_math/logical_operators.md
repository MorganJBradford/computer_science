---
id: logical_operators
aliases: []
tags: []
---

_Negation, Conjunction, and Disjunction_

There are 6 logical operators that wel will focus on:

- Negation
- Conjunction
- Disjunction
- Exclusive Or
- Implication
- Biconditional

Compound propositions are formed by combining simple propositions using logical operators.

Negation
: Let p be a proposition. ~p is called negation of p which simyl states that
: "It is not the case that p"
: if p is true then ~p is false and vice versa.

Conjunction
: Let p and q be two propositions. Conjunction of p and q is donoted by p ^ q
: When both p and q are true then only the compound proposition p ^ q is true.
- Both 'but' and 'and' are used to represent conjunction.

| p | q | p ^ q |
|---|---|-------|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   F   |

Disjunction
: Let p and q be two propositions. The XOR of p and q (denoted by p ⊕ q) is a proposition that simply means that exactly one of p and q will be true but both cannot be true at the same time.
- Either 'or' or 'but not both' are used to represent disjunction.

| p | q | p ⊕ q |
|---|---|-------|
| T | T |   F   |
| T | F |   T   |
| F | T |   T   |
| F | F |   F   |

Implication
: Let p and q be two propositions. The proposition "if p then q" as denoted by p -> q is called _implication_ or _conditional_ statement.

| p | q | p -> q |
|---|---|-------|
| T | T |   T   |
| T | F |   F   |
| F | T |   T   |
| F | F |   T   |

- p is called _hypothesis_ (or premise) and q is called _conclusion_ (or consequence).

Example 1:
> "If you study hard, then you will pass the exam."
- Here, studying hard is the hypothesis and passing the exam is the conclusion.

p = "You study hard"
q = "You pass the exam"

Case 1: If you study hard and you pass the exam, then the statement is true.
> p = T, q = T
> p -> q = T

Case 2: If you study hard but you do not pass the exam, then the statement is false.
> p = T, q = F
> p -> q = F

Case 3: If you do not study hard but you pass the exam, then the statement is true.
> p = F, q = T
> p -> q = T | why?
- Because you can make the compound proposition false only when you satisfy the first condition itself i.e. If that itself not satisfied then we cannot make compound proposition false. Not false means true.

Case 4: If you do not study hard and you do not pass the exam, then the statement is true.
> p = F, q = F
> p -> q = T

u Golden Rule:
## If the hypothesis is false, then the statement is always true.
### p -> q = T, when p = F

    _Implication_ - _ Representations_
Different Ways to represent conditional statements:

    - "if p then q"
    - "p implies q"
    - "q when p"
    - "q whenever p"
    - "q follows from p"
    - "p only if q"
    - "q is necessary for p"
    - "p is sufficient for q"
    - "q unless ~p"

# "p only if q"
  > how "if p then q" and "p only if q" can be the same?
  > "I will stay home only if I'm sick."
  >> let p = "I will stay at home" and q = "I'm sick"
  >> p only if q = p -> q
  >>> According to the above statement, becoming sick is the necessary condition for staying at home.
  > Proof idea: trueth value of p and q must be the same in order to falsify the compound proposition.
  > if p then q "If I stay at home, then I'm sick."

