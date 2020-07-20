## MAx and Second Max
### Problem Statement - 
> Given an array **ar** of size **N**. Find the **first maximum** element and the **second maximum** element in the array. If there is no second maximum array **return -1**.
## Input Format -
* 3
* 5
* 1 2 3 4 5
* 3
* 2 1 2
* 2
* 5 5
## Output format - 
* 5 4
* 2 1
* 5 -1

> Return a vector containing the fist element as first maximum and second element as second maximum.
### Psuedocode -
```C++
vector<int> maxi(int ar[], int n) {
    int m1 = ar[0], m2 = INT_MIN;

    for(int i = 1; i < n; i++) {
        if(m1 != a[i])
            m2 = max(m2, min(m1, ar[i]));
        m1 = max(m1, ar[i]);
    }

    if(m2 == INT_MIN) m2 = -1;

    vector<int> v;
    v.push_back(m1);
    v.push_back(m2);
    return v;
}
```
### Time Complexity -
> O(N)