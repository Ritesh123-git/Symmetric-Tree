# Symmetric-Tree
This problem is all about whether a tree is symmetric about it axis is or not
    1
   / \
  2   2
 / \ / \
3  4 4  3
  
Ans- True 
Reason- when we divide this tree from its axis. And when we are overlapping it we can see that the values at both the part are same.

Code----->
class Solution 
{
    public TreeNode mirror(TreeNode root) 
    {
        if(root==null)
        {
            return null;                     // calculating the mirror of original tree
        }
        TreeNode left=mirror(root.left);
         TreeNode right=mirror(root.right);
        TreeNode node=null;
        node=root.left;
        root.left=root.right;
        root.right=node;
        return root;
        
        
    }
     public boolean isSameTree(TreeNode p, TreeNode q) 
    {
         if(p==null  && q==null)
        {
            return true;                      // After calculating the mirror of a tree if the original tree is same as mirror tree
        }                                     then it is symmetric about it axis.
        if(p!=null && q==null)               
        {
            return false;
        }
          if(q!=null && p==null)
        {
            return false;
        }
       
       if(p.val!=q.val)
       {
           return false;
       }
        boolean left1= isSameTree(p.left,q.right);
        boolean right1= isSameTree(p.right,q.left);
        if(left1==true && right1==true)
        {
            return true;
        }
        return false;
    }
    
    
    public boolean isSymmetric(TreeNode root) 
    {
        TreeNode mirrorNode= mirror(root);      //  first we are calculating the mirror of a tree.
        boolean ans= isSameTree(root,mirrorNode);
        return ans;
    }
}
