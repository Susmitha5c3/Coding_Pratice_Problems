## Subarray Sum with k
### Problem Statement -
> Given an array and K, return the indices of subarray which has sum K.

### Input Format -
* 5 12
* 1 2 3 7 5
* 10 15
* 1 2 3 4 5 6 7 8 9 10
 ### Output Format - 
 * 2 4
 * 1 5
 ### psuedocode -
 ```java
 public static int subarraySum(int ar[], int s, int n){
        int sum = ar[0], st = 0;
        for(int i = 1; i<=n; i++){
            while(sum > s && st < i-1) {
                sum = sum - ar[st];
                st++;
            }
            if(sum == s){
                System.out.println((st+1)+ " "+i);
                return 0;
            }
            if(i < n){
                sum += ar[i];
            }
        }
        return -1;
    }
 ```