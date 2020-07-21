## Maximum Circular Subarray sum
### Problem Statment - 
> Find the maximum circular subarray sum.
### Input Format - 
* 5 -2 3 4
* 2 3 -4
* 3 -4 5 6 -8 7
* -8 7 6

### Output Format -
* 12
* 5
* 17
* 13

### Psuedocode -
1. Naive Solution O(N^2):
> we consider every element as the begining of the subarray and compute the sum.
```C++
int maxSum (int ar[], int n) {
    int res = ar[0];
    for(int i = 0; i < n; i++) {
        int curr_max = ar[i]; //Begining os the subarray.
        int curr_sum = ar[i];
        for(int j = 1; j < n ; j++) {
            int idx = (i+j) % 2;
            curr_sum += ar[idx];
            curr_max = max(curr_max, curr_sum);
        }
        res = max(res, curr_max);
    }
    return res;
}
```

2. Efficient Approach O(N) :
> Idea here is to first calculate the normal subarray sum by using kadane's algorithm. Then find the maxximum sum for the circular subarrays.

> For getting the maximum sum in circular subarrays, we can subtract the minimum sum from the total sum of the array. Thus we left with the maximum sum of the circular subarray.

> The minimum sum can be calculated by the same kadane's algorithm by shifting the sigins of the array elements.

```C++
int sumKadane (int ar[], int n) {
    int sum = ar[0] res = INT_MIN;
    for(int i = 0; i < n; i++) {
        sum = max(ar[i], sum+ar[i])
        res = max(res, sum);
    }
    return res;
}

int subarraySum (int ar[], int n){
    int maxSum = 0;
    maxSum = sumKadane(ar, n);
    if(maxSum < 0) return maxSum; //If array elements are negative
    int total_sum = 0
    for(int i = 0; i<n; i++) {
        total_sum += ar[i];
        ar[i] = -ar[i];
    }
    int circluar_sum = total_sum + sumKadane(ar, n); //As we reverse the sign of the elements. so,(+)
    return max(circular_sum, maxSum);
}
```