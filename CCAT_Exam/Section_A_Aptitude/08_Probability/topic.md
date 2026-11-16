# Topic: Probability
# Section A — Aptitude

---

## What to Read
https://www.geeksforgeeks.org/probability/
https://www.indiabix.com/aptitude/probability/

---

## Core Formulas

P(Event) = Number of favorable outcomes / Total outcomes
P(A) lies between 0 and 1 (both inclusive)
P(A) + P(not A) = 1

---

## STEP 1: Basic Probability

Sample space = all possible outcomes
Event = set of outcomes we care about

Example: Die has 6 faces → sample space = {1,2,3,4,5,6}
P(rolling a 4) = 1/6
P(rolling even) = 3/6 = 1/2

Card deck: 52 cards total
- 4 suits (Hearts, Diamonds, Clubs, Spades)
- 13 cards per suit (A,2,3,...10,J,Q,K)
- Face cards (J,Q,K) = 12 total

---

## STEP 2: Addition Rule

P(A OR B) = P(A) + P(B) - P(A AND B)

Mutually exclusive events (cannot happen together):
P(A AND B) = 0
P(A OR B) = P(A) + P(B)

Example: P(rolling 2 or 4) = 1/6 + 1/6 = 2/6 = 1/3

---

## STEP 3: Multiplication Rule

Independent events (one doesn't affect the other):
P(A AND B) = P(A) × P(B)

Example: Tossing a coin twice:
P(Head both times) = 1/2 × 1/2 = 1/4

Dependent events: P(A AND B) = P(A) × P(B|A)
where P(B|A) = probability of B given A happened

---

## STEP 4: Complement Rule

P(at least one) = 1 - P(none)

Example: P(at least one head in 3 coin tosses)
= 1 - P(no heads) = 1 - (1/2)³ = 1 - 1/8 = 7/8

---

## STEP 5: Coin / Die / Card Examples

Coin toss outcomes: H, T → P(H) = 1/2
Two coins: HH, HT, TH, TT → 4 outcomes
Three coins: 8 outcomes → P(2 heads) = 3/8

Single die: 6 outcomes
P(prime number) = P(2,3,5) = 3/6 = 1/2
P(>4) = P(5,6) = 2/6 = 1/3

Two dice: 6×6 = 36 outcomes
P(sum=7) = {(1,6),(2,5),(3,4),(4,3),(5,2),(6,1)} = 6/36 = 1/6
P(sum=2) = {(1,1)} = 1/36

---

## Practice Links

IndiaBIX Probability:
https://www.indiabix.com/aptitude/probability/

GFG Probability Basics:
https://www.geeksforgeeks.org/probability/

---

## Target
Do 25 probability questions on IndiaBIX.
