Download link :https://programming.engineering/product/eecs-126-probability-and-random-processes-problem-set-4/


# EECS-126-Probability-and-Random-Processes-Problem-Set-4
EECS 126: Probability and Random Processes Problem Set 4
1. Reducible Markov Chain

Consider the following Markov chain, for ; ; p; q 2 (0; 1).

1

1

1

p

1 q

1=2

p

1=2

1=2

0

1

2

3

4

5

1=2

q

Find all the recurrent and transient classes.

Given that we start in state 2, what is the probability that we will reach state 0 before state 5?

What are all of the possible stationary distributions of this chain? Hint: Consider the recurrent classes.


(d) Suppose we start in the initial distribution 0 := 0 0 1 0 0 for some

2 [0; 1]. Does the distribution of the chain converge, and if so, to what?

2. Finite Random Walk

Assume 0 < p < 1. Find the stationary distribution. Hint: Let q = 1 p and =

p

, but be

q

careful when = 1.

3. Convergence in Probability

Let (Xn)1n=1, be a sequence of i.i.d. random variables distributed uniformly in [ 1; 1]. Show that the following sequences (Yn)1n=1 converge in probability to some limit.

Qn

(a) Yn = i=1 Xi.

(b) Yn = maxfX1; X2; : : : ; Xng.

(c) Yn = (X12 + + Xn2)=n.

4. Gambling Game

Let’s play a game. You stake a positive initial amount of money w0. You toss a fair coin. If it is heads you earn an amount equal to three times your stake, so you quadruple your wealth.


If it comes up tails you lose everything. There is one requirement though, you are not allowed to quit and have to keep playing, by staking all your available wealth, over and over again.

Let Wn be a random variable which is equal to your wealth after n plays.

Find E[Wn] and show that limn!1 E[Wn] = 1.

Since limn!1 E[Wn] = 1, this game sounds like a good deal! But wait a moment!! Where does the sequence of random variables fWngn 0 converge almost surely (i.e. with probability 1) to?

5. Soliton Distribution

This question pertains to the fountain codes introduced in Lab 2.

Say that you wish to send n chunks of a message, X1; : : : ; Xn, across a channel, but alas the

channel is a packet erasure channel: each of the packets you send is erased with probability pe > 0. Instead of sending the n chunks directly through the channel, we will instead send n packets through the channel, call them Y1; : : : ; Yn. How do we choose the packets Y1; : : : ; Yn? Let p( ) be a probability distribution on f1; : : : ; ng; this represents the degree distribution of the packets.

For i = 1; : : : ; n, pick Di (a random variable) according to the distribution p( ). Then,

choose Di random chunks among X1; : : : ; Xn, and \assign” Yi to the Di chosen chunks.

For i = 1; : : : ; n, let Yi be the XOR of all of the chunks assigned for Yi (the number of chunks assigned for Yi is called the degree of Yi).

Send each Yi across the channel, along with metadata which describes which chunks were assigned to Yi.

The receiver on the other side of the channel receives the packets Y1; : : : ; Yn (for simplicity, assume that no packets are erased by the channel; in this problem, we are just trying to understand what we should do in the ideal situation of no channel noise), and decoding proceeds as follows:

If there is a received packet Y with only one assigned chunk Xj , then set Xj = Y . Then, \peel o ” Xj : for all packets Yi that Xj is assigned to, replace Yi with Yi XOR Xj . Remove Y and Xj (notice that this may create new degree-one packets, which allows decoding to continue).

Repeat the above step until all chunks have been decoded, or there are no remaining degree-one packets (in which case we declare failure).

In the lab, you will play around with the algorithm and watch it in action. Here, our goal is to work out what a good degree distribution p( ) is.

Intuitively, a good degree distribution needs to occasionally have proli c packets that have high degree; this is to ensure that all packets are connected to at least one chunk. However, we need \most” of the packets to have low degree to make decoding easier. Ideally, we would like to choose p( ) such that at each step of the algorithm, there is exactly one degree-one packet.

(a) Suppose that when k chunks have been recovered (k = 0; 1; : : : ; N 1), then the expected number of packets of degree d (for d > 1) is fk(d). Assuming we are in the ideal situation where there is exactly one degree-one packet for any k : What is the probability that a


given degree d packet is connected to the chunk we are about to peel o ? Based on that, what is the expected number of packets of degree d whose degrees are reduced by one after the (k + 1)st chunk is peeled o ?

(b) We want fk(1) = 1 for all k = 0; 1; : : : ; n 1. Show that in order for this to hold, then

for all d = 2; : : : ; n we have fk(d) = (n k)=[d(d 1)]. From this, deduce what p(d) must

be, for d = 1; : : : ; n. (This is called the ideal soliton distribution.)

[Hint: You should get two di erent recursion equations since the only degree 1 node at peeling k + 1 is going to come from the peeling of degree 2 nodes at peeling k, however, for other higher degree d nodes, there will be some probability that some degree d ones will remain from the previous iteration and some probability that they will come from d + 1 one that will be peeled o ]

(c) Find the expectation of the distribution p( ).

In practice, the ideal soliton distribution does not perform very well because it is not enough to design the distribution to work well in expectation.
