# **Surreal numbers and combinatorial games** 

A seminar series on Conway’s *On Numbers and Games* (ONAG) requires **10 sessions** (60–90 minutes each). This pace allows you to establish the construction of the Surreal Numbers $No$ in the first half, general Combinatorial Game Theory (CGT) in the second half, and explicitly study how surreal numbers sit embeddably inside the broader partially ordered group of Playing Games $Pg$.

## **Tentative Overview & Schedule**

| \# | Chapter | Primary Subject | Key Concepts |
| :---- | :---- | :---- | :---- |
| **1** | Ch. 0–1 | The Axioms of Surreal Numbers | Conway’s inductive construction \$x \= \\{L \\mid R\\}\$, order, basic arithmetic |
| **2** | Ch. 2–3 | Reals, Ordinals, and the Field $No$ | Dyadic rationals, Dedekind vs. Conway cuts, embedding $R$ and $On$ |
| **3** | Ch. 4–6 | Structure and Algebra of $No$ | Conway normal form, sign sequences, field operations, $x+y$ and $x\cdot y$ |
| **4** | Ch. 7 | Generalizing Numbers to Games | Dropping ${x}_{L}<{x}_{R}$, Left/Right options, outcomes ($P,N,L,R$) |
| **5** | Ch. 8–9 | Game Algebra & Canonical Forms | Equality/equivalence, domination, reversibility, simplifying games |
| **6** | Ch. 10 | Impartial Games & Sprague-Grundy | Impartial games as a sub-universe, nim-addition ($\oplus$), nim-values ($*n$) |
| **7** | Ch. 12 | Infinitesimal Partisan Games | Number Avoidance Theorem, Star ($*$), Up/Down ($\uparrow ,\downarrow$), all-small games |
| **8** | Ch. 11 | Temperature Theory & Thermography | Mean values, cooling/warming, temperature, thermographs, stop values |
| **9** | Ch. 13, 15 | Advanced Game Structures | Atomic weight, tinies/minies, coin-turning/nim-like variations |
| **10** | Ch. 14, 16 | Infinite Games & The Grand Synthesis | Transfinite games, loopy games, $No\subset Pg$ embedding theorem |

## **Detailed Session Breakdown**

### **Phase I: Surreal Numbers ($No$)**

#### **Session 1: The Construction of Surreal Numbers**

* **ONAG Chapters:** 0 & 1  
* **Topics:**  
  * Conway’s single unified construction rule: \$x \= \\{L \\mid R\\}\$ subject to \$x\_L \\nsim x\_R\$ (no left option is greater than or equal to any right option).  
  * Inductive definition of the partial order $\leq$ and equivalence $=$.  
  * Birthday construction: creation of numbers day by day starting from Day 0 (\$\\emptyset \\mid \\emptyset \= 0\$).  
  * Constructing integers ($Z$) and dyadic rationals ($Z[1/2]$) on finite days.

#### **Session 2: Embeddings of Reals ($R$) and Ordinals ($On$)**

* **ONAG Chapters:** 2 & 3  
* **Topics:**  
  * Transfinite days: infinite birthdays and the birth of $\omega$, $\epsilon =1/\omega$, $\pi$, and $\sqrt{2}$.  
  * Conway cuts vs. Classical Dedekind cuts (why Conway cuts yield a field without equivalence classes).  
  * Embedding the von Neumann ordinals $On$ directly into $No$.  
  * Sign sequences ($+/-$) as an alternative representation for surreal numbers.

#### **Session 3: Algebra and Arithmetic in $No$**

* **ONAG Chapters:** 4, 5 & 6  
* **Topics:**  
  * Inductive definitions of addition ($x+y$) and multiplication ($x\cdot y$).  
  * Proof sketch: $No$ forms a proper class field containing both real numbers and ordinal arithmetic.  
  * Conway Normal Form (expanding surreal numbers in terms of powers of $\omega$).  
  * Overview of the surreal field extension $O{n}_{2}$ (nim-arithmetic fields).

### **Phase II: The Transition from Numbers to Games ($Pg$)**

#### **Session 4: Dropping the Order Constraint**

* **ONAG Chapter:** 7  
* **Topics:**  
  * Defining a general game \$G \= \\{G\_L \\mid G\_R\\}\$ by dropping the condition ${x}_{L}<{x}_{R}$.  
  * Physical interpretation: Left moves to ${g}_{L}\in {G}_{L}$, Right moves to ${g}_{R}\in {G}_{R}$ under the normal play convention (last player to move wins).  
  * The four fundamental outcome classes:  
    * $G>0$ (Left wins regardless of who goes first)  
    * $G<0$ (Right wins regardless of who goes first)  
    * $G=0$ (Second player wins, $P$\-position)  
    * $G\parallel 0$ (First player wins, $N$\-position / confused with zero)

#### **Session 5: Equivalence and Canonical Forms**

* **ONAG Chapters:** 8 & 9  
* **Topics:**  
  * Group structure of games: disjunctive sum $G+H$ and negative $-G$.  
  * Partial order on games: \$G \\ge H \\iff G \- H \\ge 0\$.  
  * Simplification theorems:  
    * **Dominated options:** deleting redundant moves.  
    * **Reversible moves:** replacing moves that allow immediate counter-attacks.  
  * Uniqueness of the **canonical form** for finite short games.

### **Phase III: Combinatorial Game Theory & Special Classes**

#### **Session 6: Impartial Games and Sprague-Grundy Theory**

* **ONAG Chapter:** 10  
* **Topics:**  
  * Impartial games (${G}_{L}={G}_{R}$ for all subpositions).  
  * Nim and $nim$\-values (\$\*n \= \\{0, \*1, \\dots, \*(n-1) \\mid 0, \*1, \\dots, \*(n-1)\\}\$).  
  * Sprague-Grundy Theorem embedded in Conway's framework: every finite impartial game is equivalent to a single nim-heap $*n$.  
  * Nim-addition ($\oplus$) via bitwise XOR.

#### **Session 7: Partisan Infinitesimals & Numbers as Values**

* **ONAG Chapter:** 12  
* **Topics:**  
  * **Number Avoidance Theorem:** why players avoid moving in positions that are true numbers unless forced.  
  * Non-number games: Star (\$\* \= \\{0 \\mid 0\\}\$), Up (\$\\uparrow \= \\{0 \\mid \*\\}\$), and Down ($\downarrow =-\uparrow$).  
  * The order relationship: $0<\uparrow <\frac{1}{{2}^{n}}$ (a strictly positive game that is smaller than every positive number).  
  * Concept of *all-small games*.

### **Phase IV: Advanced Analysis & Structural Synthesis**

#### **Session 8: Temperature Theory and Thermography**

* **ONAG Chapter:** 11  
* **Topics:**  
  * Motivation: evaluating positions in hot games where players want to move to gain advantage.  
  * Cooling operator ${G}_{t}$ and the definition of **Temperature** $t(G)$ and **Mean Value** $m(G)$.  
  * Constructing and reading **Thermographs**.  
  * The Thermographic Theorem and optimal play in disjunctive sums of hot games.

#### **Session 9: Atomic Weight and Fine-Grained Infinitesimal Structure**

* **ONAG Chapters:** 13 & 15  
* **Topics:**  
  * Comparing infinitesimals: why $\uparrow$ dominates multiples of $*$.  
  * Definition of **Atomic Weight** $aw(G)$ for analyzing games composed of up-switches and star-like components.  
  * Tinies (${+}_{x}$) and Minies (${-}_{x}$): games that are smaller than all positive multiples of $\uparrow$.  
  * Applications to specific board games (e.g., Hackenbush, Domineering).

#### **Session 10: Transfinite/Loopy Games & The Grand Synthesis**

* **ONAG Chapters:** 14 & 16  
* **Topics:**  
  * Introduction to Infinite Games (transfinite play lengths) and Loopy Games (cycles, ties, stopper positions).  
  * **Synthesis:** The precise embedding $No\subset Pg$.  
    * Numbers are total orders inside the game partial order.  
    * Real numbers represent quiescent games, infinitesimals represent urgent local advantages, and non-numeric games represent tactical conflicts.  
  * Open problems and modern extensions in CGT.