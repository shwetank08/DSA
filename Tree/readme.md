## Given a Binary Tree (Bt), convert it to a Doubly Linked List(DLL). The left and right pointers in nodes are to be used as previous and next pointers respectively in converted DLL. The order of nodes in DLL must be the same as in Inorder for the given Binary Tree. The first node of Inorder traversal (leftmost node in BT) must be the head node of the DLL.

[Link](https://practice.geeksforgeeks.org/problems/binary-tree-to-dll/1)

```
class Solution
{
    public: 
    Node* head = NULL, *prev = NULL;
    //Function to convert binary tree to doubly linked list and return it.
    Node * bToDLL(Node *root)
    {
        // your code here
        if(!root){
            return NULL;
        }
        bToDLL(root->left);
        if(!prev){head = root;}
        else{
            prev->right = root;
            root->left = prev;
        }
        prev = root;
        bToDLL(root->right);
        return head;
    }
};
```

## A Given a binary tree, the task is to flip the binary tree towards the right direction that is clockwise. See the below examples to see the transformation. In the flip operation, the leftmost node becomes the root of the flipped tree and its parent becomes its right child and the right sibling becomes its left child and the same should be done for all left most nodes recursively.

```
Node* flipBinaryTree(Node* root){
    if(!root){return root;}
    if(!root->left && !root->right){
        return root;
    }
    Node*newRoot = flipBinaryTree(root->left);
    root->left->left = root->right;
    root->left->right = root;
    root->left = root->right = NULL;

    return newRoot;
}
```

## Given a binary tree, print all its root-to-leaf paths without using recursion. For example, consider the following Binary Tree.

```
vector<string> binaryTreePaths(TreeNode* root) {
        vector<string>ans;
        if(!root){
            return ans;
        }
        queue<pair<TreeNode*,string>>q;
        q.push({root,to_string(root->val)});
        while(!q.empty()){
            TreeNode*curNode = q.front().first;
            string path = q.front().second;
            q.pop();
            if(!curNode->left && !curNode->right){
                ans.push_back(path);
            }
            if(curNode->left){
                string s = path+"->"+to_string(curNode->left->val);
                q.push({curNode->left,s});
            }
            if(curNode->right){
                string s = path+"->"+to_string(curNode->right->val);
                q.push({curNode->right,s});
            }
        }
        return ans;
    }
```


