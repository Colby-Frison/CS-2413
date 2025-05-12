Topics \\/
# Sorting
1. Non-comparison based
    1. Simple bucket sort = O(n + m)
    2. Radix sort = O(d * max(N,10))
2. Comparison based algorithm = Make assumption that elements are comparable
    1. Sorting by Ranking
        1. ranked by arbitrary number 1 - n each number goes through entire array finding its rank amongst all vals, once all vals have a rank the list is sorted
            1. Each val undergoes n-1 comparisons
        2. This doesn't take any swapping it inserts in a new array based on rank, hence its not an exchange algorithm
    2. Sorting by Exchanges
        1. Bubble sort O($n^2$﻿)
            1. compare n to n + 1, if n is bigger it swaps
                1. but after 1 run through the list can still be unsorted, so the method must be called essentially for every element which leads to the time complexity of $n^2$﻿
            2. Implementation is a nested loop that does the comparison for every element leading to O(n^2)
                1. To make it slightly faster a flag can be created with a Boolean flag that is made false upon a swap.
                2. This flag is connected to a while loop around the whole loop
                3. This makes it so that if no swap is made then it doesn't have to do any comparisons making it very fast
            3. Overall bubble sort is better as it does not have to create a new array
        2. Quick sort ⇒ O($n^2$﻿)
    3. Sorting by selection
	    1. Selection sort
	    2. Heap sort
    4. Sorting by insertion
        1. Insertion sort = O($n^2$﻿)
        2. Binary insertion sort = O($n^2$﻿)
        3. Using height balanced binary search tree = O(nlogn)
            1. [AVL, Red-Black]
    5. Sorting by merging
        1. Merge sort = O(nlogn)
    6. Sorting with BSTs