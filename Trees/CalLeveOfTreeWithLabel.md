### Calculating the level of a label in binary tree.

## Formula
Level = Math.log(label)/Math.log(2) -> Gives the level of that label in the tree.

### Calcularing the index of a label in the bianry tree
## Formula 


## Problem Statement - 
> Given a label in the binary tree, such that nodes are zig zag fashion in every level, line
                 
            ->   1
               /    \    
              3      2  <-
            /   \   /   \
      ->   4     5  6    7 
Find the path of a given label from the root node to that label.


### Input 
14
### Output
[1 3 4 14]

```java
class Solution {
    public List<Integer> pathInZigZagTree(int label) {
        ArrayList<Integer> path = new ArrayList<>();
        int targetLevel = (int) (Math.log(label)/Math.log(2));
        int targetIndex;
        if(targetLevel%2 == 0)
            targetIndex = label-1;
        else
           targetIndex = 3 * (int) Math.pow(2, targetLevel) - (label+2);
        
        int parentIndex = targetIndex;
        int currLevel = targetLevel;
        int currlabel;
        for(int i = 0; i<targetLevel+1; i++) {
            path.add(0);
        }
        
        while(currLevel >= 0) {
            if(currLevel % 2 == 0)
                currlabel = parentIndex+1;
            else {
                currlabel = 3 * (int) Math.pow(2, currLevel) - (parentIndex+2);
            }
            path.set(currLevel, currlabel);
            parentIndex = (parentIndex -1) /2;
            currLevel--;
        }
        return path;
    }
}
```
