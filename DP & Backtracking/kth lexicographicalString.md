Problem Link = [KthLexicographical](https://leetcode.com/problems/the-k-th-lexicographical-string-of-all-happy-strings-of-length-n/)


``` Java
List<Integer> ans;
int ar[] = {'a','b','c'};
String subsets(String s, char c, int n) {
    if(n == len(s)){
        ans.add(s);
        return s;
    }
    s += c;
    for(int i = 0; i < 3; i++) {
        int len = s.length();
        if(len == 0){
            s += subsets(s, ar[i], n);
        }
        else if(len < n && s[len[s]-1] != ar[i])
            s += subsets(s, ar[i], n);
    }
    return s;
}
```
> Wrong Code........

```java

class Solution {
    List<String> ans = new ArrayList<>();
    char ar[] = {'a','b','c'};
    void subsets(String s, int n) {
       if(n == 0) {
           ans.add(s);
           return ;
       }
       for(int i = 0; i < 3; i++) {
           if(s.length() == 0 || s.charAt(s.length()-1) != ar[i]) {
               s += ar[i];
               subsets(s, n-1);
               s = s.substring(0, s.length()-1);
           }
       }
    }
    public String getHappyString(int n, int k) {
        subsets("", n);
        // System.out.println(ans.size());
        // for(int i = 0; i<ans.size(); i++)
        //     System.out.print(ans.get(i)+" ");
        if(ans.size() < k)
            return "";
        else
            return ans.get(k-1);
        // return "abc";
    }
    
}
```