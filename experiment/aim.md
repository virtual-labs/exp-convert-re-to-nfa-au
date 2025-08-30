### Aim of the Experiment

The objective of this experiment is to **convert a given Regular Expression (RE) into an equivalent Non-Deterministic Finite Automaton (NFA)** using **Thompson’s Construction method**.  
This experiment demonstrates the step-by-step transformation process, enabling learners to understand how regular expressions can be systematically represented as finite automata.  
This is a key concept in **pattern recognition, lexical analysis, and compiler design**.

Thompson’s Construction is an algorithmic method that constructs an NFA from a regular expression by recursively handling its basic operators:

1. **Concatenation (`AB`)** → Connect the NFA of `A` to the NFA of `B` using ε-transitions.  
2. **Union (`A|B`)** → Create a new start state with ε-transitions to the start states of `A` and `B`, and a new final state with ε-transitions from the final states of `A` and `B`.  
3. **Kleene Star (`A*`)** → Create a new start and final state. Connect the start state to `A`’s start and to the new final state via ε-transitions. Loop from `A`’s final state back to its start and to the new final state using ε-transitions.  
   
This ensures that the resulting NFA accepts the same language as the original regular expression.

