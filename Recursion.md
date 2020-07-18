## 1. Josephus Problem (AMAZON)
[Problem Link](https://www.geeksforgeeks.org/josephus-problem-set-1-a-on-solution/)

___

## 2. Lucky Numebrs (Microsoft)
### Problem Statement - 
> Given a number. Check if it is lucky or not.
> **Lucky Number** - It is a subset of series of integers. Observe the following :
* Let's consider 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19,..................
* In first iteration
    * Remove the second integers
    * Result - 1, 3, 5, 7, 9, 11, 13, 15, 17, 19,..................
* In second iteration
    * Remove the third integers
    * Result - 1, 3, 7, 9, 13, 15, 19,...........
* And so on..
* The number which is in this series is the Lucky Numebr.
### Input Format - 
* 2
* 5
* 19
## Output Format - 
* 0 (True)
* 1 (False)

### Psuedocode - 
> Here we need to find the postion(P) of the numebr in every iteration. The counter / iteration(I) initially was given 2.
> If I > P then it is a lucky numebr. And also if the N divided by the counter(I) return false.

```C++
bool Lucky(int n, &counter) {
    int pos = n; //Initally pos is n.
    if( counter < I ) return 1;
    if( n % counter == 0) return 0;

    pos -= (pos / counter);
    counter++;

    return Lucky(pos, counter);
}

```
### Time Complexity - 
> O( sqrt(N) )
### Reference Link - 
[Lucky Numbers](https://www.geeksforgeeks.org/lucky-numbers/)

___
## 3. Power Of Numbers (makemytrip, walmart)
### Problem Statement - 
> Given a number N and reverse of it R. Compute power(N, R). The values are very big so return answer with modulo 1e9+7.
### Input Format -
* 2
* 2
* 12
### Output Format -
* 4
* 864354781

### Psuedocode -
> For pow(a,b) if b is even then the pow(a,b) = pow(a, b/2) * pow(a, b/2)

> For Pow(a,b) if b is odd, then the pow(a,b) = a * pow(a, b-1)

```C++
int M = 1000000007;
long long power(int N, int R) {
    if(R == 0) return 1;
    if(R % 2 == 0) 
        return ((power(N, R/2)) % M * (power(N, R/2)) % M) % M;
    else
        return (N * power(N, R - 1)% M) % M;
}
```

### Time Complexity - 
> O( LogN )

___
## 4. PowerSet of a string lexicographical
### Input Format -
* 2
* a
* abc
### Output Fromat - 
* a
* a ab abc ac b bc c
### Psuedocode -
```Java
    static ArrayList<String> set(String s, int idx, String curr, ArrayList<String> ans) {
        int n = s.length();
        if(idx == n) {
            ans.add(curr);
            return ans;
        }
        ans = set(s, idx+1, curr, ans);
        ans = set(s, idx+1, curr+s.charAt(idx), ans);
        return ans;
    }
    static ArrayList<String> powerSet(String s)
    {
        ArrayList<String> a = new ArrayList<>();
        a = set(s, 0, "", a);
        return a;
    }
```
### Time Complexity -
> O(2 ^ N)
