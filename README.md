# Solving-Boolean-SAT-problem-using-Grovers-Algorithm
This repository is about solving a particular Boolean satisfiability problem using Grover's algorithm from Scratch.

Problem Statement-Frank wants to throw a dinner party to celebrate Alice and Bob’s engagement. He is also considering 
inviting their mutual friends Charles, Dave and Eve. However, he is aware that Charles will come to the party only if 
Dave comes without Eve. Frank wants to know what possible combinations of invitations he can write for his friends 
Alice, Bob, Charles, Dave and Eve. 
Help Frank calculate all the possible combinations using Grover’s algorithm.

In total, there are 32 combinations of invitations. Clearly, Frank has two possible combinations of invitations 
viz. {Dave,Charles,Bob,Alice} and {Eve,Dave,Bob,Alice}. we initialize 5 qubits with lebels qo-Alice, q1-Bob, 
q2-Charles, q3-Dave, q4-Eve. So, the winner states are |11110> and |11011>.

Applying Hadamard gate to all qubits gives uniform superposition of all possible states. Now, applying a 
controlled z gate on q2 and q4 with q0,q1,q3 as control bits, gives a uniform superposition state with negative phase 
in front of winner states.

|x> -oracle-> |x>  (|x> != |11110> or |11011>)

|w> -oracle-> -|w> (|w> = |11110> or |11011>)

Now, we add grover operator to our circuit to perform reflection of whole state about it's mean, which in turn amplifies
the probability of winner states. This action can also be visualised as reflection about uniform superposition state |s>.

The successive application of grover operator after the oracle amplifies the winning states. The question arises 
"how many iterations of these two operators we should apply to our qubits to sufficiently increse the probablity of winning?"
It turns out that only two iterations required to make the winning chance greater than 90 %. 
For details of calculation refer to following link. 
https://drive.google.com/file/d/14cMakC-VxLV6Ig8FhQATigIBWkWKxihq/view?usp=sharing

Conclusion- We got our winner states with probability greater than 90 % just by running amplitude modification twice. 
It ran for two shots in qasm simulator to reach all winner states. 
Overall we called our oracle four times.
