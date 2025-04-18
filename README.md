# Add-two-linked-list
Add two linked list....
#include <iostream>
#include <bits/stdc++.h>

using namespace std;

// Node class represents a
// node in a linked list
class Node {
public:
       int data;
       Node* next;
   Node(int data1) {
        data = data1;
        next = nullptr;
    }
};
Node* addTwoLinkedLists(Node* l1, Node* l2) {
    
    Node* dummyNode = new Node(0);
    Node* curr = dummyNode;
    int carry=0;
     while (l1 != NULL || l2 != NULL||carry) {
      int sum= 0;
     if(l1!=NULL){
        sum+=l1->data;
        l1=l1->next;
     }if(l2!=NULL){
        sum+=l2->data;
        l2=l2->next;
     }
     sum+=carry;
     carry=sum/10;
     Node*newnode=new Node(sum%10);
     curr->next=newnode;
     curr=newnode;
    }
    return dummyNode->next;

};
void printLinkedList(Node* head) {
    Node* temp = head;
    while (temp != nullptr) {
        // Print the data of the current node
        cout << temp->data << " "; 
        // Move to the next node
        temp = temp->next; 
    }
    cout << endl;
};

int main() {
     Node* l1 = new Node(1);
    l1->next = new Node(0);
  Node*temp= l1->next->next = new Node(1);
  temp->next=new Node(9);
     Node* l2 = new Node(2);
    l2->next = new Node(0);
    l2->next->next = new Node(9);
    l2->next->next->next = new Node(1);

    cout << "First sorted linked list: ";
    printLinkedList(l1);

    cout << "Second sorted linked list: ";
    printLinkedList(l2);

    Node* mergedList = addTwoLinkedLists(l1, l2);

    printLinkedList(mergedList );

      
    return 0;
}
