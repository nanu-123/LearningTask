Got it! Here's the full content in **Markdown (MD)** format:

```markdown
# Linked Lists: Types, Examples, and Use Cases

Below, I’ll provide detailed explanations, examples in C, and use cases for all major types of linked lists: **Singly Linked List**, **Doubly Linked List**, **Circular Singly Linked List**, and **Circular Doubly Linked List**. Each example will include basic operations (like insertion and traversal) to illustrate how they work, followed by practical use cases.

---

## 1. Singly Linked List

### Explanation
- Each node contains **data** and a **pointer to the next node**.
- The last node points to **NULL**, marking the end.
- Traversal is **unidirectional** (forward only).

### Example in C

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Insert at the beginning
void insert(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = *head;
    *head = newNode;
}

// Print the list
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    insert(&head, 3);  // 3 -> NULL
    insert(&head, 2);  // 2 -> 3 -> NULL
    insert(&head, 1);  // 1 -> 2 -> 3 -> NULL
    printList(head);   // Output: 1 -> 2 -> 3 -> NULL

    // Free memory (simplified)
    while (head != NULL) {
        struct Node* temp = head;
        head = head->next;
        free(temp);
    }
    return 0;
}
```

**Output:**  
`1 -> 2 -> 3 -> NULL`

### How It Works
- **Insertion:** New node points to the current head, then becomes the new head (**O(1)**).
- **Traversal:** Follow `next` pointers until `NULL` (**O(n)**).

### Use Cases
- **Stack Implementation:** Push/pop operations at the head (LIFO - Last In, First Out).  
  *Example: Undo functionality in text editors.*
- **Queue Implementation:** Insert at tail, remove from head (FIFO - First In, First Out).  
  *Example: Task scheduling in operating systems.*
- **Dynamic Data Storage:** When the size isn’t known upfront.  
  *Example: Storing user inputs in a program.*

---

## 2. Doubly Linked List

### Explanation
- Each node has **data**, a **pointer to the next node**, and a **pointer to the previous node**.
- Allows **bidirectional traversal** (forward and backward).
- The first node’s `prev` and last node’s `next` point to `NULL`.

### Example in C

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
    struct Node* prev;
};

// Insert at the beginning
void insert(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = *head;
    newNode->prev = NULL;
    if (*head != NULL) {
        (*head)->prev = newNode;
    }
    *head = newNode;
}

// Print forward
void printForward(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d <-> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    insert(&head, 3);  // 3 <-> NULL
    insert(&head, 2);  // 2 <-> 3 <-> NULL
    insert(&head, 1);  // 1 <-> 2 <-> 3 <-> NULL
    printForward(head); // Output: 1 <-> 2 <-> 3 <-> NULL

    // Free memory (simplified)
    while (head != NULL) {
        struct Node* temp = head;
        head = head->next;
        free(temp);
    }
    return 0;
}
```

**Output:**  
`1 <-> 2 <-> 3 <-> NULL`

### How It Works
- **Insertion:** Adjust `next` and `prev` pointers for the new node and its neighbors (**O(1)**).
- **Traversal:** Can go forward (`next`) or backward (`prev`) (**O(n)** in either direction).

### Use Cases
- **Browser History:** Move back and forth between visited pages.  
  *Example: Chrome’s "Back" and "Forward" buttons.*
- **Undo/Redo Systems:** Track previous and next states.  
  *Example: Graphic design software (e.g., Photoshop).*
- **Music Playlists:** Navigate songs forward or backward.  
  *Example: Media players with "previous" and "next" controls.*

---

## 3. Circular Singly Linked List

### Explanation
- A singly linked list where the **last node points back to the first node**, forming a loop.
- No `NULL` pointer; traversal can continue indefinitely unless stopped explicitly.

### Example in C

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Insert at the end
void insert(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;

    if (*head == NULL) {
        *head = newNode;
        newNode->next = *head;
    } else {
        struct Node* temp = *head;
        while (temp->next != *head) {
            temp = temp->next;
        }
        temp->next = newNode;
        newNode->next = *head;
    }
}

// Print the list (stop after one loop)
void printList(struct Node* head) {
    if (head == NULL) return;
    struct Node* temp = head;
    do {
        printf("%d -> ", temp->data);
        temp = temp->next;
    } while (temp != head);
    printf("(back to %d)\n", head->data);
}

int main() {
    struct Node* head = NULL;
    insert(&head, 1);  // 1 -> (back to 1)
    insert(&head, 2);  // 1 -> 2 -> (back to 1)
    insert(&head, 3);  // 1 -> 2 -> 3 -> (back to 1)
    printList(head);   // Output: 1 -> 2 -> 3 -> (back to 1)

    // Free memory (simplified)
    struct Node* temp = head->next;
    while (temp != head) {
        struct Node* next = temp->next;
        free(temp);
        temp = next;
    }
    free(head);
    return 0;
}
```

**Output:**  
`1 -> 2 -> 3 -> (back to 1)`

### How It Works
- **Insertion:** Find the last node (where `next` points to `head`), link the new node, and point it back to `head`.
- **Traversal:** Use a `do-while` loop to stop after one full cycle (**O(n)**).

### Use Cases
- **Round-Robin Scheduling:** Cycle through tasks or processes.  
  *Example: CPU scheduling in operating systems.*
- **Game Loops:** Players take turns in a circular order.  
  *Example: Multiplayer board games.*
- **Circular Buffers:** Store data in a fixed-size loop.  
  *Example: Streaming audio buffers.*

---

## 4. Circular Doubly Linked List

### Explanation
- A doubly linked list where the **last node’s `next` points to the first node**, and the **first node’s `prev` points to the last node**.
- Forms a **bidirectional loop**.

### Example in C

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
    struct Node* prev;
};

// Insert at the end
void insert(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;

    if (*head == NULL) {
        *head = newNode;
        newNode->next = newNode;
        newNode->prev = newNode;
    } else {
        struct Node* last = (*head)->prev;
        newNode->next = *head;
        newNode->prev = last;
        last->next = newNode;
        (*head)->prev = newNode;
    }
}

// Print forward (one loop)
void printForward(struct Node* head) {
    if (head == NULL) return;
    struct Node* temp = head;
    do {
        printf("%d <-> ", temp->data);
        temp = temp->next;
    } while (temp != head);
    printf("(back to %d)\n", head->data);
}

int main() {
    struct Node* head = NULL;
    insert(&head, 1);  // 1 <-> (back to 1)
    insert(&head, 2);  // 1 <-> 2 <-> (back to 1)
    insert(&head, 3);  // 1 <-> 2 <-> 3 <-> (back to 1)
    printForward(head); // Output: 1 <-> 2 <-> 3 <-> (back to 1)

    // Free memory (simplified)
    struct Node* temp = head->next;
    while (temp != head) {
        struct Node* next = temp->next;
        free(temp);
        temp = next;
    }
    free(head);
    return 0;
}
```

**Output:**  
`1 <-> 2 <-> 3 <-> (back to 1)`

### How It Works
- **Insertion:** Link the new node between the last node and the head, updating `next` and `prev` pointers.
- **Traversal:** Bidirectional; use `next` or `prev` to loop (**O(n)**).

### Use Cases
- **Playlist with Navigation:** Cycle through songs with "next" and "previous" options.  
  *Example: Music apps with looping playlists.*
- **Multiplayer Game Turns:** Players can move forward or backward in turn order.  
  *Example: Card games with reversible turns.*
- **Memory Management:** Track allocated blocks in a circular structure.  
  *Example: OS kernel managing resources.*

---

## Summary of Types and Use Cases

| Type                     | Key Feature                          | Traversal          | Use Cases                                      |
|--------------------------|--------------------------------------|--------------------|-----------------------------------------------|
| **Singly Linked List**    | Next pointer only                   | Forward only       | Stacks, queues, dynamic lists                 |
| **Doubly Linked List**    | Next and prev pointers              | Bidirectional      | Browser history, undo/redo, playlists         |
| **Circular Singly**       | Last links to first (next only)     | Forward loop       | Round-robin, game turns, buffers              |
| **Circular Doubly**       | Last and first linked both ways     | Bidirectional loop | Playlists, reversible cycles, resources       |

---

## Why Use These Types?
- **Singly:** Simple and memory-efficient for basic needs.
- **Doubly:** Adds flexibility with bidirectional access.
- **Circular (Singly/Doubly):** Ideal for cyclic or looping scenarios.
```
