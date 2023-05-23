---
id: "LR Parsing"
aliases:
  - "Implementation"
tags:
  - "CS132"
---

- Recall the original motivation for LL(1) parsing
  - L: Read the input from left to right
  - L: Always use the left-most derivation
  - 1: We should also perform lookahead by one symbol
- Compare the above with LR(1) parsing
  - L: Read the input from left to right
  - R: Always use the right-most derivation
  - 1: We should also perform lookahead by one symbol
- $LL(1)\subseteq LR(1)$, i.e. all LL(1) grammars are LR(1) grammars, but _not_
  the other way around
- We will build the right-most derivation _backwards_, by _ending with the start
  symbol, $S$_
  - Instead of always adding nodes below like in LL(1), we add always nodes
    above in LR(1)
- Consider the input string $abbcde$ with rules

$$
\begin{align*}
S &\mapsto aABe \\
A &\mapsto Abc \mid b \\
B &\mapsto d
\end{align*}
$$

- We then evaluate, by looking at prefixes and matching against the right-hand
  sides of the productions, from right to left:
  - $a\mapsto a$
  - $ab\mapsto aA$
  - $abb\mapsto aAb$
  - $abbc\mapsto aAbc\mapsto aA$
  - $abbcd\mapsto aAd\mapsto aAB$
  - $abbcde\mapsto aABe\mapsto S$
- We are trying to find _handles_, which are the right-hand-sides of the
  productions that can be matched right-to-left in our input
- Theorem: If $G$ is unambiguous then every right-sentential form has a unique
  handle
  - A grammar $G$ is _ambiguous_ if and only if there exists two different
    production trees that evaluate to the same token string $w$
  - For example, `if b1 then if b1 then s2 else s3` can be interpreted as
    either `if b1 then (if b1 then s2 else s3)` or `if b1 then (if b1 then s2)
else (s3)`
  - We wish to have unambiguity, so we can parse in linear time

## Implementation

- One scheme to implement a handle-pruning, bottom-up parser is called a
  _shift-reduce_ parser
- The main data structure used is the stack, with an input buffer
- Algorithm:
  - Initialize stack with `$`
  - Repeat until the top of the stack is the goal symbol and the input is `$`
    - If a handle exists on the top of the stack, _reduce_ by popping off the
      handle and pushing the symbol on the LHS onto the stack
    - Otherwise, _shift_ an input symbol onto the stack

## Shift-Reduce Parsing

- A shift-reduce parser has four canonical actions:
  - Shift: Move next input symbol from input buffer onto the stack
  - Reduce: Right end of handle is replaced with start symbol
  - Accept: Return that the parsing succeeded
  - Error: Return some error state

## LR(1) Parse Table Size

- Recall that the size of a LL(1) parse table is the number of non-terminal
  symbols multiplied with the number of terminal symbols
- The rows of the LR(1) parse table each represent a list of symbols that is the
  LHS of a production yielding a handle
  - Thus the size of the LR(1) parse table is the number of lists of symbols
    multiplied with the number of terminal symbols

## Why LR(1)?

- Virtually all PLs can be expressed in an LR(1) form
- LR grammars are the most general grammars parsable by a deterministic,
  bottom-up parser
- Efficient parsers can be implemented for LR(1) grammars
- LR parsers detect errors as soon as possible in a left-to-right scan of the
  input
- LR grammars are a proper superset of LL grammars

## Fun Facts

- **Note**: For natural languages, ambiguity is inevitable, so we parse using
  ambiguity-tolerant parsers that are _not_ linear-time
  - Oftentimes this relies on dynamic programming techniques in order to have
    sub-exponential runtime
