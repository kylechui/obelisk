---
id: "Front End"
aliases: []
tags:
  - "CS132"
---

- The front end is language-specific, but architecture-agnostic
- It is responsible for:
  - Recognizing legal procedures
  - Reporting errors
  - Producing the IR
  - Preliminary storage map
  - Shaping the code for the back end
- Scanner:
  - Maps the characters into tokens
    - **Lexeme**: string value for a token
    - Eliminates white space
    - Speed is a priority
  - The tokens are then passed to the parser
- Parser:
  - Recognizes context-free syntax
  - Guides context-sensitive analysis
  - Construct IR(s)
  - Produce meaningful error messages
  - Attempt error correction
- The IR(s) are then passed to the [[Front End|front end]]
