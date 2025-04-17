1. the schedule is not conflict-serializable
- T1's WRITE(A) (6) conflicts with T2's READ(A) (10)
- T2's WRITE(B) (5) conflicts with T1's READ(B) (7) </br>
These conflicts form a cycle in the precedence graph (T1→T2→T1) making it non-serializable

2. Reordered confict-serializable schedule: </br>
REAR(A) by T1  </br>
A = A + 100 by T1 </br>
WRITE(A) by T1 </br>
REAR(B) by T1 </br>
B = B - 50 by T1 </br>
WRITE(B) by T1 </br>
REAR(B) by T2 </br>
B = B + 200 by T2  </br>
WRITE(B) by T2  </br>
REAR(A) by T2 </br>
A = A - 150 by T2 </br>
WRITE(A) by T2 </br>
