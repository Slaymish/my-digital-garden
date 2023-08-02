# Simplifying Logic Circuits Pract

Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 10-03-2023
***
$$Z = ABC + A*not(B)*(not(not(a)*not(c)))$$

## To Simplify the given Boolean Expression, We Can Use the following Rules:

1. Double Negation Law:  
   not(not(A)) = A
   
2. De Morgan's Law:  
   not(A*B) = not(A) + not(B)  
   not(A+B) = not(A)*not(B)  

Using these rules, we can simplify the given expression as follows:

Z = ABC + A*not(B)*(not(not(A)*not(C)))  (Given expression)

Z = ABC + A*not(B)*(A + C)              (Using Double Negation Law)

$Z = ABC + A*not(B)*A + A*not(B)*C$   
(Using Distributive Law)

$Z = ACB + A*not(B)*C$            (Using Associative Law)

$Z = A(CB + not(B)C)$                    (Using Distributive Law)

$Z = A(C + not(B))$                      (Using De Morgan's Law)

Therefore, the simplified boolean expression is: 

$$Z = A(C + not(B))$$