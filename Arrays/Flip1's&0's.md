## Flip Consecutive 0's and 1's
### Problem Statement -
> Given a binary array, flip the minimum number of groups either 1 or 0 such that all the elements should equal.

### Input Format-
* 1 1 0 0 0 1
* 1 0 0 0 1 0 0 1 1 1 1
* 1 1 1

### Output Format -
* From 2 to 4
* from 1 to 3, From 5 to 6
* (empty)

### Psuedocode - 
> Before implementing, there is a interesting fact in this.

> The number of groups of 0's and 1's are either same or the difference btween both of them is 1
Let's see this:
* Group Counts differ by one:
    * 1 1 0 0 0 1 1 1 0 0 1
    > in this, the number of one's and zeores are differ by 1. If we add one more  0 at last then the difference is same.

    >And the case where we have all the zeros or all ones, it is also fall in this senario.
* Groups count are same:
    * 0 0 1 1 1 0 0 0 0 1 1
    > Here the countsare same
> To implement this approach, as our string can either start with zero or one.

> If starting we have a **1**, then the difference is one. If we add some **0's** the difference is zero. And again if we add **1's** the difference is one.And so on....

> Therefore, the string which has same starting and ending will have diffrence one. If begining and end are not same, then the difference is zero. Hence if we flip always the second group, then we get the minimum flips.

```Java
void flipBits(int ar[], int n) {
    for(int i = 1; i < n; i++) {
        if(ar[i] != ar[i-1]) {
            if(Ar[i] != ar[0])
                System.out.print("From "+i+" to");
            else
                System.out.println(i-1);
        }
    }
    if(ar[n-1] != a[0])
        System..out.println(n-1);
}
```

### Time Complexity - 
> O(N)