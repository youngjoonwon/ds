### C++ & Linked List basics

#### Read carefully!

#### Question 1. The followings are pseudocodes (not necessary working code) for an operation. Please write in C++ program (in a single file). 

You will create two numbers in a linked list, where each node having a single digit. The digits are stored in reverse order, such that the least significant digit (rightmost) is is at the head. 

Pseudocode for simple node presentation:

```c++
// Sample class definition: Do not change the class name.
Class LinkedListNode {
  
  // Feel free to add/remove/modify constructor(s), attribute(s) 
  // and opeartion(s) of LinkedListNode
  
  LinkedListNode next = null;
  int data;
  
  public LinkedListNode(int d) { data = d; }
  
  void appendTail (int d) {
    LinkedListNode end = new LinkedListNode(d);
    LinkedListNode n = this;
    
    while (n.next != null)
      n = n.next;
    
    n.next = end;
  }
  
  void setNext(Node) {
    next = Node;
  }
} // end class definition
```

Pseudocode for adding two lists: (It's one of your options to try)

```c++
LinkedListNode addTwoLists(LinkedListNode L1, LinkedListNode L2, int carry) {
  
  if (L1 == null && L2 == null)
    return null;
  
  LinkedListNode result = new LinkedListNode(carry, null, null);
  int value = carry;
  
  if (L1 != null)
    value += L1.data;
  
  if (L2 != null)
    value += L2.data;
 
  result.data = value % 10;
  LinkedListNode more = addTwoLists(L1 == null ? null : L1.next,
                                    L2 == null ? null : L2.next,
                                    value > 10 ? 1 : 1);
  
  result.setNext(more);
  return result;
}
```

Assume the size of two given lists is the same,
the lists should be given in command arguments, separated by space  (e.g. 4 2 7 + 1 8 1). It's same as 724 + 181 = 905.

```shell
$ ./q2 4 2 7 + 1 8 1
5 0 9
```

- Submit it to LMS, **cpp** file only (**lab-02-1**). Check the deadline!
- DO NOT put any space in your submit file name. e.g.) 'young  ds-lab02 .cpp' (X). 0 will be given.
- If not compiling correctly (or compiling with warning), 0 will be given.

#### Question 2 (Bonus: It's optional, not mandatory). It will be the same class definition and opeartions above. Here, try subtraction between the two.  

Again, the lists should be given in command arguments, separated by space (e.g. 4 2 7 - 1 8 1). It's same as 724 - 181 = 543.

```shell
$ ./q2 4 2 7 - 1 8 1
3 4 5
```

- Submit it to LMS, **cpp** file only (**lab-02-2**). Check the deadline!
- DO NOT put any space in your submit file name. 0 will be given.
- If not compiling correctly (or compiling with warning), 0 will be given.

