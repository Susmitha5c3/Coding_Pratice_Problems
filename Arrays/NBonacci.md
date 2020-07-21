## N-bonacci numebrs.
### Problem Statement -
> Print first **m** N-bonacci numbers. Fibnonacci means 2 - bonacci numbers. Such that print N - bonacci numbers.
For all the series, first N-1 elements are zero and Nth element is 1.

### Input Format -
* n m
* 3 8
* 4 10
### Output format - 
* 0 0 1 1 2 4 7 13
* 0 0 0 1 1 2 4 8 15 29

### Psuedocode - 
```Java
	static void bonacciseries(int n, int m) 
	{ 
	
		// Assuming m > n. 
		int a[] = new int[m]; 
		for(int i = 0; i < m; i++) 
			a[i] = 0; 
			
		a[n - 1] = 1; 
		a[n] = 1; 
	
		// Uses sliding window 
		for (int i = n + 1; i < m; i++) 
			a[i] = 2 * a[i - 1] - a[i - n - 1]; 
	
		// Printing result 
		for (int i = 0; i < m; i++) 
			System.out.print(a[i] + " "); 
	} 
```