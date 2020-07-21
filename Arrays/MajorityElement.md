## Majority Element
### Problem Statement -
> Given an array, find the majority element index in the array. An element is said to be majority element, if it appears more than n/2 times in that array.

### Input formaat -
* 8 3 4 8 8 
* 1 2 4 2 1 1
* 30 40 50 50 50 50 50

### Output Format -
* 0 or 3 or 4
* -1 (No majority)
* 2 or 3 or 4 or 5 or 6

### Psuedocode -

Efficient Approch O(N) :
> This approach is called as **Moore's voting Algorithm**

> In this approach, there are two phases. In the first phase, it's finds out a candidate. If there was a majority element in the array, then this candidate is the majority element.

> In the second phase, we check whether this candidate is majority element or not. If it is gaurantee that the array will always contains a majority element then we dont need this second phase.

> This algorithm doesn't always give the first occurence of the majority element.
```C++
int majority(int ar[], int n){
    int res = 0, count = 1;
    //Finding the candidate
    for(int i = 1; i <n; i++){
        if(ar[res] == ar[i]){
            count++;
        }
        else count--;
        if(count == 0){
            res = i;
            count = 1;
        }
    }

    //Check if candidate is majority element
    count = 0;
    for(int i = 0; i<n; i++) {
        if(ar[i] == ar[res])
            count++;
    }
    if(count <= n/2) res=-1;
    return res;
}
```