# Heap sort

- Insert each element into a min heap
    - n * logn complexity
- perform “delete min” n times
    - n * logn complexity

  

- heap sort is O(n*logn)

---

Given n elements one can contract a min deap in O(n*logn) by inserting one element at a time.

==Heapify Algorithm can construct a min heap in O(n) time==

  

heap sort will not be on the exam

# Sorting
1. Non-comparison based
    1. Simple bucket sort = O(n + m)
    2. Radix sort = O(d * max(N,10))
2. Comparison based algorithm = Make assumption that elements are comparable
    1. Sorting by Ranking
        1. ranked by arbitrary number 1 - n each number goes through entire array finding its rank amongst all vals, once all vals have a rank the list is sorted
            - Each val undergoes n-1 comparisons
        2. This doesn't take any swapping it inserts in a new array based on rank, hence its not an exchange algorithm
    2. Sorting by Exchanges
        1. Bubble sort O($n^2$﻿)
            - compare n to n + 1, if n is bigger it swaps
                - but after 1 run through the list can still be unsorted, so the method must be called essentially for every element which leads to the time complexity of $n^2$﻿
	        -  Implementation is a nested loop that does the comparison for every element leading to O(n^2)
	            -  To make it slightly faster a flag can be created with a Boolean flag that is made false upon a swap.
                -  This flag is connected to a while loop around the whole loop
                -  This makes it so that if no swap is made then it doesn't have to do any comparisons making it very fast
            -  Overall bubble sort is better as it does not have to create a new array
        2. Quick sort ⇒ O($n^2$﻿)
    3. Sorting by selection
	    1. Selection sort
	    2. Heap sort
    4. Sorting by insertion
        1. Insertion sort = O($n^2$﻿)
        2. Binary insertion sort = O($n^2$﻿)
        3. Using height balanced binary search tree = O(nlogn)
            -  [AVL, Red-Black]
    5. Sorting by merging
        1. Merge sort = O(nlogn)
	        - Requires extra array so time complexity is good but space is bad
    6. Sorting with BSTs
	    1. worst case  = O(nlogn)

Non-contructu proof

## Decision tree
$x_1$, $x_2$, $x_3$

$3!$ permutations; so 6 permutations ( orders)

