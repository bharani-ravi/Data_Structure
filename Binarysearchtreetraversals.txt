#include <stdio.h>  
#include <stdlib.h>  
#include <stdbool.h>  
 
struct node{  
    int data;  
    struct node *left;  
    struct node *right;  
};  
  
struct node *root= NULL;  
  
struct node* createNode(int data){  
    struct node *newNode = (struct node*)malloc(sizeof(struct node));  
    newNode->data= data;  
    newNode->left = NULL;  
    newNode->right = NULL;  
      
    return newNode;  
}  
void insert(int data) {  
    
    struct node *newNode = createNode(data);  
            
    if(root == NULL){  
        root = newNode;  
        return;  
      }  
    else {  
        struct node *current = root, *parent = NULL;  
         while(true) {  
            parent = current;  
    
            if(data < current->data) {  
                current = current->left;  
                if(current == NULL) {  
                    parent->left = newNode;  
                    return;  
                }  
            }  
            else {  
                current = current->right;  
                if(current == NULL) {  
                    parent->right = newNode;  
                    return;  
                }  
            }  
        }  
    }  
}  
     
void inorderTraversal(struct node *node) {  
    if(root == NULL){  
        printf("Tree is empty\n");  
          return;  
     }  
    else {  
            
        if(node->left!= NULL)  
            inorderTraversal(node->left);  
        printf("%d ", node->data);  
        if(node->right!= NULL)  
          inorderTraversal(node->right);  
            
    }        
}  
void preorderTraversal(struct node *node) {  
        
    if(root == NULL){  
        printf("Tree is empty\n");  
          return;  
     }  
    else {  
        printf("%d ", node->data);     
        if(node->left!= NULL)  
            preorderTraversal(node->left);  
        if(node->right!= NULL)  
          preorderTraversal(node->right);  
            
    }        
}  
void postorderTraversal(struct node *node) {  
    
    if(root == NULL){  
        printf("Tree is empty\n");  
          return;  
     }  
    else {  
            
        if(node->left!= NULL)  
            postorderTraversal(node->left);  
        if(node->right!= NULL)  
          postorderTraversal(node->right);  
        printf("%d ", node->data);  
            
    }        
}          
int main()  
{  
    insert(2);  
    insert(1);  
    insert(3);
      
    printf("\nBinary search tree - inorder traversal: \n");  
    inorderTraversal(root);  
    printf("\nBinary search tree - preorder traversal: \n");  
    preorderTraversal(root);
    printf("\nBinary search tree - postorder traversal: \n");  
    postorderTraversal(root);
      
  
    return 0;  
}  


Output:
Binary search tree - inorder traversal: 
1 2 3 
Binary search tree - preorder traversal: 
2 1 3 
Binary search tree - postorder traversal: 
1 3 2 