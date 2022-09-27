# Is-Binary-Tree-Heap
Given a binary tree. The task is to check whether the given tree follows the max heap property or not.

In this questions, i used the basic concept of heap
A heap is a complete binary tree, so that does mean the height difference between left and right tree should be atmost 1, moreover left ht has to be gte than right ht. Every node in a max heap should be greater than all of it's children nodes.

Sharing the code approach 
```
class Item{
    int ht;
    boolean isHeap;
    Item(){
        
    }
    Item(int ht,boolean isHeap){
        this.ht = ht;
        this.isHeap = isHeap;
    }
}
class Solution {
    boolean isHeap(Node tree) {
        // code here
        return isHeapCheck(tree).isHeap;
    }
    
    Item isHeapCheck(Node tree){
         if(tree==null)
        return new Item(0,true);
        
        
        Item leftItem = isHeapCheck(tree.left);
        Item rightItem = isHeapCheck(tree.right);
        
        
        if(leftItem.isHeap&&rightItem.isHeap != true)
         return new Item(0,false);;
        if(!(leftItem.ht-rightItem.ht==1||leftItem.ht-rightItem.ht==0))
         return new Item(0,false);
         
        boolean left = tree.left==null?true:(tree.data>=tree.left.data);
        boolean right = tree.right==null?true:(tree.data>=tree.right.data);
        
        return new Item(1+leftItem.ht,left&&right);
    }
}
```

Time Complexity : 0(N) where N is the number of nodes in a heap
Space Complexity: O(logN), this is the stack space 
