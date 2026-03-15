EX-1  

#include <stdio.h>  
#include <stdlib.h>  
struct node{  
int value;  
struct node *next;  
};  
printLinkedlist(struct node* p){      
while (p != NULL) {          
printf("%d ", p->value);          
p = p->next;  
}  
}  
int main() {      
struct node* head;      
struct node* one = NULL;      
struct node* two = NULL;      
struct node* three = NULL;  
one = malloc(sizeof(struct node));      
two = malloc(sizeof(struct node));      
three = malloc(sizeof(struct node));  
one->value = 1;      
two->value = 2;      
three->value = 3;  
one->next = two;          
two->next = three;    
three->next = NULL;     
head = one;    
printLinkedlist(head);    
return 0; 
}

EX-2  

#include <stdlib.h>  
#include <stdio.h>  
struct node{  
int data;     
struct node *left;     
struct node *right;  
};  
struct node *root = NULL;  
void insert(int data){  
struct node *tempnode = (struct node*)   
malloc(sizeof(struct node));      
struct node *current;      
struct node *parent;  
tempnode->data = data;      
tempnode->left = NULL;      
tempnode->right = NULL;  
if(root == NULL){          
root = tempnode;  
return;  
} 
else{ 
current = root;    
parent=NULL;   
while(1){          
parent = current;          
if(data < parent->data){  
current = current->left;              
if(current == NULL){                  
parent->left = tempnode;  
                return;  
            }          
}  
else {  
current = current->right;                 
if(current == NULL){                  
parent->right = tempnode;  
                return; }  
        }  
    }  
  }  
} 
struct node* search(int data){     
struct node *current = root;     
printf("Visiting elements:");  
while(current->data!=data){ 
if(current != NULL){          
printf("%d", current->data);  
 if(current->data >data)              
current=current->left;          
} 
else{ 
current=current->right; 
} 
If(current==NULL) 
{ 
       return NULL; 
       } 
} 
return current; 
} 
int main(){     
int arr[7] = 
{27,14,35,10,19,31,42};  
int i;  
for(i = 0; i < 7; i++)          
insert(arr[i]);  
i = 31;  
struct node *temp = search(i);      
if(temp != NULL)  { 
printf("\n[%d] Element found", temp
>data);  
printf("\n");    
} 
else { 
        printf("\n%d Element not found\n", 
i);  
} 
i = 15;      
temp = search(i);     
if(temp != NULL) 
{  
printf("\n[%d] Element found", temp
>data); 
printf("\n");    
}  
else {  
       printf("\n%d Element not found\n", i);  
} 
}


EX-3

#include <stdio.h>  
#include <stdlib.h>  
struct node {  
    int data;  
    struct node* next;  
};  
struct node *head = NULL, *tail = NULL;  
void addnode(int data) {  
struct node* new_node = (struct node*) 
malloc(sizeof(struct node));      
new_node->data = data;      
new_node->next = NULL;  
if (head == NULL) {  
        head = new_node;  
       tail = new_node;  
    }  
else {  
        tail->next = new_node;  
        tail = new_node  
    }  
}  
void sortlist() {  
struct node* current = head;     
struct node* index = NULL;     
int temp; 
if (head == NULL) {  
        return;   
    }  
else {  
          while (current != NULL) {              
index = current->next;              
while (index != NULL) {                  
if (current->data > index->data) {  
temp = current->data;                     
current->data = index->data;                     
index->data = temp;  
}  
index = index->next;  
}  
     current = current->next;  
        }  
    }  
}  
void display() {      
struct node* current = head;      
if (head == NULL) {          
printf("List is empty\n");         
return;  
    }  
while (current != NULL) {  
        printf("%d ", current->data);           
        current = current->next;  
    }  
    printf("\n");  
}  
int main() {  
addnode(9);      
addnode(7);      
addnode(11);      
addnode(15);  
addnode(2);  
printf("Original List:\n");      
display();  
sortlist();  
printf("Sorted List:\n");      
display();  
return 0;  
} 


EX—4

#include<stdio.h>  
#include<stdlib.h>  
#include<stdbool.h>  
struct node{  
  int key;  
  struct node*next;  
  };  
void push(struct node**head_ref, int 
new_key){  
         struct node*new_node=(struct  
node*) malloc(sizeof(struct node));  
 new_node->key=new_key;    
new_node->next=(*head_ref);  
 (*head_ref)=new_node;  
}  
bool search(struct node*head, int x) {  
struct node*current=head;  
 while(current!=NULL){      
       if(current->key==x)  
        return true;  
        current=current->next;  
    }  
    return false;  
}  
int main() {  
struct node*head=NULL;  
 push(&head,10);    
push(&head,15);    
push(&head,20);    
push(&head,48);  
 search(head,48)?printf("Yes"):printf(" 
No");  
 return 0;  
} 



EX-5 

#include<stdio.h>  
#include<stdlib.h>  
struct node {  
 int data;    
struct node*next;  
};  
struct node*head=NULL;  
void push(int val){  
 struct node*newnode=(struct  
node*) malloc(sizeof(struct node));  
 newnode->data=val;    
newnode->next=head;    
head=newnode;  
}  
void pop(){  
struct node*temp;   
if(head==NULL)  
  printf("Stack is empty \n");  
 else {  
            printf("Poped element %d\n",  
                                                  head
>data);  
            temp=head;  
head=head->next;        
free(temp);  
         }  
}  
void printlist(){
struct node*temp=head;    
while(temp!=NULL){      
printf("\t %d",temp->data);  
               temp=temp->next;  
  }  
  printf("\t NULL\n");  
}  
int main()  
{  
     push(20);    
     push(30);    
     push(40);  
     printlist();  
     pop();  
     printlist();  
}


EX-6 

#include <stdio.h>  
#include <stdlib.h>  
struct node {  
    int data;      
    struct node* next;  
};  
struct node* front = NULL;  
struct node* rear = NULL; 
void enqueue(int value) {  
    struct node* ptr = (struct node*) 
malloc(sizeof(struct node));  
    ptr->data = value;  
    ptr->next = NULL;   
    if (front == NULL && rear == NULL) 
{  
        front = rear = 
ptr;       }  
else {          
rear->next = ptr;           
rear = ptr;          
}  
printf("Node is inserted\n\n");  
}   
int dequeue() {  
if (front == NULL) {          
printf("\nUnderflow");          
return -1;    
}  
else {          
struct node* temp = front;          
int temp_data = front->data;         
front = front->next;    
free(temp);             
return temp_data;       
    }  
} 
void display() {     
struct node* temp;  
if (front == NULL && rear == NULL) {         
printf("\nQueue is empty\n");  
 }  
else {          
printf("The queue is: \n");         
temp = front;         
 while (temp) {              
printf("%d ---> ", temp
>data);               temp = temp
>next;    
}  
        printf("NULL\n\n");  
    }  
} 
int main() {      
int choice = 0, 
value;  
printf("Implementation of queue using 
linked list\n");  
 while (choice != 4) {  
printf("1. Enqueue\n2. Dequeue\n3. 
Display\n4. Exit\n");          
printf("Enter your choice: ");          
scanf("%d", &choice);  
 switch (choice) {              
case 1:  
printf("\nEnter the value to insert: ");                 
scanf("%d", &value);                 
enqueue(value);  
break;              
case 2:
printf("Popped Element is: %d\n",     
dequeue());  
break;             
 case 3:                 
display();                 
break;              
case 4:                 
printf("Exiting...\n
";                 return 
0;               
default:  
printf("\nWrong choice\n");  
        }  
    }  
    return 0;  
}


EX - 7

#include<stdio.h> 
#include<stdlib.h> 
struct Node{ 
 int data; 
 struct Node*next; 
 struct Node*prev; 
}; 
void insertFront(struct Node** head, int data){ 
 struct Node* newNode = (struct 
Node*)malloc(sizeof(struct Node)); 
 newNode->data = data; 
 newNode->next = (*head); 
 newNode->prev = NULL; 
 if((*head) != NULL) 
  (*head)->prev = newNode; 
 (*head) = newNode; 
} 
void insertAfter(struct Node* prev_node, int 
data){ 
 if(prev_node == NULL){ 
 printf("Previous node cannot be null"); 
  return; 
 } 
 struct Node* newNode = (struct 
Node*)malloc(sizeof(struct Node)); 
 newNode->data = data; 
 newNode->next = prev_node->next; 
 prev_node->next = newNode; 
 newNode->prev = prev_node; 
 if(newNode->next != NULL) 
 newNode->next->prev = newNode; 
} 
void insertEnd(struct Node** head,int data) { 
 struct Node* newNode = (struct 
Node*) malloc(sizeof(struct Node));
newNode->data = data; 
 newNode->next = NULL; 
 struct Node* temp = *head; 
 if(*head == NULL) { 
  newNode->prev = NULL; 
  *head = newNode; 
  return; 
 } 
 while(temp->next != NULL) 
 temp=temp->next; 
 temp->next = newNode; 
 newNode->prev = temp; 
} 
void deleteNode(struct Node** head,struct 
Node* del_node){ 
 if(*head == NULL || del_node == 
NULL) 
  return; 
 if(*head == del_node) 
  *head = del_node->next; 
 if(del_node->next != NULL) 
del_node->next->prev =   
del_node->prev; 
 if(del_node->prev != NULL) 
  del_node->prev->next = 
del_node->next; 
  free(del_node);   
} 
void displayList(struct Node* node){ 
 struct Node* last; 
 while (node != NULL) { 
  printf("%d->",node->data); 
  last = node; 
  node = node->next; 
 } 
 if(node == NULL) 
  printf("NULL\n");
  } 
int main() { 
 struct Node* head = NULL; 
 insertEnd(&head,5); 
 insertFront(&head,1); 
 insertFront(&head,6); 
 insertEnd(&head,9); 
 insertAfter(head,11); 
 insertAfter(head->next,15); 
 displayList(head); 
 deleteNode(&head,head->next->next
>next->next->next); 
 displayList(head); 
}


EX- 8 

#include<stdio.h> 
int main(){ 
 int arr[10], no, i, j, c, heap_root, temp; 
 printf("Input number of elements:"); 
 scanf("%d",&no); 
 printf("\nInput array values one by      
one : "); 
 for(i = 0;i< no;i++) 
 scanf("%d",&arr[i]); 
 for(i = 1;i<no;i++){ 
 c=i; 
 do{ 
  heap_root=(c-1)/2; 
  if(arr[heap_root] < arr[c]){ 
  temp = arr[heap_root]; 
  arr[heap_root] = arr[c]; 
  arr[c] = temp; 
  } 
  c=heap_root; 
  } while(c != 0); 
 } 
 printf("Heap array : "); 
 for(i = 0;i< no;i++) 
 printf("%d \t",arr[i]); 
 for(j = no-1;j>=0;j--){ 
      temp = arr[0]; 
      arr[0] = arr[j]; 
      arr[j] = temp; 
      heap_root = 0; 
      do{ 
           c = 2*heap_root+1; 
           if((arr[c] < arr[c+1]) && c <j-1) 
         c++; 
           if(arr[heap_root]<arr[c] && 
c<j){ 
  temp = arr[heap_root]; 
  arr[heap_root] = arr[c]; 
  arr[c] = temp; 
  } 
 heap_root = c; 
 }while(c < j); 
 } 
 printf("\n Sorted array:"); 
 for(i = 0;i <no;i++) 
 printf("\t%d",arr[i]); 
 printf("\n"); 
}


EX-9
#include<stdio.h> 
char stack[20]; 
int top = -1; 
void push(char x){ 
 stack[++top] = x; 
} 
char pop() { 
 if(top == -1) 
 return -1; 
 else 
 return stack[top--]; 
} 
int priority(char x) { 
 if(x =='(') 
 return 0; 
 if( x == '+'||x == '-') 
 return 1; 
 if(x=='*'||x=='/') 
 return 2; 
} 
int main() { 
 char exp[20]; 
 char *e,x; 
 printf("Enter the expression:"); 
 scanf("%s",exp); 
 e = exp; 
 while(*e !='\0') { 
  if(isalnum(*e)) 
  printf("%c",*e); 
  else if(*e =='(') 
  push(*e); 
  else if(*e==')') 
  { 
   while((x=pop())!='(') 
   printf("%c",x); 
  } 
  else { 
 while(priority(stack[top])>=priority(*e)) 
  printf("%c",pop()); 
  push(*e); 
  } 
  e++; 
 } 
 while(top != -1) { 
  printf("%c",pop()); 
 } 
    }

    

 EX-10

 
 #include <stdio.h> 
 
int max(int a, int b) { 
    return (a > b) ? a : b; 
} 
int knapSack(int W, int wt[], int val[], int n) 
{ 
int i, w; 
    int K[n + 1][W + 1]; 
    for (i = 0; i <= n; i++) 
    { 
        for (w = 0; w <= W; w++) 
        { 
            if (i == 0 || w == 0) 
                K[i][w] = 0; 
            else if (wt[i - 1] <= w) 
                K[i][w] = max(val[i - 1] + K[i - 1][w - wt[i - 1]], K[i - 1][w]); 
            else 
                K[i][w] = K[i - 1][w]; 
        } 
    } 
    return K[n][W]; 
} 
 
int main() 
{ 
    int i, n, val[20], wt[20], W; 
    printf("Enter number of items:"); 
    scanf("%d", &n); 
    printf("Enter value and weight of     
   items:\n"); 
    for (i = 0; i < n; ++i) 
    { 
        scanf("%d%d", &val[i], &wt[i]); 
    } 
    printf("Enter size of knapsack:"); 
    scanf("%d", &W); 
    printf("%d", knapSack(W, wt, val, n)); 
    return 0; 
}


EX-11

#include <stdio.h> 
#include <limits.h> 
#define V 5 
 
int minKey(int key[], int mstSet[])  
{ 
    int min = INT_MAX, min_index; 
    int v; 
    for (v = 0; v < V; v++) 
        if (mstSet[v] == 0 && key[v] < min) 
            min = key[v], min_index = v; 
    return min_index; 
} 
 
int printMST(int parent[], int n, int 
graph[V][V])  
{ 
    int i; 
    printf("Edge   Weight\n"); 
    for (i = 1; i < V; i++) 
        printf("%d - %d    %d\n", parent[i], i, 
graph[i][parent[i]]); 
} 
 
void primMST(int graph[V][V])  
{ 
int parent[V]; 
    int key[V], i, v, count; 
    int mstSet[V]; 
    for (i = 0; i < V; i++) 
        key[i] = INT_MAX, mstSet[i] = 0; 
    key[0] = 0; 
    parent[0] = -1; 
    for (count = 0; count < V - 1; count++)  
    { 
        int u = minKey(key, mstSet);
        mstSet[u] = 1; 
        for (v = 0; v < V; v++) 
            if (graph[u][v] && mstSet[v] == 0 && graph[u][v] < key[v]) 
                parent[v] = u, key[v] = graph[u][v]; 
    } 
    printMST(parent, V, graph); 
} 
 
int main()  
{ 
    int graph[V][V] = { 
        {0, 2, 0, 6, 0}, 
        {2, 0, 3, 8, 5}, 
        {0, 3, 0, 0, 7}, 
        {6, 8, 0, 0, 9}, 
        {0, 5, 7, 9, 0} 
    }; 
    primMST(graph); 
    return 0; 
}



EX-12

#include <stdio.h> 
#include <math.h> 
 
int board[20], count; 
void queen(int row, int n); 
void print(int n); 
int place(int row, int column); 
 
int main() 
{ 
    int n, i, j; 
    printf("- N Queens Problem Using 
Backtracking -"); 
    printf("\n\nEnter number of Queens:"); 
    scanf("%d", &n); 
    queen(1, n); 
    return 0; 
} 
 
void print(int n) 
{ 
    int i, j; 
    printf("\n\nSolution %d:\n\n", ++count); 
    for(i = 1; i <= n; ++i) 
        printf(" %d", i); 
    for(i = 1; i <= n; ++i) 
    { 
        printf("\n\n%d", i);
           for(j = 1; j <= n; ++j) 
        { 
            if(board[i] == j) 
                printf("\tQ"); 
            else 
                printf("\t-"); 
        } 
    } 
} 
 
int place(int row, int column) 
{ 
    int i; 
    for(i = 1; i <= row - 1; ++i) 
    { 
        if(board[i] == column) 
            return 0; 
        else if(abs(board[i] - column) == abs(i - 
row)) 
            return 0; 
    } 
    return 1; 
} 
 
void queen(int row, int n) 
{ 
    int column; 
    for(column = 1; column <= n; ++column) 
    { 
        if(place(row, column)) 
        { 
            board[row] = column; 
            if(row == n) 
                print(n); 
            else 
                queen(row + 1, n);
                  } 
    } 
} 



EX-13

#include<stdio.h> 
#define INFINITY 9999 
#define MAX 10 
 
void Dijkstra(int Graph[MAX][MAX],int n,int 
start){ 
int 
cost[MAX][MAX],distance[MAX],pred[MAX
]; 
int 
visited[MAX],count,mindistance,nextnode,i,j; 
for(i = 0; i<n ; i++) 
for(j = 0;j < n; j++) 
if(Graph[i][j] == 0) 
cost[i][j] = INFINITY; 
else 
cost[i][j] = Graph[i][j]; 
for(i=0;i<n;i++){ 
 distance[i] = cost[start][i]; 
 pred[i]=start; 
 visited[i]=0; 
} 
distance[start]=0; 
visited[start]=1; 
count=1; 
while(count<n-1){ 
 mindistance=INFINITY; 
 for(i=0;i<n;i++) 
 if(distance[i]<mindistance && 
!visited[i]){ 
  mindistance = distance[i]; 
  nextnode = i; 
 } 
 visited[nextnode]=1; 
 for(i=0;i<n;i++) 
 if(!visited[i]) 
 if(mindistance+cost[nextnode][i]<dist
ance[i]){ 
  distance[i] = 
mindistance+cost[nextnode][i]; 
  pred[i]=nextnode; 
 } 
 count++; 
} 
for(i=0;i<n;i++) 
if(i!=start){ 
 printf("\nDistance from source to 
%d:%d",i,distance[i]); 
} 
} 
int main(){ 
 int Graph[MAX][MAX],i,j,n,u; 
 n=7; 
 Graph[0][0]=0; 
 Graph[0][1]=0; 
 Graph[0][2]=1; 
 Graph[0][3]=2; 
 Graph[0][4]=0; 
 Graph[0][5]=0; 
 Graph[0][6]=0; 
 Graph[1][0]=0; 
 Graph[1][1]=0; 
 Graph[1][2]=2; 
 Graph[1][3]=0; 
 Graph[1][4]=0; 
 Graph[1][5]=3; 
 Graph[1][6]=0; 
 Graph[2][0]=1; 
 Graph[2][1]=2; 
 Graph[2][2]=0; 
 Graph[2][3]=1; 
 Graph[2][4]=3; 
 Graph[2][5]=0; 
 Graph[2][6]=0; 
 Graph[3][0]=2; 
 Graph[3][1]=0; 
 Graph[3][2]=1; 
 Graph[3][3]=0; 
 Graph[3][4]=0; 
 Graph[3][5]=0; 
 Graph[3][6]=1; 
 Graph[4][0]=0; 
 Graph[4][1]=0; 
 Graph[4][2]=3; 
 Graph[4][3]=0; 
 Graph[4][4]=0; 
 Graph[4][5]=2; 
 Graph[4][6]=0; 
 Graph[5][0]=0; 
 Graph[5][0]=0; 
 Graph[5][1]=3; 
 Graph[5][2]=0; 
 Graph[5][3]=0; 
 Graph[5][4]=2; 
 Graph[5][5]=0; 
 Graph[5][6]=1; 
 Graph[6][0]=0; 
 Graph[6][1]=0;
 Graph[6][2]=0; 
 Graph[6][3]=1; 
 Graph[6][4]=0; 
 Graph[6][5]=1; 
 Graph[6][6]=0; 
 u=0; 
 Dijkstra(Graph,n,u); 
 return 0; 
}



EX-14

#include <stdio.h> 
#include <stdlib.h> 
struct node{ 
    int data; 
    struct node* left; 
    struct node* right; 
}; 
 
void inorder(struct node* root){ 
    if(root == NULL)  
        return; 
    inorder(root->left); 
    printf("%d->", root->data); 
    inorder(root->right); 
} 
 
void preorder(struct node* root){ 
    if(root == NULL)  
        return; 
    printf("%d->", root->data); 
    preorder(root->left); 
    preorder(root->right); 
} 
 
void postorder(struct node* root){ 
    if(root == NULL)  
        return; 
    postorder(root->left); 
    postorder(root->right); 
    printf("%d->", root->data); 
} 
 
struct node* createNode(int value){ 
    struct node* newNode = (struct 
node*)malloc(sizeof(struct node)); 
    newNode->data = value; 
    newNode->left = NULL; 
    newNode->right = NULL; 
    return newNode; 
} 
 
struct node* insertleft(struct node *root, int 
value) { 
    root->left = createNode(value); 
    return root->left; 
} 
 
struct node* insertright(struct node *root, int 
value){ 
    root->right = createNode(value); 
    return root->right; 
} 
int main(){ 
    struct node* root = createNode(1); 
    insertleft(root,12); 
    insertright(root,9); 
    insertleft(root->left,5); 
    insertright(root->left,6); 
    printf("inorder traversal\n"); 
    inorder(root); 
    printf("\n preorder traversal\n"); 
    preorder(root); 
    printf("\n postorder traversal\n"); 
    postorder(root); 
    return 0; 
}


EX-15

#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 
#include <stdbool.h> 
#define SIZE 20 
 
struct DataItem { 
    int data; 
    int key; 
}; 
 
struct DataItem* hashArray[SIZE]; 
struct DataItem* dummyItem; 
struct DataItem* item; 
int hashCode(int key) { 
    return key % SIZE; 
} 
 
struct DataItem *search(int key) { 
    int hashIndex = hashCode(key); 
    while(hashArray[hashIndex] != NULL) { 
        if(hashArray[hashIndex]->key == key) 
            return hashArray[hashIndex]; 
        ++hashIndex; 
        hashIndex %= SIZE; 
    } 
    return NULL; 
} 
 
void insert(int key, int data) { 
    struct DataItem *item = (struct DataItem*) 
malloc(sizeof(struct DataItem)); 
    item->data = data; 
    item->key = key; 
    int hashIndex = hashCode(key); 
 
while(hashArray[hashIndex] != NULL && 
hashArray[hashIndex]->key != -1) { 
        ++hashIndex; 
        hashIndex %= SIZE; 
    } 
    hashArray[hashIndex] = item; 
} 
struct DataItem* delete(struct DataItem* item) 
{ 
    int key = item->key; 
    int hashIndex = hashCode(key); 
    while(hashArray[hashIndex] != NULL) { 
        if(hashArray[hashIndex]->key == key) { 
            struct DataItem* temp = 
hashArray[hashIndex]; 
            hashArray[hashIndex] = dummyItem; 
            return temp; 
        } 
        ++hashIndex; 
        hashIndex %= SIZE; 
    } 
    return NULL; 
} 
 
void display() { 
    int i = 0; 
    for(i = 0; i < SIZE; i++) { 
        if(hashArray[i] != NULL) 
            printf(" (%d,%d)", hashArray[i]->key, 
hashArray[i]->data); 
        else 
            printf(" ~~ "); 
    } 
    printf("\n"); 
} 
 
int main() { 
dummyItem = (struct DataItem*) 
malloc(sizeof(struct DataItem)); 
    dummyItem->data = -1; 
    dummyItem->key = -1; 
    insert(1, 20);
    insert(2, 70); 
    insert(42, 80); 
    insert(4, 25); 
    insert(12, 44); 
    insert(14, 32); 
    insert(17, 11); 
    insert(13, 78); 
    insert(37, 97); 
    display(); 
    item = search(14); 
    if(item != NULL) { 
        printf("Element found: %d\n", item
>data); 
    } else { 
        printf("Element not found\n"); 
    } 
    return 0; 
