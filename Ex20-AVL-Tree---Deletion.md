# Ex20 AVL Tree - Deletion
## DATE: 18-04-2025
## AIM:
To write a C function to delete an element from an AVL Tree.

## Algorithm
1. Search for the node to delete starting from the root.
2. Delete the node using standard BST rules.
3. Update the height of the affected nodes.
4. Calculate the balance factor of each updated node.
5. Perform rotations if the node is unbalanced.
6. Continue until the tree is balanced again.  

## Program:
```
Program to find and display the priority of the operator in the given Postfix expression
Developed by: SADHANA SHREE B
RegisterNumber: 212223230177

typedef struct node
{
int data;
struct node *left,*right;
int ht;
}node;
 
node *insert(node *,int);
node *Delete(node *,int);
void preorder(node *);
void inorder(node *);
int height( node *);
node *rotateright(node *);
node *rotateleft(node *);
node *RR(node *);
node *LL(node *);
node *LR(node *);
node *RL(node *);
int BF(node *);
node * Delete(node *T,int x)
{
    node *p;
    if(T==NULL){
        return NULL;
    }
    else if(x > T->data){
        T->right = Delete(T->right,x);
        if(BF(T)==2){
            if(BF(T->left)>=0){
                T=LL(T);
            }
            else{
                T=LR(T);
            }
        }
    }
    else{
        if(x < T->data){
            T->left=Delete(T->left,x);
            if(BF(T)==-2){
                if(BF(T->right)<=0){
                    T=RR(T);
                }
                else{
                    T=RL(T);
                }
            }
        }
        else{
            if(T->right!=NULL){
                p=T->right;
                while(p->left!=NULL){
                    p=T->left;
                }
                T->data=p->data;
                T->right=Delete(T->right,p->data);
                {
                    if(BF(T)==2){
                        if(BF(T->left)>=0){
                            T=LL(T);
                        }
                        else{
                            T=LR(T);
                        }
                    }
                }
            }
            else{
                return(T->left);
            }
        }
    }
    T->ht = height(T);
    return (T);
}

```

## Output:

![Screenshot 2025-05-18 131037](https://github.com/user-attachments/assets/37f25e6c-95c1-467f-bc35-7d015601e41c)


## Result:
Thus, the C program to delete an element from an AVL Tree is implemented successfully.
