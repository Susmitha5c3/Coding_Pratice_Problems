## Count Repeated Numbers
### Problem Statement - 
> Given a sorted array with one element repeated. Find the repeated element and number of times it is repeating.
### Input Format - 
* 5
* 1 2 3 3 4
* 5
* 2 3 4 5 5
### Output Format -
* 3 2
* 5 2

### Psuedocode -
> For finding the number of times the number is repeated we can calculate by **N - (arr[N-1] - arr[0])**. To find th element we need to do binary search.
```C++
int c = n-(arr[n-1] - arr[0]);
    int num;
    int hi = n-1, lo = 0;
    while(lo < hi) {
        int m = (lo+hi)/2;
        if(arr[m] >= m+arr[0]){
            lo = m +1;
        }
        else 
            hi = m;
    }
    num = arr[lo];
    pair <int, int> ans;
    ans.first = num;
    ans.second = c;
    return ans;
```