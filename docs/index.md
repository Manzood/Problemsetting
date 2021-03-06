---
layout: default
---


### Editorial for problem D) Watson's Sorting Challenge

[Link to problem](https://www.hackerrank.com/contests/wtp-2021/challenges/d-a-harder-problem)

This is probably only slightly more advanced than the initial method, because it requires a more solid understanding of the programming language, but as a result, it is also more efficient.

The key thing we can do is pair the values we recieve as input with the initial index.
For example, if we recieve the following array in input: [5, 10, 40, 30, 20], the resultant array that we store would look something like this:

        [ [5, 0], [10, 1], [40, 2], [30, 3], [20, 4] ]

This can be implemented using either a 2D array or std::pair in C++.

Now, if we sort with the first index of each element in the array as a key value, We can move the elements into ascending order while retaining their original indexes.
Continuing the above example, the array after sorting would look something like this:

        [ [5, 0], [10, 1], [20, 4], [30, 3], [40, 2] ]

Now all there's left to do is traverse through the array, and update it in our array, using the following step:

        ans[ a[i][1] ] = i

Time Complexity: O(n\*log(n)), because sorting in this case would have O(n\*log(n)) Time Complexity.


#### Code (C++):

```c++
#include "bits/stdc++.h"
using namespace std;

int32_t main () {
    int n;
    scanf("%d", &n);
    vector <pair <int, int>> a(n);
    vector <int> ans(n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &a[i].first);
        a[i].second = i;
    }
    sort(a.begin(), a.end());
    for (int i = 0; i < n; i++) {
        ans[a[i].second] = i;
    }
    for (int i = 0; i < n; i++) {
        printf("%d ", ans[i]);
    }
    printf("\n");
}
```
