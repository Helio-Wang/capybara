.. _Suboptimal enumeration:

**********************
Suboptimal enumeration
**********************

The input format is the same as for :ref:`Optimal enumeration` (see :ref:`Enumeration input`). 

Basic usage
-----------

Consider all reconciliations of a given input **ordered by cost** in a list, then the K-best solutions is the first K
element of this list.

Note that the ordering between solutions having the same cost is arbitrary.


K-best solution enumeration allows to obtain sub-optimal solutions if the number K is fixed to be larger
than the number of optimal solutions.


Example
-------

For :download:`this input file <resources/SFC.nex>` and cost vector (0,1,2,1), there are 40 solutions
having the optimal cost 21 (none of which is acyclic), and 396 solutions having the second-optimal cost 22 (146 are acyclic).

By fixing K = 100 (without filtering by cyclicity), the output will contain 100 solutions. The first 40 are the optimal
solutions, and the next 60 are chosen arbitrarily among the 396 second-optimal solutions. 

The choice of these 60 solutions are arbitrary, meaning that if the user closes and restarts the program,
the output may be different in spite of using exactly the same input.

If the cyclicity filter is applied, the output will contain a certain number of acyclic solutions: it's the number of acyclic solutions
among the 60 second-optimal solutions. This number varies each time the program restarts, and it might be zero.


