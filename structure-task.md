# Structure Task:

- [View JSON Grid](https://jsongrid.com/)

## Simple Array 

### JSON Prototype:

```json
{
  "marks": [85, 90, 78, 88, 92]
}

```

### Program:

```c
#include <stdio.h>

int main(void) 
{
    int marks[5] = {85, 90, 78, 88, 92};
    int i;
    printf("Student Marks:\n");
    for (i = 0; i < 5; i++) 
    {
        printf("Student %d: %d\n", i + 1, marks[i]);
    }
    return 0;
}
```


## Array Within a Structure

### JSON Prototype:

```json
{
  "student": {
    "id": 1,
    "name": "Sita",
    "marks": [85, 90, 88]
  }
}

```

### Program:
```c
#include <stdio.h>

struct Student 
{
    int id;
    char name[50];
    int marks[3];
};

int main(void) 
{
    struct Student student = {1, "Sita", {85, 90, 88}};
    int i;
    printf("Student ID: %d\n", student.id);
    printf("Name: %s\n", student.name);
    printf("Marks:\n");
    printf("======\n");
    for (i = 0; i < 3; i++) {
        printf("%d ", student.marks[i]);
    }
    return 0;
}
```
## Array of Structures

### JSON Prototype:

```json
{
  "students": [
    {
      "id": 1,
      "name": "Aayush",
      "marks": 88.5
    },
    {
      "id": 2,
      "name": "Bina",
      "marks": 92
    },
    {
      "id": 3,
      "name": "Chirag",
      "marks": 79.5
    }
  ]
}
```
### Program:
```c
#include <stdio.h>

struct Student 
{
    int id;
    char name[50];
    float marks;
};

int main(void) 
{
    struct Student students[3] = 
    {
        {1, "Aayush", 88.5},
        {2, "Bina", 92.0},
        {3, "Chirag", 79.5}
    };
    for (int i = 0; i < 3; i++) {
        printf("Student %d:\n", i + 1);
        printf("=======\n");
        printf("ID: %d\n", students[i].id);
        printf("Name: %s\n", students[i].name);
        printf("Marks: %.2f\n", students[i].marks);
    }
    return 0;
}

```

## Nested Structures

### JSON Prototype:

```json
{
  "student": {
    "id": 1,
    "name": "Krishna",
    "address": {
      "city": "Kathmandu",
      "country": "Nepal"
    }
  }
}
```
### Program:

```c
#include <stdio.h>

struct Address 
{
    char city[30];
    char country[30];
};

struct Student 
{
    int id;
    char name[50];
    struct Address address;
};

int main(void) 
{
    struct Student student = {1, "Krishna", {"Kathmandu", "Nepal"}};
    printf("Student ID: %d\n", student.id);
    printf("Name: %s\n", student.name);
    printf("Address:\n");
    printf("========\n");
    printf("City: %s\n", student.address.city);
    printf("Country: %s\n", student.address.country);
    return 0;
}

```
## Array of Structures Within a Structure

### JSON Prototype:

```json
{
  "student": {
    "id": 1,
    "name": "Aayush Sharma",
    "subjects": [
      { 
        "name": "Math", 
        "marks": 88 
      },
      { 
        "name": "Physics", 
        "marks": 92 
      },
      { 
        "name": "Chemistry", 
        "marks": 79 
      }
    ]
  }
}
```

### Program:

```
Do Yourself
```
