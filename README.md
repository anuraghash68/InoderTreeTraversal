# InoderTreeTraversal
Traversal of a Tree by using inorder in recusive and iterative.
#include <bits/stdc++.h>
using namespace std;

struct Node{
	int data;
	Node* left,*right;
	
	Node(int data)
	{
		this -> data = data;
		this -> left = nullptr;
		this -> right = nullptr;
	}
};

void recursiveInorder(Node* root)
{
	if(root == nullptr)
		return;
	
	recursiveInorder(root -> left);
	printf("%d ", root -> data);
	recursiveInorder(root -> right);
}

void nonRecursiveInorder(Node* root)
{
	stack<Node*> stack;
	 
	Node* curr = root;
	
	while(!stack.empty() || curr != nullptr)
	{
		if(curr != nullptr)
		{
			stack.push(curr);
			curr = curr -> left;
		}
		else
		{
		    curr = stack.top();
			stack.pop();
			cout << curr -> data << ' ';
			curr = curr -> right;
		}
	}
}

int main() {
	// your code goes here
	
	Node * root = new Node(1);
	root -> left = new Node(2);
	root -> right = new Node(3);
	
	recursiveInorder(root);
	cout << endl;
	nonRecursiveInorder(root);
	
	return 0;
}
