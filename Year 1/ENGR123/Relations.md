# Relations

Related: #relations #induction #terms 
Hamish Burke || 31-01-2023
***

## Terms

### AntiSymmetric

- if aRb and a≠b, then bRa must not hold'
- if (a,b), then it cannot be (b,a) (unless b=a)

### Partial Ordering

*A partially ordered relation must be:**
-   Reflexive
-   AntiSymmetric
-   Transitive

### Equivilence Relation

*Each class, is a partition of set A*
-   Transitive
-   Reflexive
-   Symmetric

***

## Proof by Induction

### Base case

*The induction step*
$P(1) -> P(k)$
$P(k) -> P(k+1)$

### Three Conditions:

-   The set of elements have to be infinite
-   Prove property for first element
-   If property true for the first (k) elements, can you prove it true of (k+1)?

### Assume P(k) is True:

$k^3 + 2k$ is divis by 3
$k^3 +2k = 3z$
$(k+1)^3 + 2(k+1)$ is divis by 3

*expand*
  
$k^3 + 3k^2 + 5k + 3$

$(k^3 + 2k) + (3k^2 + 3k + 3)$

$3z + 3(k^2 + k + 1)$

$3(z+k^2 + k + 1)$
