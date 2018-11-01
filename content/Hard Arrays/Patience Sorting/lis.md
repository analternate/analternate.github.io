+++
title = "Longest Increasing Subsequence"
weight = 1
+++

### Extending to Longest Increasing Subsequence (LIS)
> ## Prints: [[10, 9, 2], [5, 3], [7], [8], [9]]

Notice that the last element forms an LIS. To solve LIS, we simply take the last element of each bucket

We could also omit using a bucket and use a single number (last number) instead

### LIS
Given numbers [10,9,2,5,3,7,8,9]

```python
import bisect

def lis(numbers):
    buckets = []

    for c in numbers:
        if len(buckets) == 0 or c > buckets[-1]:
            buckets.append(c)
            continue

        idx = bisect.bisect_left(buckets, c)
        buckets[idx] = c
    
    return buckets

print(patienceSort([10,9,2,5,3,7,8,9]))
## Prints: [[10, 9, 2], [5, 3], [7], [8], [9]]
```
Complexity: O(nlgn)
