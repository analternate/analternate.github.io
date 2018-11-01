+++
title = "Introduction"
weight = 1
+++

### Game of Patience

```
Given a deck of cards, form as few piles as possible with the following rules
1. Can't place a higher-valued card onto a lowered-valued card.
2. Can form a new pile and put a card onto it.
``` 

### Solution
Greedy: Place each card on leftmost pile that fits, else, create new pile
Observation: At any stage, top piles increase from left to right

### Example
Given cards [10,9,2,5,3,7,8,9]

```python
import bisect

def patienceSort(cards):
    buckets = []

    for c in cards:
        if len(buckets) == 0 or c > buckets[-1][-1]:
            buckets.append([c])
            continue

        # Lazy way to do binary search. 
        # This makes the algorithm O(n^2) instead of O(nlgn) in reality
        # but for demonstration we use this instead
        idx = bisect.bisect_right([buckets[i][-1] for i in range(len(buckets))], c)
        buckets[idx].append(c)
    
    return buckets

print(patienceSort([10,9,2,5,3,7,8,9]))
## Prints: [[10, 9, 2], [5, 3], [7], [8], [9]]
```
Complexity: O(nlgn)

### Extending to LIS

Notice that the last element forms an LIS. To solve 

##### Refer: 
1. https://www.cs.princeton.edu/courses/archive/spring13/cos423/lectures/LongestIncreasingSubsequence.pdf
2. https://en.wikipedia.org/wiki/Patience_sorting
