---
id: logical_operators
aliases: []
tags: []
---

# _Negation, Conjunction, and Disjunction_

There are 6 logical operators that we will focus on:

- Negation
- Conjunction
- Disjunction
- Exclusive Or
- Implication
- Biconditional

Compound propositions are formed by combining simple propositions using logical operators.

## Negation
- Let p be a proposition. $\neg p$ is called negation of p which simyl states that
- "It is not the case that p"
- if p is TRUE then $\neg p$ is FALSE and vice versa.

## Conjunction
- Let p and q be two propositions. Conjunction of p and q is donoted by p ^ q
- When both p and q are TRUE then only the compound proposition p ^ q is TRUE.
- Both 'but' and 'and' are used to represent conjunction.

| $p$ | $q$ | $p \land q$ |
|---|---|-------|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   F   |

## Disjunction
- Let p and q be two propositions. The XOR of p and q (denoted by p ⊕ q) is a proposition that simply means that exactly one of p and q will be TRUE but both cannot be TRUE at the same time.
- Either 'or' or 'but not both' are used to represent disjunction.

| $p$   | $q$   | $p \oplus q$ |
| --- | --- | ----- |
| T   | T   | F     |
| T   | F   | T     |
| F   | T   | T     |
| F   | F   | F     |

## Implication
- Let p and q be two propositions. The proposition "if p then q" as denoted by p -> q is called _implication_ or _conditional_ statement.

| $p$ | $q$ | $p \Rightarrow q$ |
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

Case 1: If you study hard and you pass the exam, then the statement is TRUE.
> $p = T,\ q = T$
> $p \Rightarrow q = T$

Case 2: If you study hard but you do not pass the exam, then the statement is FALSE.
> $p = T,\ q = F$
> $p \Rightarrow q = F$

Case 3: If you do not study hard but you pass the exam, then the statement is TRUE.
> $p = F,\ q = T$
> $p \Rightarrow q = T$ | why?
- Because you can make the compound proposition FALSE only when you satisfy the first condition itself i.e. If that itself not satisfied then we cannot make compound proposition FALSE. Not FALSE means TRUE.

Case 4: If you do not study hard and you do not pass the exam, then the statement is TRUE.
> $p = F,\ q = F$
> $p \Rightarrow q = T$

## Golden Rule:
### If the hypothesis is FALSE, then the statement is always TRUE.
#### $p \Rightarrow q = T, when\ p = F$

# _Implication_ - _Representations_
Different Ways to represent conditional statements:

- "$if\ p\ then\ q$"
    - "$p\ implies\ q$"
    - "$q\ when\ p$"
    - "$q\ whenever\ p$"
    - "$q\ follows\ from\ p$"
    - "$p\ only\ if\ q$"
    - "$q\ is\ necessary\ for\ p$"
    - "$p\ is\ sufficient\ for\ q$"
    - "$q\ unless\ \neg p$"

## "$p\ only\ if\ q$"
### how "$if\ p\ then\ q$" and "$p\ only\ if\ q$" can be the same? \
> "I will stay home only if I'm sick."
>> let p = "I will stay at home" and q = "I'm sick" \
>> p only if $q = p \Rightarrow q$
>>> According to the above statement, becoming sick is the necessary condition for staying at home.
> Proof idea: truth value of p and q must be the same in order to falsify the compound proposition. \
> if p then q "If I stay at home, then I'm sick." \
> The only way to falsify the above statement is by making p TRUE and q FALSE. \
> Therefore, p only if q is equivalent to if p then q.

### Why "p only if q" is not equivalent to "if q then p"? \
> "I will stay home only if I'm sick."
>> p = "I will stay at home" and q = "I'm sick"
>>> Proof: p only if q is FALSE when p is TRUE and q is FALSE.
>>>> If q then p: "If I'm sick, then I will stay at home." \
>>>> Are these two statements equivalent? \
>>>> Tyically we know that:
>>>>> if: $FALSE \Rightarrow TRUE = TRUE$ \
>>>>> We need to change the table to q implies p to make it equivalent to p only if q.

| $q$ | $p$ | $q \Rightarrow p$ |
|---|---|--------|
| T | T |   T    |
| T | F |   F    |
| F | T |   T    |
| F | F |   T    |

As when p is TRUE and q is FALSE, "p only if q" is FALSE but same TRUE values of p and q, "if q then p" is TRUE.
Therefore, "p only if q" is not equivalent to "if q then p".

q is the necessary condition for p. So if q is FALSE, then p has to be FALSE.

## "$q\ is\ necessary\ for\ p$"

> Example: "Good food is necessary to keep us alive"
>> According to this statement, if we don't have good food then we will die.
>> However, is this the only factor keeping us alive? No.
>>> Example: "My friend died at the age of 16 and he has no shortage of good food".
>>> Even though he has good food, he still died.

>> Therefore, when we say A is necossary for B then falsity of A guarantees the falsity of B but _we cannot guarentee_ the _truth_ of B from the truth of A.
>> Similarly, when we say q is necessary for p, then we can only guarentee that when q is false, then p is definitely false.

## "$p\ is\ sufficient\ for\ q$"

> Example: "It is sufficient for you to travel by car in order to reach your destination on time."
>> Definitely, if you travel by car, you'll reach your destination on time. No doubt.
>> But if you won't travel by car, does it mean you'll never reach your destination on time? May be by flight or other means of transport you'll reach your destination much earlier.
> Therefore, when we say that when A is sufficient for B then, trueth of A guarantees the thruth of B but _we cannot guarentee_ the _falsity_ of B from the falsity of A.
> Similarly, when we say the "p is sufficient for q", then we can only guarentee that when p is true, then q is definitely true.

### why is p not necessary for q?

| $p$ | $q$ | $p \Rightarrow q$ |
|---|---|--------|
| T | T |   T    |
| T | F |   F    |
| F | T |   T    |
| F | F |   T    |

Proof by contradiction:
> Let say p is necessary for q.
> if p is really necessary for q then if p is false then it is mandatory for q to be false in order to make the whole compound proposition p->q true. But it is not the case.
> According te the truth table it is not mandatory for q to be false when p is false. Hence "p is no necessary for q".

### Why is q not sufficient for p?

| $p$ | $q$ | $p \Rightarrow q$ |
|---|---|--------|
| T | T |   T    |
| T | F |   F    |
| F | T |   T    |
| F | F |   T    |

Proof by contradiction:
> Let say q is sufficient for p.
> if q is really sufficient for p then if q is true then it is mandatory for p to be true in order to make the whole compound proposition p->q true. But it is not the case.
> According te the truth table it is not mandatory for p to be true when q is true. Hence "q is no sufficient for p".

## "$q\ unless\ \neg p$"
unless
: 'expect if'

> _Evolution steps_:
>> "if p then q" (if p is true then q must be true)
>>      V
>> "q is true when p is true"
>>      V
>> "q is true except when p is false"
>>      V
>> "q is true unless p is false" = "$q\ unless\ \neg p$"

# _Implication_, _Converse_, _Contrapositive_, and _Inverse_

Implication or conditional statement: $p \Rightarrow q$
Converse: $q \Rightarrow p$
Contrapositive: $\neg q \Rightarrow \neg p$
Inverse: $\neg p \Rightarrow \neg q$

Example: "If it rains today, then I will stay at home."
Converse - "If i will stay at home then it rains today."
Contrapositive - "If I will not stay at home then it will not rain today."
Inverse - "If it will not rain today then I will not stay at home."

Facts:
> Implcation and contrapositive are equivalent.
> Converse and inverse are equivalent.
> Neither converse tor inverse is equivalent to implication.

| $p$ | $q$ | $\neg p$ | $\neg q$ | $p \Rightarrow q$ | $q \Rightarrow$ p | $\neg q \Rightarrow \neg p$ | $\neg p \Rightarrow \neg q$ |
|---|---|----|----|--------|--------|----------|----------|
| T | T | F  | F  |   T    |   T    |    T     |    T     |
| T | F | F  | T  |   F    |   T    |    F     |    T     |
| F | T | T  | F  |   T    |   F    |    T     |    T     |
| F | F | T  | T  |   T    |   T    |    T     |    T     |



## Biconditional Operator

Definition: let p and q be two propositions. The biconditional statement of the form $p \iff q$ is the proposition "$p\ if\ and\ only\ if\ q$".
$p \iff q$ is true whenever the truth values of p and q are the same.

| $p$ | $q$ | $p \iff q$ |
|---|---|--------|
| T | T |   T    |
| T | F |   F    |
| F | T |   F    |
| F | F |   T    |

How does "$p\ if\ and\ only\ if\ q$" makes sense?
"$p\ if\ and\ only\ if\ q$" is composed of two statements:
"$p\ if\ q$" and "$p\ only\ if\ q$"

"$p\ only\ if\ q" = if\ p\ then\ q$ and "$p if q" = "if\ q\ then\ p$"
$(p \Rightarrow q) \land (q \Rightarrow p) \equiv p \iff q$


Representations:

1. p is necessary and sufficient for q and vice versa
2. if p then q, and conversely
3. p iff q

Example: let p be a proposition "You get promoted" and let q be a proposition "You have connections"

then $p \iff q$ = "You get promoted if and only if you have connections."
