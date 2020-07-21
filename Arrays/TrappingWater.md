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