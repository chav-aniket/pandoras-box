# Linked Lists
Tags: #guide, #C

This is pretty in-depth so if you don't understand something don't be scared, take it in bits at a time and ask us questions so we can make sure that everything is connecting, just like a linked list of information :) 

## Introduction

> What are they?

Linked lists are a data structure used to create a "chain" of nodes. These nodes are created using structs within C defined similar to what is shown below.

```C
struct node {
    int num;
    node *next;
};

struct list {
    node *head;
};
```

As you can see, the `node` in this case holds some integer as well as a pointer to the next `node`. 

If there is no next node, the value of next will be `NULL`. 

An example of such a list can be:

`(1) -> (2) -> (3) -> (4) -> NULL`

In this example, we will visualise one `node` as `(X)` where X is the `num` variable and the `->` is the pointer `*next`. 

## Purpose and Comparison

> We already have arrays, so why would we use linked lists for?

A table would be good here but I kinda wanna expand more so screw that.

### Length

The big obvious difference: arrays in C have a **static length** that you have to define when you define the array. If you want to append to a linked list, you can always just create a new node and point the last node to this new one. 

### Iterating

Going through an array is easy. You will usually just have some `for` loop and index the array. Linked lists are slightly more difficult because of their dynamic nature. We can index arrays because we define their length and the type the array will be comprised of (E.g. int, char, struct). This will let the compiler know that we need for example 20 integers worth of memory allocated in a row. With linked lists, when we create nodes they can be created at any point in the code and so are not necessarily right next to each other in terms of memory allocation. 

This is the reason why all linked lists **neeeeeed** that `*next` pointer. As arrays are blocks of memory right next to each other, they can just hop on over to the next memory block, but in linked lists we need to point to wherever the next node is in memory.

Because traditionally we only store the head of the linked list (as you can see within the `list` struct above), every time we need to access say the 4rth element of a linked list we need to start from head and keep going form `*next` to `*next` till we reach the 4rth node. It's definitely not as good as just writing list[4], don't worry we'll see an implementation of how to iterate soon. 

(If you didn't get some of the memory stuff don't worry, it's extension material and is covered more in-depth in subjects like COMP1521 and COMP2521!)

### Reordering

Because arrays are essentially one uninterrupted row of memory blocks with a set length, we can never pull something out or push something in. We can only ever redefine a certain element within the array. 

If we want to take the last element and make it the first (shifting the list one position forward), it would look something like this following code: 

```C
int[10] numList = {0,1,2,3,4,5,6,7,8,9};
// We have to store the last element seperately for later
int temp = numList[9];
// We rewrite every element backwards in the list to be the previous one
for (int i = 9; i >= 0; i--) {
    numList[i] = numList[i-1];
}
// We now replace the first element to be last element
numList[0] = temp;
// Honestly you won't ever do this, we use modulus for this stuff
```

Well, linked lists provide a computationally better alternative to this! Because linked lists are just a bunch of nodes in random places of memory which just point to each other, if we carefully rewire those pointers than we can do something like putting the last node in the first position without having to shift the entire list. We'll also get into this later when we go over implementations of changing a linked list.

### Conclusion

So the final score is 2:1 in favour of linked lists. Realistically speaking linked lists aren't exactly used in the industry, but we teach them because they're a good foundational data structure which help teach multiple things such as pointers, structs and malloc. With that consideration, 2 is a decent score. Those aren't all the differences but it's a good start.

## Use and Implementations

> Here we'll go through some of the things we can do with linked lists and how to do them

### Creation

Let's make a linked list with numbers from 0 - 6:

`ourList -> head = (0) -> (1) -> (2) -> (3) -> (4) -> (5) -> (6) -> NULL`

```C
// We'll be using the structs defined at the top of this document

// We will first define and malloc our list "carrier"
struct list *ourList = malloc(sizeof(list));
ourList->head = NULL;

struct node *curr = NULL;
for (int i = 0; i < 7; i++) {
    // We create a new node and malloc it
    struct node *newNode = malloc(sizeof(node));
    newNode->num = i;

    // If there is no head (AKA we're making the first node right now),
    //	we'll point head to this newNode;
    if (ourList->head == NULL) {
        ourList->head = newNode;
        curr = newNode;
    }
    
    // Here we say curr's next node is newNode, 
    //	line 17 ensures curr should never be NULL
    curr->next = newNode;
    
    // Replaces curr with the newNode to maintain reference to the latest
    //	node in the list
    curr = newNode;
}

// curr is at the last node right now so we'll just set that next to NULL
curr->next = NULL;
```

### Iteration

Yeah we know, I could've just put this in the last Iteration section but I make the rules here. 

```C
// Once again will be using the structs defined at the top of this document

// Let's assume we have some linked list defined within this ourList
struct list *ourList;

// Now to iterate, we just want to go through to the end right? The end is at NULL 
struct node *curr = ourList->head;
while (curr != NULL) {
    // Whatever we want to do with this current node
    curr = curr->next; // We replace the curr node with the next node
}
// When we get to the end, curr == NULL and the while loop will be exited
```

If you're doing anything with the next node, you probably want to have a condition like `curr->next != NULL` in the while loop just to make sure you never accidentally try to do something with `NULL`, this will cause an error in your code. 

### Appending

Now to add a new node with the number 7 to the end of the list.

`ourList -> head = (0) -> (1) -> (2) -> (3) -> (4) -> (5) -> (6) -> (7) -> NULL`

```C
// Once again we assume to have some linked list defined in ourList

struct list *ourList;

// We start by creating the new node we want to append
struct node *newNode = malloc(sizeof(node));
newNode->num = 4;
newNode->next = NULL;

// Now we want to iterate to the end so let's chuck a copy paste from above
struct node *curr = ourList->head;
while (curr->next != NULL) {
    curr = curr->next;
}

// We used this different condition because we want to stop BEFORE we get to NULL. This will exit the loop when curr equals the last node.
curr->next = newNode;

// And that's it, thanks for listening to my TEDtalk. 
```

### Reordering

We now want to reorder the list to put the last node in the first position.

`ourList -> head = (7) -> (0) -> (1) -> (2) -> (3) -> (4) -> (5) -> (6) -> NULL`

```C
// Let's skip the usual assumptions this time

struct list *ourList;

// We want to put the last node in first position,
//	so let's get that last node first.
struct node *curr = ourList->head;
while (curr->next->next != NULL) {
    curr = curr->next;
}

// This time we stopped at the second last node
// Because it will be the new last node and we want to point it to NULL
struct node *last = curr->next;
curr->next = NULL;

// Here we point the last node to the first node,
//	then officially make the last node the new head. 
last->next = ourList->head;
ourList->head = last;
```

### **WARNING**

Hopefully that got your attention, order of operations is EXTREMELY important when reordering linked lists. Just then, if we had lines 16 and 17 swapped, we would have lost our pointer to the old head and subsequently would have lost pointer reference to the rest of the list, only holding a pointer to that last node. 

### Removing



### 