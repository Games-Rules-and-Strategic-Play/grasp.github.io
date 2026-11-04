# Research Problems for Students: New Games on Young Diagrams




This page turns the partition games in the [TCS games notes](cgt4tcs.md) into small, well-defined research projects. The games below are deliberately close to **Corners**, **LCTR**, and **CRIM**, but each changes one rule in a way that creates new questions. They are proposed directions rather than claims about what is already known.

All games use normal play: the player with no legal move loses. They are impartial, and every move deletes at least one square, so play always ends. As usual, a position is a $\mathcal P$-position when the previous player can force a win, and an $\mathcal N$-position otherwise. For a finer question, compute the Grundy value $g(\lambda)$: it is the least nonnegative integer missing from the Grundy values of all positions reachable from $\lambda$. In particular, $g(\lambda)=0$ exactly for $\mathcal P$-positions.

## A shared piece: terminal rectangles

Write a nonempty partition in plateau form

$$
\lambda=[w_1^{h_1},w_2^{h_2},\ldots,w_t^{h_t}],
\qquad w_1>w_2>\cdots>w_t>0.
$$

Let $s_i=h_1+\cdots+h_i$, let $s_0=0$, and set $w_{t+1}=0$. With rows numbered from top to bottom and columns from left to right, define the $i$-th **terminal rectangle** by

$$
B_i=\{(r,c):s_{i-1}<r\le s_i,\quad w_{i+1}<c\le w_i\}.
$$

It has height $h_i$, width $w_i-w_{i+1}$, and its southeast cell $(s_i,w_i)$ is one outer corner of $\lambda$. This is a precise, non-overlapping meaning of a “block” or terminal rectangle; after every move, the terminal rectangles are recomputed.

For example, $[5,4^2,1^3]$ has terminal rectangles of sizes $1\mathbin\times1$, $2\mathbin\times3$, and $3\mathbin\times1$. The middle one occupies rows 2–3 and columns 2–4. Removing it leaves $[5,1^5]$.

## 1. Block Corners

**Positions.** All integer partitions, including the empty partition $[\ ]$.

**Move.** Choose any nonempty collection of current terminal rectangles and delete every selected rectangle.

**Terminal position.** The empty partition.

Deleting $B_i$ changes the corresponding plateau of rows from length $w_i$ to length $w_{i+1}$; deleting several blocks still leaves a Young diagram. This is a block variant of **Corners**: a move may affect several boundary features at once, but it does so through whole terminal rectangles rather than individual squares.

### A guided benchmark

Let $d(\lambda)=t$ be the number of distinct positive parts of $\lambda$. If the selected blocks form $r$ consecutive runs in the index list $1,\ldots,t$, then the resulting partition has $d(\lambda)-r$ distinct parts. Conversely, every

$$
1\le r\le \left\lceil\frac{d(\lambda)}2\right\rceil
$$

can occur. Thus the outcome depends only on $d(\lambda)$ and reduces to the one-dimensional move rule

$$
t\longrightarrow t-r,\qquad 1\le r\le\left\lceil\frac t2\right\rceil.
$$

**First theorem to prove.** The $\mathcal P$-positions are precisely the partitions with

$$
d(\lambda)=2^k-2 \qquad (k\ge1).
$$

So the empty partition, and every partition with $2,6,14,\ldots$ distinct parts, is a losing position. This is a useful calibration project: it gives a first proof and a way to check a program before changing the rules.

### Research directions

- Find a closed description of the full Grundy sequence for the reduced game on $t$ distinct parts.
- Restrict legal blocks by area—for example, allow only $|B_i|\in S$ for a fixed set $S$—and determine when the actual widths and heights begin to matter.
- Analyze the misère version, or require exactly a prescribed number of terminal rectangles in each move.

## 2. Domino Corners

**Positions.** All partitions.

**Move.** Choose one terminal rectangle. Remove exactly one domino flush with its southeast corner: either the two rightmost cells in its bottom row (when its width is at least 2), or the two bottom cells in its rightmost column (when its height is at least 2).

**Terminal positions.** The staircases $[k,k-1,\ldots,2,1]$, including $[\ ]$ when $k=0$.

The terminal-position claim is a good first exercise. A horizontal domino is available exactly when some terminal rectangle has width at least 2; a vertical one is available exactly when some terminal rectangle has height at least 2. Hence no move is possible precisely when every plateau has height 1 and successive part sizes differ by 1.

### Research directions

- Classify $\mathcal P$-positions among hooks $[c,1^{r-1}]$, two-row partitions, or rectangles.
- For fixed $m$, tabulate the outcomes of $[n,m]$ as $n$ grows. Is there a recurrence or eventual pattern?
- Compare normal and misère play. Since a terminal position need not be empty, the parity of the total number of squares alone does not decide the winner.
- Prove or disprove conjugate invariance by matching horizontal and vertical domino moves under transposition.

## 3. Rectangle Corners

**Positions.** All partitions.

**Move.** Choose a terminal rectangle $B_i$ of height $h_i$ and width $w_i-w_{i+1}$. Choose

$$
1\le a\le h_i,\qquad 1\le b\le w_i-w_{i+1},
$$

then remove the $a\mathbin\times b$ rectangle whose southeast cell is the southeast corner of $B_i$.

**Terminal position.** The empty partition.

The condition on $a$ and $b$ guarantees that the shortened rows still form a partition. At the level of individual moves, this includes one-corner moves ($1\mathbin\times1$), Domino Corners moves, and deletion of an entire terminal rectangle.

### Research directions

- Prove that transposition sends an $a\mathbin\times b$ move to a $b\mathbin\times a$ move. Deduce that conjugate partitions have the same Grundy value.
- Prove $g([n])=g([1^n])=n$, then investigate the values of rectangles $[c^r]$.
- Determine the $\mathcal P$-positions among hooks and two-row partitions. Are Grundy values unbounded when the number of rows is fixed?
- Compare the one-rectangle rule with the variant that permits several rectangles based at different corners in the same move.

## 4. Two ways to change the selection rule

### Interval Corners

List the current corners from top to bottom as $q_1,\ldots,q_m$.

**Move.** Choose $1\le i\le j\le m$ and remove the consecutive interval of corners $q_i,q_{i+1},\ldots,q_j$.

This is a local version of **Corners**, which permits an arbitrary nonempty set of corners. Transposition reverses the corner order, so Interval Corners is conjugate-invariant.

**Research directions.** Classify positions with two or three distinct part sizes; determine the Grundy values of hooks and staircases; and study the parameterized rule in which an interval may contain at most $k$ corners.

### Diagonal Corners

Give a cell $(i,j)$ its anti-diagonal rank $i+j$.

**Move.** Choose a rank represented by at least one current corner, then remove every current corner of that rank.

For example, the corners $(1,5)$ and $(3,3)$ of $[5,3^2,1]$ both have rank 6, so they must be removed together when rank 6 is chosen. Transposition preserves rank, hence this game is also conjugate-invariant.

**First calculation.** Every corner of the staircase $[n,n-1,\ldots,1]$ has rank $n+1$. Its only move is therefore to the next smaller staircase, so its Grundy value is $0$ for even $n$ and $1$ for odd $n$.

**Research directions.** Determine the values on hooks and two-row partitions; test whether the multiset of corner ranks determines the Grundy value; and compare this rule with the variant allowing a nonempty subset of one rank class.

## Turning a game into a student project

Start with one game and one family of shapes, rather than trying to classify everything at once. A productive sequence is:

1. Enumerate partitions of small size and compute $\mathcal P/\mathcal N$ status or Grundy values recursively.
2. Organize the data by a structural parameter: number of distinct parts, width, height, hook arm and leg, or number of corners.
3. State a precise conjecture and actively search for its first counterexample.
4. Turn a persistent pattern into a proof, usually by induction on the number of cells or by pairing moves under transposition.

A successful short project can consist of a precise rule, reproducible small data, a proved theorem for one family of partitions, and a sharply stated next conjecture. The Block Corners theorem is a proof-first starting point; Domino Corners and Rectangle Corners are especially suitable for moving from experiments to new conjectures.
