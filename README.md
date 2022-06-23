# Solving-Boolean-SAT-problem-using-Grovers-Algorithm
This repository is about solving a particular Boolean satisfiability problem using Grover's algorithm from Scratch.
Grover's Algorithm is a quantum search algorithm which provides quadratic speed up over the classical algorithms when
searching on unsorted and large datasets.

Problem Statement-Frank wants to throw a dinner party to celebrate Alice and Bob’s engagement. He is also considering 
inviting their mutual friends Charles, Dave and Eve. However, he is aware that Charles will come to the party only if 
Dave comes without Eve. Frank wants to know what possible combinations of invitations he can write for his friends 
Alice, Bob, Charles, Dave and Eve. 
Help Frank calculate all the possible combinations using Grover’s algorithm.

In total, there are 32 combinations of invitations. The equivalent boolean expression for the problem statement is

(Alice AND Bob AND (-Charles)) OR (Alice AND Bob AND Charles AND Dave AND (-Eve))

Let's initialize 5 qubits with lebels qo-Alice, q1-Bob, q2-Charles, q3-Dave, q4-Eve. So, there are five winner states which
satisfies the above boolean expression viz.

|11000>, |11001>, |11010>, |11011> and |11110>.

Now, let's try to make a oracle circuit which adds a -ve phase only to winner states. For details of oracle construction refer
to  https://drive.google.com/file/d/1MgX91DmX6Nq2qfPI5rj1UOEXTNTekyAI/view?usp=sharing

Applying Hadamard gate to all qubits gives uniform superposition of all possible states. Now, passing this uniform superposition
to our oracle gives a uniform superposition state with negative phase in front of all the winner states.

|x> -oracle-> |x>        (|x> != |11000>, |11001>, |11010>, |11011> or |11110>)

|w> -oracle-> -|w>       (|w> = |11000>, |11001>, |11010>, |11011> or |11110>)

Now, we add grover operator to our circuit to perform reflection of whole state about it's mean, which in turn amplifies
the probability of winner states. This action can also be visualised as reflection about uniform superposition state |s>.

The successive application of grover operator after the oracle, amplifies the winning states. The question arises 
"how many iterations of these two operators we should apply to our qubits to sufficiently increse the probablity of winning?"
In this case, only one grover iteration should be applied to increase winning probablity to 88 %.
For details of calculation refer to following link. 
https://drive.google.com/file/d/1UtcFw6IsJc19JHbum4Cvy2Oluw5Xz1oT/view?usp=sharing

Conclusion- Using grovers algorithm, we get a state where probablity of success (getting a solution state) upon measurement 
is over 88 % in a single grover's iteration. 
It ran for hundred shots in qasm simulator to reach all five winner states.
