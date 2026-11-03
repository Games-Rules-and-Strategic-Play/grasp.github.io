**English** · [Slovenščina](cgt4tcs-sl.md)

<style>
.md-content__inner.md-typeset,
.md-content__inner.md-typeset :not(code, code *, pre, pre *, mjx-container, mjx-container *) {
    font-family: "Inter Tight", sans-serif !important;
}
.md-sidebar--secondary {
  display: block !important;
}
</style>

## Module 1: Some Combinatorial Games on Partitions

**Theoretical Computer Science I**

**FAMNIT, University of Primorska**

**Autumn 2026**

**Prof. Eric Gottlieb**[^1]

[^1]: These teaching modules were developed with the support of a Fulbright U.S. Scholar Award. The author extends his gratitude to the U.S. State Department, which sponsors the Fulbright program, to his host institution the University of Primorska, and to his home institution Rhodes College.

This semester, we will use combinatorial game theory to illustrate the topics we will be exploring in class. The idea is to help you see how the concepts we are studying are used by practicing mathematicians in their research. We will begin by learning about a few simple combinatorial games. Our goal in this module is to familiarize you with combinatorial games in an intuitive way. We will also mention some technical terms that will be defined more carefully in later modules, where we will explore some theoretical aspects of combinatorial games. Let's begin!

---

### Subtraction: a "simple" combinatorial game

Suppose you have a pile of 30 tokens. Two friends Peter and Nina take turns removing 1, 2, or 3 tokens from the pile. Nina goes first. The last player to pick up a token wins. Does one of the players have a winning strategy? If so, which one, and how should they play?

It's hard to see what's going on with so many tokens. Let's see if we can figure out what's going on when there are fewer tokens. If there's one token, Nina can win by taking one stone. In fact, she *must* win, since that's the only move available to her. If there are two tokens, Nina can take one or two of them. If she takes just one, then Peter can (and must) win by taking the last one. But if she takes two, then Nina wins. Obviously, Nina should take both tokens. Similarly, if there are three tokens, Nina should take all three, because if she takes one or two, then Peter can win by taking the remaining ones.

This illustrates an important point: when we say that Nina has a winning strategy when there are two tokens on the table, that doesn't mean that Nina wins no matter what she does. It means that no matter what Peter does, Nina has a path to victory. For this reason, our analysis will always assume perfect (i.e., errorless) play by both participants.

Let's consider what happens when there are four tokens. If Nina takes one, then Peter can win by taking three. If she takes two, then Peter wins by taking two. If she takes three, Peter wins by taking one. In other words, no matter what Nina does, Peter has a winning response. Thus, Peter has a winning strategy when there are four tokens.

Very well; our analysis shows that Nina has a winning strategy when there are one, two, or three tokens, while Peter can force a win if there are four tokens.

| $n$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **winner** | N | N | N | P |  |  |  |  |  |  |  |  |  |

With five tokens, things start to get a little more complicated. Clearly Nina shouldn't remove three tokens, because then Peter can win by taking two. Nor should she take two tokens, because then Peter can win by taking three. But what if she takes one token? In this case, Peter is in the very same position that Nina was in when there were four tokens — he has no winning move. In other words, Nina has left Peter in a losing position, so she has a winning strategy!

Now it's your turn.

**Exercise 1.** Work with your group to complete the following table by indicating which player has a winning strategy for the given number of tokens.

| $n$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **winner** | N | N | N | P | N |  |  |  |  |  |  |  |  |

**Exercise 2.** If you didn't make a mistake, there will be an obvious rule describing your answer to Exercise 1. Can you think of a way to prove that the rule holds for any positive number of tokens? What does your rule tell us about who has a winning strategy when there are 30 tokens?

There are a few things to notice about this game:

1. There's nothing special about the number 30; we could have started with any natural number of tokens.
2. We could change the rules by allowing players to remove, e.g., 2 or 5 tokens. Or, players could remove 1, 3, 4, or 6 tokens. In other words, there's nothing special about the numbers 1, 2, and 3; we could have used any set of positive integers we like as allowable moves. If we want a concise notation to denote such games, we could use $S_{\{1, 2, 3\}}$, $S_{\{2,5\}}$, and $S_{\{1, 3, 4, 6\}}$ for the three games mentioned above.
3. We assumed that both players were allowed to make the same moves. Such games are called *impartial*. By contrast, games in which the players have access to different moves are called *partizan*. For example, we could have stipulated that Peter can remove 1, 2, or 3 tokens, while Nina can remove 2 or 5 tokens. We could denote such a game by $S_{\{2,5\}, \{1, 2, 3\}}$. In this class, we will focus primarily on impartial games but may discuss partizan ones from time to time.
4. We could have changed the rules so that the last player to pick up a token loses. The original convention is called *normal play*; the second is called *misère play*. Both conventions are studied, but normal play has nicer theoretical properties as we will see. Our focus in this class will be primarily on normal play, but we may occasionally venture into misère territory.
5. In **Subtraction**, there is no way for the players to tie and no way for play to continue indefinitely, as there would be if players were allowed to place tokens on the pile in addition to removing them. Games in which play is guaranteed to conclude after a finite number of steps from any position are called *short*. In this class, we will focus exclusively on short games.
6. In **Subtraction**, we have seen that one of the players always has a winning strategy. This will be true for all of the games we will consider in this class.
7. In **Subtraction**, play continues until no tokens remain. A position from which no moves are possible is called a *terminal position*. In normal play, Peter automatically wins on any terminal position.

**Exercise 3.** Complete the following table for $S_{\{2,5\}}$.

| $n$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **winner** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

As we have seen, it can get a bit complicated to keep track of which player has the winning strategy. This is because Nina begins as the next player, but once she moves, Peter becomes the next player and Nina becomes the previous player. The analysis becomes simpler if we talk about a position as being winnable by the *next* player or the *previous* one, instead of by a particular person. A position winnable by the next (resp. previous) player is said to be an $\mathcal{N}$- (resp. $\mathcal{P}$-) position.

We conclude this section with an important observation that is useful for analyzing **Subtraction** or any other short impartial combinatorial game.

> **Observation 1.** $\mathcal{N}$-positions are precisely those with a move to a $\mathcal{P}$-position. $\mathcal{P}$-positions are precisely those with no move to a $\mathcal{P}$-position.

---

### Nim

In the game of **Nim**, we begin with several piles of tokens. Players take turns selecting one of the piles, then removing any positive number of tokens from that pile. We denote the position with $k$ piles in which the $j$-th pile contains $n_j$ tokens by $n_1/\ldots/n_k$.

**Nim** plays a critical role in the analysis of short impartial games. We will have more to say about this important game later; for now, we will just use it to practice our newly-acquired combinatorial game theory skills.

**Exercise 4.** Which player has a winning strategy in **Nim** on the following positions?

1. No piles, no tokens
2. One pile with $n$ tokens, where $n$ is a positive integer.
3. $1/2$
4. $1/2/3$
5. $n/n$, where $n$ is a positive integer.
6. $m/n$, where $m$ and $n$ are distinct positive integers.
7. $1/3/5/7$ is the classical opening position. Unless you are familiar with **Nim** strategy, it is hard to know whether it is a $\mathcal{P}$- or $\mathcal{N}$-position, but it would be good for you to think about it just so you get a sense of how difficult it is.

---

### Partitions and Young diagrams

In recent years, we[^2] have studied a variety of combinatorial games on integer partitions. In this class, you will learn about some of these games and how some of the topics you learn about in this class are used in studying them. Before we can describe the games, we need to talk about partitions and Young diagrams.

[^2]: Here "we" refers to Profs. Eric Gottlieb, Matjaž Krnc, and Peter Muršič, as well as several student collaborators from the University of Primorska and Rhodes College.

An *integer partition* (or simply, a *partition*) of a nonnegative integer $n$ is a way of writing $n$ as a sum of positive integers, without regard to the order of the summands. The summands are called the *parts* of the partition. Here are all of the partitions of the first six nonnegative integers:

| 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
|  | 1 | 2 | 3 | 4 | 5 |
|  |  | 1+1 | 2+1 | 3+1 | 4+1 |
|  |  |  | 1+1+1 | 2+2 | 3+2 |
|  |  |  |  | 2+1+1 | 3+1+1 |
|  |  |  |  | 1+1+1+1 | 2+2+1 |
|  |  |  |  |  | 2+1+1+1 |
|  |  |  |  |  | 1+1+1+1+1 |

Because partitions are not distinguished by the order of the parts, we can arrange them as we wish. We will use the canonical form in which the parts appear in nonincreasing order, as shown above. We use $p(n)$ to denote the number of partitions of the positive integer $n$. Thus


$$p(1) = 1 \quad p(2) = 2 \quad p(3) = 3 \quad p(4) = 5 \quad p(5) = 7$$


There is one partition of 0, namely the empty sum, so $p(0) = 1$.

**Exercise 5.** Find $p(6)$, $p(7)$, and $p(8)$.

The notation above is a bit cumbersome. To be more concise, we will replace each $+$ in a partition with a comma and enclose the result in square brackets. Thus, if $n = \lambda_1 + \cdots + \lambda_r$ is a partition, then we will write $\lambda = [\lambda_1, \ldots, \lambda_r]$. We say that $n$ is the *size* of $\lambda$ and write $\lambda \vdash n$. For example, the partition $5 + 4 + 4 + 1 + 1 + 1$ of size 16 would be written $[5,4,4,1,1,1]$. If we wish to be even more concise, we can use exponential notation to write the same partition as $[5,4^2,1^3]$. The unique partition of zero is denoted by $[\ ]$.

Even with this simplified notation, partitions can still be difficult to visualize. For this reason, we introduce *Young diagrams*, which are left-justified arrays of squares where the number of squares in the $j$-th row from the top is equal to the $j$-th part of the partition. For example, the Young diagram of the partition mentioned above appears in Figure 1. We use the terms "partition" and "Young diagram" interchangeably and denote the set of all partitions by $\mathbb{Y}$.

*Figure 1: The Young diagrams of $[5,4^2,1^3]$ and its conjugate $[6,3^3,1]$.*

Given a Young diagram $\lambda$ with $k$ rows, we can construct a new Young diagram $\lambda'$ with $k$ columns where the number of squares in the $j$-th column of $\lambda'$ is equal to the number of squares in the $j$-th row of $\lambda$ for each $j \in \{1, 2, \ldots, k\}$. We say that $\lambda'$ is the *conjugate* of $\lambda$. A partition is said to be *self-conjugate* if $\lambda' = \lambda$. The reader can verify that $(\lambda')' = \lambda$. Figure 1 shows the conjugate of $[5,4^2,1^3]$.

While many combinatorial objects are counted by tidy formulae, this is not the case for partitions. There are, however, very pretty correspondences between different classes of partitions. For example, the number of partitions of $n$ into odd parts is equal to the number of partitions of $n$ into distinct parts. A number of famous mathematicians have investigated properties of the set of partitions, including Hardy and Ramanujan, Euler, Rademacher, Sylvester, MacMahon, Dyson, and Ono.

---

### LCTR

Consider the combinatorial game **LCTR** played on $\mathbb{Y}$ in which players take turns removing either the Leftmost Column or Topmost Row of a given partition $\lambda$ until they reach the empty partition (which is terminal). University of Primorska student Jelena Ilić studied **LCTR** for her senior project.

**Exercise 6.** Which player has a winning strategy in **LCTR** on the following partitions?

1. $[\ ]$
2. $[1]$
3. $[c]$, where $c$ is a positive integer. A partition of this form is called a *row*.
4. $[1^r]$, where $r$ is a positive integer. A partition of this form is called a *column*.
5. $[c, 1^{r-1}]$, where $c$ and $r$ are positive integers. A partition of this form is called a *hook*.
6. $[c^r]$, where $c$ and $r$ are positive integers. A partition of this form is called a *rectangle*.
7. $[k, k-1, \ldots, 2, 1]$, where $k$ is a positive integer. A partition of this form is called a *staircase*.
8. $[5,4^2,1^3]$

**Exercise 7.** Show that, in **LCTR**, a partition $\lambda$ is in $\mathcal{P}$ if and only if $\lambda'$ is in $\mathcal{P}$.

A game with the property mentioned in Exercise 7 is said to be *conjugate-invariant*.

---

### CRIM

In **LCTR**, we are allowed to remove only the leftmost Column or the topmost row of a Young diagram. What if players can remove any row or column, with the stipulation that if the row or column removed is neither the first nor the last, then the remaining parts of the Young diagram are merged together? We refer to this game as **CRIM**, or *column-row impartial merge*; see Figure 2.

*Figure 2: The allowable moves in CRIM from $[5,4^2,1^3]$.*

**Exercise 8.** Which player has a winning strategy in **CRIM** on the following partitions?

1. $[\ ]$
2. $[1]$
3. $[c]$
4. $[1^r]$
5. $[c, 1^{r-1}]$
6. $[c^r]$
7. $[k, k-1, \ldots, 2, 1]$
8. $[5,4^2,1^3]$

**Exercise 9.** Is **CRIM** conjugate-invariant? Why or why not?

---

### Corners

A square of a Young diagram is called a *corner* if there is no square below it or to its right. In the game **Corners**, players take turns removing a nonempty subset of the corners of a partition; see Figure 3.

*Figure 3: The corners of $[5,4^2,1^3]$ are shaded. Moves correspond to removing a nonempty subset of the corners.*

**Exercise 10.** Which player has a winning strategy in **Corners** on the following partitions?

1. $[\ ]$
2. $[1]$
3. $[c]$
4. $[1^r]$
5. $[c, 1^{r-1}]$
6. $[c^r]$
7. $[k, k-1, \ldots, 2, 1]$
8. $[5,4^2,1^3]$

**Exercise 11.** Is **Corners** conjugate-invariant? Why or why not?


## Module 2

In the last module, you learned about some simple combinatorial games. In this module, we will see how some of the proof techniques we will study can be used to prove theorems about these games. As we will see, induction is particularly powerful in this context, as it is throughout combinatorics. 

When playing a game it is helpful to know what the $\p$-positions are, since these are the ones you want to leave to your opponent. If you know them, then you can investigate whether any of your moves result in such a position. Remember that $\n$-positions are precisely those with a move to a $\p$-position, while $\p$-positions are those positions with no such move; you will use this in the exercises below.

In some games, it's not too hard to characterize the losing positions. For example, in $S_{\{1, 2, 3\}}$, we saw strong evidence (but not proof -- stay tuned) that the losing positions are precisely those heaps for which the number of tokens is divisible by four. For Nim and LCTR, such a characterization is possible but a bit involved. However, some more restricted results can be obtained without too much effort. 

### Losing Positions in $S_{\{1, 2, 3\}}$

Recall that in $S_{\{1, 2, 3\}}$, players take turns removing 1, 2, or 3 tokens from a single heap. Now you have the tools to prove our conjecture that the losing positions in normal-play $S_{\{1, 2, 3\}}$ are precisely those for which the number of tokens in the heap is divisible by four.  

**Exercise 1:** Use induction to prove that a position in normal-play $S_{\{1, 2, 3\}}$ is losing if and only if the number of tokens in the heap is a multiple of four. 

### Some results on Nim

Recall that in Nim there are a positive number of heaps of tokens. Players alternate choosing a heap and removing a positive number of tokens. We begin with some simple results for normal-play Nim. These can be established by direct proof. 

**Exercise 2:** Let $n \in \mathbb Z_{>0}$. Prove that in normal-play Nim, $n$ is in $\n$. 

**Exercise 3:** Let $n \in \mathbb Z_{>0}$. State and prove a necessary and sufficient condition for $1/n$ to be in $\p$ in normal-play Nim. 

**Exercise 4:** Prove that in normal-play Nim, $2/2$ is in $\n$. 

**Exercise 5:** Let $n \in \mathbb Z_{>0}$. State and prove a necessary and sufficient condition for $2/n$ to be in $\p$ in normal-play Nim. 

Next we consider some problems that require the use of induction. 

**Exercise 6:** State a conjecture characterizing the two-heap positions in normal-play Nim that are in $\p$. 

**Exercise 7:** Use induction to prove your conjecture from Exercise 6. 

**Exercise 8:** State a conjecture for normal-play Nim giving a sufficient condition for a position with an even number of heaps to be in $\p$. 

**Exercise 9:** Use induction to prove your conjecture from Exercise 8. 

**Exercise 10:** Is the condition in your conjecture from Exercise 8 also necessary for membership in $\p$? Explain.  

### Some Results on LCTR

Recall that LCTR is a game on partitions in which the players take turns removing either the leftmost column or topmost row of the corresponding Young diagram. We will consider some results that can be established directly, but first we need some terminology. 

A *row* is a partition of the form $[c]$, where $c \in \mathbb Z_{>0}$. A *column* is a partition of the form $[1^r]$, where $r \in \mathbb Z_{>0}$. A *hook* is a partition of the form $[c, 1^{r-1}]$, where $c \in \mathbb Z_{>0}$ and $r \in \mathbb Z_{>0}$. Notice that if $r=1$ then $[c, 1^{r-1}]$ is a row and if $c = 1$ then $[c, 1^{r-1}]$ is a column. We say that the hook $[c, 1^{r-1}]$ is *nondegenerate* if $c>1$ and $r>1$. 

**Exercise 11:** Formulate and prove results about the $\p/\n$-status in normal-play LCTR of rows, columns, and nondegenerate hooks. 

Next, we'll explore some examples in LCTR where induction is helpful. A *rectangle* is a partition of the form $[c^r]$, where $c \in \mathbb Z_{>0}$ and $r \in \mathbb Z_{>0}$. A *staircase* is a partition of the form $[n, n-1, \ldots, 2, 1]$ where $n \in \mathbb Z_{>0}$. 

**Exercise 12:** Formulate and prove characterizations of the $\p/\n$-status of rectangles and staircases in normal-play LCTR. 

**Exercise 13:** Formulate and prove a characterization of the $\p/\n$-status of partitions with two parts in normal-play LCTR. 

The next two exercises (and maybe the previous ones too) will be easier with some examples in front of you. I'll be happy to share some Mathematica code with you, or to run examples for you, to generate some data. You should have access to Mathematica through UP. 

**Exercise 14:** Formulate and prove a result about the $\p/\n$-status of self-conjugate partitions in normal-play LCTR. 

**Exercise 15:** Generalize your result, or part of it, from Exercise 14 to partitions that are not self-conjugate. 

### Some results on CRIM

Recall that in CRIM, players take turns removing a single row or column from the Young diagram of a partition. If the row or column is neither the first nor the last, then the two parts of the Young diagram are merged. We begin with a result for normal-form CRIM that can be proved directly. 

**Exercise 16:** State and prove a characterization for the $\p/\n$-status of rows and columns in normal-form CRIM. 

The remaining results require induction. 

**Exercise 17:** State and prove a characterization for the $\p/\n$-status of rectangles in normal-form CRIM. 

**Exercise 18:** State and prove a characterization for the $\p/\n$-status of nondegenerate hooks in normal-form CRIM.

**Exercise 19:** Formulate a conjecture for the $\p/\n$-status of staircases in normal-form CRIM.

### Some results on Corners

Recall that in Corners, players alternate removing nonempty sets of corners from the Young diagram of a partition. 

**Exercise 20:** Use data to formulate a conjecture characterizing the $\p/\n$-status of two-row partitions in normal-form Corners. 

**Exercise 21:** Use induction to prove your conjecture from Exercise 20. 

**Exercise 22:** Use data to formulate a conjecture characterizing the $\p/\n$-status of hooks in normal-form Corners. 

**Exercise 23:** Use induction to prove your conjecture from Exercise 22. 

### Conclusion
We have seen that various proof techniques can be used to better understand how to play combinatorial games and win. This is just the tip of the iceberg as there are many other combinatorial games and additional proof techniques that are used in their study.
