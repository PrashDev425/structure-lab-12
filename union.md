# Union in C

## What is Union in C?
A **union** in C is a special data type that allows you to **store different data types in the same memory location**.  
It is similar to a `struct`, but **all members share the same memory space**, meaning **only one member can hold a value at a time**.

---

## Syntax of a Union
```c
union UnionName {
    dataType member1;
    dataType member2;
    dataType member3;
};
```
To declare and use:
```c
union UnionName variableName;
```

---

## Example: Using a Union
```c
#include <stdio.h>
#include <string.h>

union Data 
{
    int i;
    float f;
    char str[20];
};

int main(void) 
{
    union Data data;

    // Store an integer
    data.i = 10;
    printf("data.i = %d\n", data.i);

    // Store a float (overwrites integer)
    data.f = 220.5;
    printf("data.f = %.2f\n", data.f);

    // Store a string (overwrites float)
    strcpy(data.str, "Hello");
    printf("data.str = %s\n", data.str);

    // Notice that previous values are lost because memory is shared
    return 0;
}
```

---

## Example Showing Size
```c
#include <stdio.h>

union Test 
{
    int a;
    double b;
    char c;
};

int main(void) 
{
    printf("Size of union = %lu bytes\n", sizeof(union Test));
    return 0;
}
```

---

## Use Cases
- Saving memory when multiple data types are used but not at the same time.  
- Useful in **embedded systems** and **interpreting raw data** (like in networking or device drivers).
