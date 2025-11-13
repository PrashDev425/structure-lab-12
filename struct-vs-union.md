# Struct vs Union

| **Feature** | **Structure (`struct`)** | **Union (`union`)** |
|--------------|--------------------------|---------------------|
| **Memory Allocation** | Each member has its **own memory**. Total size = sum of all members. | All members **share the same memory**. Total size = size of the **largest member**. |
| **Data Storage** | Can store **different values** in all members **at the same time**. | Can store **only one value at a time** (shared memory). |
| **Usage** | Used when you need to keep **all members active together**. | Used when you need to store **one of many possible data types**. |
| **Initialization** | All members can be initialized separately. | Only the **first member** can be initialized during declaration. |
| **Memory Efficiency** | Uses **more memory**. | Uses **less memory** (memory-saving). |
| **Memory Example** | Separate memory for each member. | All members share the same memory. |
| **Access** | All members can be accessed at the same time. | Only **one member’s value** is valid at a time. |

## Struct and Union Storge Comparison

```c
#include <stdio.h>

struct Student 
{
    int id;        // 4 bytes
    float marks;   // 4 bytes
    char grade;    // 1 byte
};

union Data 
{
    int id;        // 4 bytes
    float marks;   // 4 bytes
    char grade;    // 1 byte
};

int main(void) 
{
    struct Student s1;
    union Data d1;
    printf("Size of int: %lu bytes\n", sizeof(int));
    printf("Size of float: %lu bytes\n", sizeof(float));
    printf("Size of char: %lu bytes\n\n", sizeof(char));
    printf("Size of Structure: %lu bytes\n", sizeof(s1));
    printf("Size of Union: %lu bytes\n", sizeof(d1));
    return 0;
}
```
