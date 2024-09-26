// C++ program to sort a doubly linked list 
// using bubble sort
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node* prev;

    Node(int x) {
        data = x;
        next = nullptr;
        prev = nullptr;
    }
};

// Function to sort the doubly linked list 
// using bubble sort
Node* bubbleSort(Node* head) {
    if (head == nullptr) return head;

    bool swapped;
    Node* curr;
    Node* last = nullptr;

    // Keep going until no swaps occur in a pass
    do {
        swapped = false;
        curr = head;

        // Traverse through the list and swap adjacent
        // nodes if they are in the wrong order
        while (curr->next != last) {
            if (curr->data > curr->next->data) {
              
                // Swap the data of the current node 
                // and next node
                int swap_data = curr->data;
                curr->data = curr->next->data;
                curr->next->data = swap_data;

                swapped = true;
            }
            curr = curr->next;
        }
        
        // Reduce the effective list size after 
        // each pass
        last = curr;
    } while (swapped);

    return head;
}

void printList(Node* node) {
    Node* curr = node;
    while (curr != nullptr) {
        cout << " " << curr->data;
        curr = curr->next;
    }
}

int main() {
  
    // Create a hard-coded doubly linked list:
    // 5 <-> 3 <-> 4 <-> 1 <-> 2
    Node* head = new Node(5);
    head->next = new Node(3);
    head->next->prev = head;
    head->next->next = new Node(4);
    head->next->next->prev = head->next;
    head->next->next->next = new Node(1);
    head->next->next->next->prev = head->next->next;
    head->next->next->next->next = new Node(2);
    head->next->next->next->next->prev
                     = head->next->next->next;

    head = bubbleSort(head);

    printList(head);

    return 0;
}
# Bubble-Sort-On-Doubly-Linked-List
