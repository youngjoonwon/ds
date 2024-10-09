### Linked List

#### simple example 

let's create linkedlist.cpp

```c++
#include <iostream>
using namespace std;

// Definition for singly-linked list.
struct SinglyListNode {
    int val;
    SinglyListNode *next;
    SinglyListNode(int x) : val(x), next(NULL) {}
};

//Initiate: represent a linked list using the head node
class MyLinkedList {

	private:
    	SinglyListNode *head;

	public:
		MyLinkedList() {
        	head = NULL;
    	}
		
		//Traverse the linked list to get element by index.
		SinglyListNode* getNode(int index) {
				SinglyListNode *cur = head;
				for (int i = 0; i < index && cur; ++i) {
						cur = cur->next;
				}
				return cur;
		}

		SinglyListNode* getTail() {
				SinglyListNode *cur = head;
				while (cur && cur->next) {
						cur = cur->next;
				}
				return cur;
		}

		int get(int index) {
				SinglyListNode *cur = getNode(index);
				return cur == NULL ? -1 : cur->val;
		}
  
		//Add a new node.
		void addAtHead(int val) {
				SinglyListNode *cur = new SinglyListNode(val);
				cur->next = head;
				head = cur;
				return;
		}

		void addAtTail(int val) {
				if (head == NULL) {
						addAtHead(val);
						return;
				}
				SinglyListNode *prev = getTail();
				SinglyListNode *cur = new SinglyListNode(val);
				prev->next = cur;
		}

		void addAtIndex(int index, int val) {
				if (index == 0) {
						addAtHead(val);
						return;
				}
				SinglyListNode *prev = getNode(index - 1);
				if (prev == NULL) {
						return;
				}
				SinglyListNode *cur = new SinglyListNode(val);
				SinglyListNode *next = prev->next;
				cur->next = next;
				prev->next = cur;
		}

		//Delete a node.
		void deleteAtIndex(int index) {
				SinglyListNode *cur = getNode(index);
				if (cur == NULL) {
						return;
				}
				SinglyListNode *prev = getNode(index - 1);
				SinglyListNode *next = cur->next;
				if (prev) {
						prev->next = next;
				} else {
						// modify head when deleting the first node.
						head = next;
				}
		}
};

int main(int argc, char **argv) {
	
	MyLinkedList mylinklist;
	mylinklist.addAtHead(10);	
  
  return 0;
}
```

compile and run

```shell
$ g++-14 -o ll ./linkedlist.cpp
$ ./ll
```

modify the main to create your own linked list. 

### more example, double linked list

let's create doublelist.cpp, compile and run it. 

```c++
#include <iostream>
using namespace std;

// Definition for doubly-linked list.
struct DoublyListNode {
    int val;
    DoublyListNode *next, *prev;
    DoublyListNode(int x) : val(x), next(NULL), prev(NULL) {}
};

//Initiate: represent a linked list using the head node.
class MyLinkedList {
private:
    DoublyListNode *head;
public:

    //constructor
    MyLinkedList() {
        head = NULL;
    }

		DoublyListNode* getNode(int index) {
				DoublyListNode *cur = head;
				for (int i = 0; i < index && cur; ++i) {
						cur = cur->next;
				}
				return cur;
		}

		DoublyListNode* getTail() {
				DoublyListNode *cur = head;
				while (cur && cur->next) {
						cur = cur->next;
				}
				return cur;
		}

		int get(int index) {
				DoublyListNode *cur = getNode(index);
				return cur == NULL ? -1 : cur->val;
		}
				
		void addAtHead(int val) {
				DoublyListNode *cur = new DoublyListNode(val);
				cur->next = head;
				if (head) {
						head->prev = cur;
				}
				head = cur;
				return;
		}

		void addAtTail(int val) {
				if (head == NULL) {
						addAtHead(val);
						return;
				}
				DoublyListNode *prev = getTail();
				DoublyListNode *cur = new DoublyListNode(val);
				prev->next = cur;
				cur->prev = prev;
		}

		void addAtIndex(int index, int val) {
				if (index == 0) {
						addAtHead(val);
						return;
				}
				DoublyListNode *prev = getNode(index - 1);
				if (prev == NULL) {
						return;
				}
				DoublyListNode *cur = new DoublyListNode(val);
				DoublyListNode *next = prev->next;
				cur->prev = prev;
				cur->next = next;
				prev->next = cur;
				if (next) {
						next->prev = cur;
				}
		}

		void deleteAtIndex(int index) {
				DoublyListNode *cur = getNode(index);
				if (cur == NULL) {
						return;
				}
				DoublyListNode *prev = cur->prev;
				DoublyListNode *next = cur->next;
				if (prev) {
						prev->next = next;
				} else {
						// modify head when deleting the first node.
						head = next;
				}
				if (next) {
						next->prev = prev;
				}
		}
};

int main(int argc, char **argv) {
	
  return 0;
}
```

compile and run

```shell
$ g++-14 -o dl ./doublelist.cpp
$ ./dl
```

