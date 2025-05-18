# Ex16 AVL Tree - Insertion
## DATE: 2-04-2025
## AIM:
To write a C function to insert the elements in an AVL Tree.

## Algorithm
1. Start
2. If the node is NULL, create a new node with value x.
3. Insert x recursively into the left or right subtree based on comparison.
4. Calculate the balance factor (BF) after insertion.
5. If BF is -2 or 2, perform appropriate rotations (RR, RL, LL, or LR).
6. Update the height of the current node.
7. Return the new root after insertion and balancing..
8. End
 

## Program:
```

Program to insert the elements in an AVL Tree
Developed by: SADHANA SHREE B
RegisterNumber: 212223230177

typedef struct node
{
int data;
struct node *left,*right;
int ht;
}node;
node *insert(node *,int);
void preorder(node *);
int height(node *);
node *rotateright(node *);
node *rotateleft(node *);
node *RR(node *);
node *LL(node *);
node *LR(node *);
node *RL(node *);
int BF(node *);

node * insert(node *T,int x)
{
    
    if(T==NULL){
        T=(node*)malloc(sizeof(node));
        T->data = x;
        T->left=NULL;
        T->right=NULL;
    }
    else{
        if(x > T->data){
            T-> right = insert(T->right,x);
            if(BF(T)==-2){
                if(x > T->right-> data){
                    T=RR(T);
                }
                else{
                    T=RL(T);
                }
            }
        }
        else{
            if(x < T->data){
                T-> left = insert(T->left,x);
                if(BF(T)==2){
                    if(x<T->left->data){
                        T=LL(T);
                    }
                    else{
                        T=LR(T);
                    }
                }
            }
        }
    }
    T->ht = height(T);
    return(T);
}

```

## Output:

![Screenshot 2025-05-18 125541](https://github.com/user-attachments/assets/90aeb699-92a2-4462-92c2-2601c697ec31)


## Result:
Thus, the function to insert the elements in an AVL Tree is implemented successfully in C programming language.
