## Given a binary tree, your task is to find subtree with maximum sum in tree. 

```
int dfs(TreeNode<int>*root, int &mxsum){
    if(!root){return 0;}
    int cursum = root->data+dfs(root->left,mxsum)+dfs(root->right,mxsum);

    mxsum = max(mxsum,cursum);

    return cursum;
}


int largestSubtreeSum(TreeNode<int> *root) {
    int mxsum = INT_MIN;
    dfs(root,mxsum);
    return mxsum;
}
```

## Construct the BST (Binary Search Tree) from its given level order traversal.

```
BinaryTreeNode<int>* insertInBst(BinaryTreeNode<int>*root, int val){
    if(!root){
        root=new BinaryTreeNode<int>(val);
        return root;
    }
    if(val<=root->left->data){
        root->left = insertInBst(root->left, val);
    }else{
        root->right = insertInBst(root->right, val);
    }

    return root;

}


BinaryTreeNode<int>* constructBst(vector<int>& levelOrder)
{
    if(levelOrder.size()==0){
        return NULL;
    }

    BinaryTreeNode<int>*root = NULL;
    for(int i=0;i<levelOrder.size();i++){
        root = insertInBst(root, levelOrder[i]);
    }

    return root;
}
```

## Given an array of size n. The problem is to check whether the given array can represent the level order traversal of a Binary Search Tree or not.

```
#include <bits/stdc++.h>
using namespace std;


struct boundary{
    int data;
    int mn;
    int mx;
}

bool isBST(int n, vector<int>&v){
    if(n==0){
        return true;
    }
    queue<boundary>q;
    int j=0;
    boundary cur;
    cur.data = v[j++];
    cur.mn = INT_MIN;
    cur.mx = INT_MAX;
    
    while(!q.empty() && !j=n){
        boundary tmp = q.front();
        q.pop();
        
        if(j<n && (v[j]<tmp.data && v[j]>tmp.mn)){
            cur.data = v[j++];
            cur.mn = tmp.mn;
            cur.mx = tmp.data;
            q.push(cur)
        }
        if(j<n && (v[j]>tmp.data && v[j]<tmp.mx)){
            cur.data = v[j++];
            cur.mn = tmp.data;
            cur.mx = tmp.mx;
            q.push(cur)
        }
    }
    return j==n;
}

int main() {
	int n;
	cin>>n;
	vector<int>v(n);
	
	for(int i=0;i<n;i++){
	    cin>>v[i];
	}
	
	if(isBST(n,v)){
	    cout<<"Yes\n";
	}else{
	    cout<<"No\n";
	}
	
	return 0;
}

```