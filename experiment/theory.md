### Theory

#### Finite Automaton (FA)

A **Finite Automaton (FA)** is a mathematical model of computation that acts as an abstract machine for recognizing patterns. It consists of a finite number of states and transitions between them, based on input symbols.  

Its main purpose is to determine whether an input string conforms to a predefined pattern—**accepting** or **rejecting** it.  

Formally, an FA is a 5-tuple:

\[
M = (Q, \Sigma, \delta, q_0, F)
\]

where:  
- **Q** → Finite set of states  
- **Σ (Sigma)** → Finite set of input symbols (alphabet)  
- **δ (delta)** → Transition function  
  - DFA: δ : Q × Σ → Q  
  - NFA: δ : Q × Σ → 2^Q (set of possible next states)  
- **q₀** → Initial state (q₀ ∈ Q)  
- **F** → Set of accepting (final) states, F ⊆ Q  

**Applications:** Finite automata form the foundation of **regular languages** and are used in compilers (lexical analysis), pattern matching, and input validation.

---

#### Regular Expressions (RE)

A **Regular Expression (RE)** is a symbolic representation of a **regular language**. It defines patterns over an alphabet using operators such as union, concatenation, and repetition.  

A language is regular **iff** it can be described by a regular expression.

##### Formal Definition of Regular Expressions

Let Σ be an alphabet. The set of **regular expressions** over Σ is defined recursively:

###### Base Cases
1. **Empty set (∅):**  
   - RE: `∅`  
   - Language: L(∅) = {} (no strings)  

2. **Empty string (ε):**  
   - RE: `ε`  
   - Language: L(ε) = {""}  

3. **Single symbol (a ∈ Σ):**  
   - RE: `a`  
   - Language: L(a) = {"a"}  

###### Recursive Cases (If R₁ and R₂ are REs)
1. **Union (R₁ | R₂):**  
   - Language: L(R₁ | R₂) = L(R₁) ∪ L(R₂)  

2. **Concatenation (R₁R₂):**  
   - Language: L(R₁R₂) = {xy | x ∈ L(R₁), y ∈ L(R₂)}  

3. **Kleene Star (R₁*):**  
   - Language: L(R₁*) = {ε, w, ww, www, ... | w ∈ L(R₁)}  

4. **Parentheses ():**  
   - Used for grouping, e.g., `(a|b)c`  

---

#### Non-Deterministic Finite Automaton (NFA)

An **NFA** is a finite automaton where multiple transitions for the same symbol are allowed, and ε-transitions (without consuming input) are possible.

##### Characteristics
- **Multiple transitions:** From one state, there may be several outgoing transitions for the same input.  
- **ε-transitions:** State changes can occur without reading input.  
- **Acceptance rule:** An input is accepted if **at least one computation path** leads to an accepting state.  
- **Equivalence:** Every NFA has an equivalent DFA, though conversion may cause an exponential increase in states.  

---

#### Thompson’s Construction: RE → NFA

**Thompson’s Construction** systematically converts a **regular expression** into an equivalent **NFA**.  

**Key Property:** Each constructed NFA has **exactly one start state and one final state**, which makes recursive construction simple.  

##### Construction Rules

###### Base Cases
- **Empty set (∅):**  
  - NFA: Start and final states with **no transition**.  

- **Empty string (ε):**  
  - NFA: Start →ε→ Final  

- **Single symbol (a):**  
  - NFA: Start →a→ Final  

###### Recursive Cases
- **Concatenation (R₁R₂):**  
  - Connect final state of NFA(R₁) to start state of NFA(R₂) with an ε-transition.  
  - Start = start of R₁, Final = final of R₂  

- **Union (R₁ | R₂):**  
  - Create new start and final states.  
  - ε-transition from new start to both R₁ and R₂ starts.  
  - ε-transition from both R₁ and R₂ finals to new final.  

- **Kleene Star (R*):**  
  - Create new start and final states.  
  - ε-transition from new start → old start.  
  - ε-transition from old final → old start (loop).  
  - ε-transition from old final → new final.  
  - ε-transition from new start → new final (for zero repetitions).  
