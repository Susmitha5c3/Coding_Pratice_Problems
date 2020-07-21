## Max appearing element.
### Problem Statement -
> Given an array of ranges, find the maximum apearing element in all the ranges.

### Input Format -
* 1 2 5 15 (left)
* 5 8 7 18 (right)
### Output Fromat -
* 5

### Constaints - 
0 <= L <= R <= 1000
### Psuedocode -
> If the ranges of L and R are given, then create a vector of that total range and increment the vector[l[i]] and decrement the vecotr[r[i]]. Then compute the prefix sum of that vector. Hence, we have the frequencey of every number in every index of vector.
``` Java
    static int MAX = 1000000;
    static int maximumOccuredElement(int[] L, int[] R, int n) 
	{ 
		// Initalising all element of array to 0. 
		int[] arr = new int[MAX]; 

		// Adding +1 at Li index and 
		// substracting 1 at Ri index. 
		int maxi=-1; 
		for (int i = 0; i < n; i++) { 
			arr[L[i]] += 1; 
			arr[R[i] + 1] -= 1; 
			if(R[i]>maxi){ 
			maxi=R[i]; 
		} 
		} 

		// Finding prefix sum and index 
		// having maximum prefix sum. 
		int msum = arr[0]; 
		int ind = 0; 
		for (int i = 1; i < maxi+1; i++) { 
			arr[i] += arr[i - 1]; 
			if (msum < arr[i]) { 
				msum = arr[i]; 
				ind = i; 
			} 
		} 

		return ind; 
	}
```