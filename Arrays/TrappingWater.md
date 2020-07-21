## Traping Rain water
### Problem Statement -
> Given the heights of the bar. Find how much ammount of water we can collect between those bars.
### Input Format - 
* 2 0 2
* 3 0 1 2 5
* 1 2 3
* 3 2 1
### Output Format -
* 2
* 6
* 0
* 0
### Psuedocode -
1. Naive Solution O(N^2):
> Here, if we try to store water on the leftmost bar, the water doesn't store as it don't have support. Similarly for the rightmost bar. So we are travising from the bars between the leftmost and the right most.

> The ammount of water stored between the middle bars is inbetween the highest bar in its left and the highest bar in its right. So for every ith bar we need to find the max bar from its left and max bar from its right.
> The result we be **min(left-max, right-max) - ar[i]**.

```C++
int getWater(int ar[], int n) {
    int total = 0
    for(int i = 1; i < n-1; i++) {
        int lmax = 0;
        for(int j = 0; j < i; j++) {
            lmax = max(lmax, ar[j]);
        }
        int rmax = 0;
        for(int j = i + 1; j < n-1; j++) {
            rmax = max(rmax, ar[j]);
        }
        total += min(lmax, rmax) - ar[i];
    }
    return total;
}
```
2. Efficient Solution O(N) :
> From the brute force, we observed that at every position i, we need the lmax and the right max. We somehow store these lmax and the right max then we can simple find the total water in one iteration.
```C++
int getWater(int ar[], int n) {
    int lmax[n];
    lmax[0] = ar[0];
    for(int i = 1; i < n; i++) {
        lmax[i] = max(ar[i], lmax[i-1]);
    }
    int rmax = ar[n-1], total = 0;
    for(int i = n-2; i > 0; i--) {
        rmax = max(ar[i], rmax);
        total += min(lmax[n-i-1], rmax) - ar[i];
    }
    return total;
}
```