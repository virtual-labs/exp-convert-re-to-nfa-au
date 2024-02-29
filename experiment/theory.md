<u><h3>Theory</h3></u>
<u><p><b> 1. NFA (Non-Deterministic finite automata)</b></p></u>
 - NFA stands for non-deterministic finite automata. It is easier to construct an NFA than DFA for a given regular language.
 - The finite automata are called NFA when there exist many paths for specific input from the current state to the next state.
 - Every NFA is not DFA, but each NFA can be translated into DFA.
 - NFA is defined in the same way as DFA but with the following two exceptions, it contains multiple next states, and it contains ε transition.

<u><p><b>2.Regular Expression</b><p></u>

  - The language accepted by finite automata can be easily described by simple expressions called Regular Expressions. It is the most effective way to represent any language.
 - The languages accepted by some regular expressions are referred to as Regular languages.
 - A regular expression can also be described as a sequence of patterns that defines a string.

  
 When converting a regular expression to a nondeterministic finite automaton (NFA), the following operations are typically performed:

<b>Concatenation:</b> Combining two regular expressions in sequence
<b>Union:</b> Allowing for a choice between two regular expressions
<b>Kleene star:</b> Allowing for zero or more repetitions of a regular expression
<b>Grouping:</b> Grouping parts of the regular expression together to maintain proper precedence


<u><h5>Thompson's algorithm</h5></u>
<p>Thompson's algorithm is a method for converting a regular expression into an equivalent nondeterministic finite automaton (NFA). The algorithm uses a set of rules to construct the NFA based on the structure of the regular expression, including handling concatenation, union, and the Kleene star. The resulting NFA can then be used to efficiently match the pattern defined by the original regular expression.</p>

<u><b>Rules to convert RE to NFA</b></u>

<p>1.Symbol (a) (basic RE)</p>

 - Create  two states start state  and accept state (final).
 - Add a transition from start state to accept state  labelled 'a'.
 - Mark the final/accept state . 
 <p>for example:</p> 
 <b><P>Regular Expression:"a"</P></b>
<div><img src="./images/example1.png" alt="example1"><div>

<p>2. Concatenation (ab):</p>
<b>Converting Regular Expression to NFA using Concatenation </b>

  <u>Create an NFA for the character 'a':</u>

 - Create a start state and an accept state.
 - Add a transition labeled 'a' from the start state to the accept state.

 <u>Create an NFA for the character 'b':</u>
 - Create a start state and an accept state.
 - Add a transition labeled 'b' from the start state to the accept state.

<u>Connect the NFAs for 'a' and 'b' to represent the concatenation:</u>

 - Merge the accept state of the NFA for 'a' with the start state of the NFA for 'b', and remove the accept state of the NFA for 'a'.

<p>for example: </p>
<b><P>Regular Expression:"ab"</P></b>
<div><img src="./images/example2.png" alt="example1"><div>
<p>3. Union (a|b):</p>
<b>Creating NFA for Union Operation</b>

<u>States:</u>

 - New Start State
 - New Final State 

<u>Transitions:</u>

 - Add ε-transitions from the New Start State to the start states of the existing NFAs.
 - Add ε-transitions from the accepting states  of the existing NFAs to the New Final State .


<b>Note: </b>
When the union operation is performed, 4 ε-transitions are used in total:
 - 2 ε-transitions for connecting the New Start State to the existing NFAs
 - 2 ε-transitions for connecting the accepting states of the existing NFAs to the New Final State
<p>for example: </p>
<b><P>Regular Expression:"a|c"</P></b>
<div><img src="./images/example3.png" alt="example1"><div>
<p>4. kleene closure (a)*:</p>
<b>Converting Regular Expression to NFA using Kleene Closure</b>

<p><u>States:</u><p>

 - New Start State (S₀)
 - New Accept State (F₀)
<p><u>Transitions:</u><p>

 - Add ε-transition from New Start State (S₀) to the original start state of the expression.
 - Add ε-transition from the accept state of the expression back to the original start state.
 - Add ε-transition from original accept state to New Accept State (F₀).
 - Add ε-transition from New Start State (S₀) directly to New Accept State (F₀) for zero occurrences. 
 <p><b>Note:</b></p>
 When applying the Kleene closure function, 4 ε-transitions are used in total:

 - 2 ε-transitions for connecting the New Start State to the original start state and back to the original start state
 - 1 ε-transition for connecting the original accept state to the New Accept State
 - 1 ε-transition from the New Start State directly to the New Accept State for zero occurrences
 <p>for example: </p>
<b><P>Regular Expression:"a*"</P></b>
<div><img src="./images/example4.png" alt="example1"><div>