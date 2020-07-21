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

1. Efficient Approch O(N) :
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

2. Using Binary Search Tree :
> Enter every element of the array in the binary search tree. If the element is already present in the tree, then increment the count of the node. At last traverse the tree and find the node with the highest frequency.

```Java
class Tree {
    Tree left, right;
    int data, count;
    Tree(int x) {
        data = x;
        count = 1;
        left = right = null;
    }
}

class Main {

    public void insert(Tree root, int key, int ma) {
        if(root == null) {
            if(ma == 0)
                ma = 1;
            return new Tree(key);
        }
        else if(key < root.data){
            root.left = insert(root, key, ma);
        }
        else if(key > root.data) {
            root.right = insert(root, key, ma);
        }
        else
            root.count++;
    }

    public static int inorder(Tree root, int n) {
        if(root != null) {
            inorder(root.left, n);
            if(root.count  > n/2)
                return root.data;
            inorder(root.right, n);
        }
    }

    public static void main(String args[]) {
        //Take array input
        int max = 0;
        Tree root = null;
        for(int i = 0; i < n; i++)
            insert(root, ar[i], ma);
        int res = -1;
        if(ma > n/2)
            res = inorder(root, n);
        print(res);
    }
}
```
### Time complexity for the BST approach -
> If a self balancing binary search tree(Red Black Tree, AVL Tree) is used, then the time comlplexity is O(NlogN)

> By using normal BST the time complexity is O(N^2)

3. HashMap Approach :
> It is similar to the moore's voting algorithm, but here we don't need the second phase of it. Instead we calculate the key and frequencies of the key and store it in the hashmap.

```Java
int majority(int ar[], int n) {
    HashMap<Integer, Integer> hm = new HashMap<>();
    for(int i =0; i <n ;i++) {
        if(hm.containsKey(ar[i]))
            hm.put(ar[i], hm.get(ar[i])+1);
        else
            hm.put(ar[i], 1);
    }
    for(Map.Entry map : hm.entrySet()){
        if(map.getValue() > n/2)
            return map.getKey();
    }
    return -1;
}
```