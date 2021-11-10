# EasyCrypt

> formal methods to prove things, especially cryptography-related

- given a => b, move a into the hypotheses:
`move=> {{hyp-name}}`

- the thing to prove is now in the hypotheses:
`assumption`

- when assumption works, it's the same as `apply {{hyp-name}}` with the right hyp-name.

- apply an hypothesis (of the form a => b, b being to prove):
`apply {{hyp-name}}`

- to prove a /\ b, separate into 2 subgoals a and b:
`split`

- given a /\ b as an hypothesis, separate into 2 hypotheses a and b:
`elim {{hyp-name}}`

- given a \/ b, do a case analysis (either it's a or b):
`elim {{hyp-name}}`

- prove a \/ b by proving the left or right part:
`left`
`right`

- given a forall and wanting to prove the corresponding exists:
`apply {{hyp-name}}`
`apply ({{hyp-name}} {{value}})`

- case analysis:
`case`
`case ({{predicate}})`

- given a => b => c => d..., put everything except the end into hypotheses:
`progress`

- given a = b or a <=> b, replace all occurrences of one to the other:
`rewrite {{hyp-name}}`

- call an external SMT:
`smt`

- call an external SMT, sending it only the current hypothesis:
`smt()`

- call an external SMT, sending it axioms to use:
`smt({{axiom1}} {{axiom2}})`

- for the visual organization of proofs, but no semantic:
`- {{...}}`

- search all lemmas related to an object:
`search {{object}}`
`search {0,1}`

- solve a very simple remaining goal:
`done`

- tactic; done
`by tactic`

- trivial:
`trivial`

- use n as a real, not an integer:
`{{n}}%r`

- TODO
`have`
`exists`

- ??
`by case {{var-name}}`
`last case {{var-name}}`
`apply h` vs `apply: h`
`subst {{var}}`
`auto`
`auto => /#`
`... => //`

## Program proving
- take the code of a function:
`proc`

- compute a weakest precondition:
`wp`

- compute a strongest postcondition:
`sp`

- when a program is empty, switch to the previous set of methods (exit program proving mode):
`skip`

- skip and clean the goal a bit:
`skip => />`

- case analysis for an if:
`if`

- we know that the if statement condition is false/true:
`rcondt {{instruction-number}}`
`rcondf {{instruction-number}}`

- simplify the pre and postconditions:
`=> /=`

- give a loop invariant:
`while ({{expression}})`

- inline a procedure call:
`inline {{function-name}}`

## Probabilistic programs
- type 'a distr = the discrete distributions over a

- the distribution that returns 0 or 1 with probability 1/2:
`{0,1}`

- the uniform distribution over some contiguous integers:
`[n..m]`

- the uniform distribution over some type:
`duniform<:t>`

- weight of a distribution:
`weight {{distribution-name}}`

- incorporate probabilistic instructions into the pre/postconditions:
`rnd`

- pivot rnd by the result of an intermediate event:
`rnd ({{event}}) ({{p(event)}}) ({{p(result | event)}}) ({{p(!event)}}) ({{p(result | !event)}})`

- similar to above:
`seq {{position}}: ({{event}}) ({{p(event)}}) ({{p(result | event)}}) ({{p(!event)}}) ({{p(result | !event)}})`

- more general syntax for seq:
`seq {{position}}: ({{event}}) ({{p(event)}}) ({{p(event' | event)}}) ({{p(!event)}}) ({{p(event' | !event)}}) ({{event'}})`
