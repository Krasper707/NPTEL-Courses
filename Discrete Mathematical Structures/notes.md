# Discrete Mathematical Structures.

Discrete Maths - Study of discrete structures that are abstract mathematical models that deal with discrete objects and their relationship between them.

Ex: Sets,Permutations,Graphs,etc

## Reference Books
- Elements of discrete mathematics : C.L.LIU (1985)
- Discrete Mathematical Structures with application to computer science: J.P TREMBLAY,R Manohar (1987)
- Discrete Mathematics in Computer Science : D.F Stanat , D.F McAllister ; 1977
- Discrete Mathematics and its applications ; Kenneth H Rosen ; 2003
- Introduction to Combinatorial Mathematics ; C L Liu (1968)
- Introduction to Automata theory, Languages and Computation. ; J Hofcroft ; 2001


### Proposition:
An Proposition which is either False or True but not both

Examples:
- 4 is a prime Number : False
- 3+3=6 : True

### Assertion:
An Assertion is a statement 


Truth Values (Standard)
False-0 ; True-1


Not Propositions:
- X+Y>4 ; Can be wrong for particular values and correct for others.
- X=3 ; Not a statement

The sentence `This statement is False` is a paradox; its neither wrong nor correct. ; Liar paradox ; As we cannot assign a truth value to that



### Propositional Variable
- A propositional variable denotes an arbitrary proposition with unspecified truth values P,Q,R...


### AND (^)
| P | Q | P^Q|
| --- | --- | --- | 
| F|F |F|
|F |T |F|
|T|F|F|
|T|T|T|

### Inclusive OR(v)
| P | Q | PvQ|
| --- | --- | --- | 
| F|F |F|
|F |T |T|
|T|F|T|
|T|T|T|


### Exclusive OR( $$\oplus$$ )
| P | Q | P $$\oplus$$ Q|
| --- | --- | --- | 
| F|F |F|
|F |T |T|
|T|F|T|
|T|T|F|

### $$\neg p$$

| P | $$\neg P$$ |
| --- | --- | 
| F|T |
|T |F |

### Propositional Form
- An assertion which contains at least one propositional variable is called a propositional form.
    - AND  : Conjunction
    - OR : Disjunction
    - Exclusive Or



Exclusive OR is used when we say "Either this or That"


Well formed formula(wff) / propositional logic:
A well-formed formula (WFF) is a syntactically correct expression within a formal language, meaning it follows the rules (grammar) of that language.


### Implication ( => )
P implies Q
| P | Q | P $$=>$$ Q|
| --- | --- | --- | 
| F|F |T|
|F |T |T|
|T|F|F|
|T|T|T|

In a logical implication (or conditional statement) like "If P, then Q," p is the antecedent (the condition or hypothesis), and q is the consequent (the result or conclusion)
P is the Hypothesis,Antecedent
Q is Consequent,Conclusion

Q => P is called the converse
$$\neg Q => \neg P$$ is called the contrapositive
 
### Equivalence

| P | Q | P $$<=>$$ Q|
| --- | --- | --- | 
| F|F |T|
|F |T |F|
|T|F|F|
|T|T|T|

P is equivalent to Q
P if and only if Q
P is a necessary and sufficient condition for Q

For k variables ;  we will have $$2^k$$ rows
Binary numbers from $$0 - (2^k-1)$$

### Tautology
- A propositional form whose truth value is true for all possible values of its propositional variables
- Ex: $$P$$ v $$\neg P$$

### Contradiction
- A propositional Form which is always false
- Ex: $$P$$ ^ $$\neg P$$

### Contingency 
- A propositional form which is neither a tautology nor a contradiction is called contingency.


## Logical Identities

Idempotence of v  , ^ 


Commutativity of v , ^ 


Associativity of v , ^


DeMorgan Laws


---


