---
id: "Speculation"
aliases: []
tags:
  - "CSM151B"
---

- Also known as "branch prediction"
- Instead of stalling, basically just guess what the outcome of the branch is
  and fetch the next instruction based on that
  - By assuming that the branch is not taken, we behave correctly 86% of the
    time
    - Half if-else branches are taken + 90% of loop branches are taken
      (branching ~70% of the time)
    - 80% non-branch + 30% accuracy for branching
  - If the branch is taken, we have a correctness issue
    - We clear the incorrectly-fetched instructions, called
      [[Flushing|flushing]]
- Can we improve accuracy by predicting always taken?
  - Yes, but now we need `nextPC` at the fetch stage (so the we know where the
    instruction is after taking the branch)
- We don't know where labels are the first time that we see them, but we can
  guess where they are the next time we see them
  - We add a [[Branch Predictor|branch predictor]]
  - Predict taken if we have seen it before, not taken otherwise
    - This methodology works because it leverages [[Locality|temporal locality]]
      when we loop
    - Also `jal`, `jalr`, `call`, etc. are unconditional branches
