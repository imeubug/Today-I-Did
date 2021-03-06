tags: #stack #linkedlist #data-structure #english

## Stack - Singly Linked List

A node in a singly linked list can only reference the next node. 

```cpp
class Node 
{
  public: 
    Node(int val):data(val), next(nullptr) {}

    int data;
    Node *next;
};
```

I used sentinel node to simplify the code. Thus, I can ignore the boundary conditions.

```cpp
class Stack 
{
  private:
    Node *sentinel;

  public:
    // member methods
    // ...
};
```

## Implementation

### PUSH

```cpp
void Stack::push(int x)
{
  Node *node = new Node(x);

  node->next = sentinel->next;
  sentinel->next = node; 
}
```

An empty list contains nothing but the sentinel like the image below.

`sentinel.next` always points to the top of the stack. So I can simply place the new node in between
the `sentinel` and `sentinel.next`.

### POP

```cpp
void Stack::pop()
{
  Node *temp = sentinel->next;
  sentinel->next = sentinel->next->next;
  delete temp;
}
```

Top of the stack is pointed by `sentinel.next` and we need to remove that. 
So We store that node into `temp` and update the top by `sentinel.next = sentinel.next.next`.

And then deallocate the memory of `temp`.

In C++, we need to manage the memory on our own. So we need to store the deleting node into a temporary space so we can 
deallocate its memory. If you're using a language that has an automatic memory management, or a *garbage collector*,
you can skip it.

[View](https://github.com/jioneeu/ds-algo/blob/master/stack/linkedlist) full source code of stack implementation using a singly linked list.

## Related Posts
- [[201020 LinkedList Basic]]
- [[201014 Implement a Stack using Array]]

## Reference
- Introduction to Algorithms, 3rd Edition (CLRS)