# Structures in C

## Structures

A **structure** in C is a user-defined data type that allows you to combine variables of **different data types** under a single name.

It helps to represent a record or an entity with multiple attributes — for example, a student with `id`, `name`, and `marks`.

It’s how you model real-world entities that have multiple attributes.

A structure is defined using the `struct` keyword.

### Syntax:

```c
struct StructureName 
{
    dataType member1;
    dataType member2;
    ...
};
``` 
**Example:**

```c
struct Student 
{
    int id;
    char name[50];
    float marks;
};

```
**Explanation:**

- `struct` — keyword used to define a structure
- `Student` — name of the structure
- `id`, `name`, `marks` — members (or fields) of the structure
- Each member can have a different data type

### Initializing Structures

#### Structure Initialization:

##### Syntax

```c
struct StructureName variableName = { value1, value2, value3, ... };
```
##### Example

```c
struct Student student = {1, "Sita", 89.5};
```

#### Array of Structures Initialization:

##### Syntax

```c
struct StructureName arrayName[size] = {
    { value1, value2, value3 },
    { value1, value2, value3 },
    ...
};

```
##### Example

```c
struct Student students[3] = {
    {1, "Sita", 89.5},
    {2, "Ram", 92.0},
    {3, "Hari", 76.8}
};

```
### Accessing Structure Members

#### Structure:

```c
struct Student student = {1, "Sita", 89.5};

printf("ID: %d\n", student.id);
printf("Name: %s\n", student.name);
printf("Marks: %.2f\n", student.marks);
```
#### Array of Structures:
```c
struct Student students[3] = {
    {1, "Sita", 89.5},
    {2, "Ram", 92.0},
    {3, "Hari", 76.8}
};

// Access members directly without loop
printf("First student: %s, Marks: %.2f\n", students[0].name, students[0].marks);
printf("Second student: %s, Marks: %.2f\n", students[1].name, students[1].marks);
printf("Third student: %s, Marks: %.2f\n", students[2].name, students[2].marks);
// Access members with loop
for (int i = 0; i < 3; i++) 
{
    printf("Student %d: %s, Marks: %.2f\n", students[i].id, students[i].name, students[i].marks);
}

```

## Real World Example

[**See Unstructured Info**](person-info.md)


### JSON Prototype:

**JSON (JavaScript Object Notation)** is a lightweight text format for representing structured data.  
It is human-readable and language-independent, making it perfect for **quick prototyping** of data models before writing actual code.

```json
{
  "person": 
  {
    "id": 1,
    "name": "Ram Prasad Sharma",
    "age": 35,
    "gender": "M",
    "isMarried": true,
    "height": 5.8,
    "weight": 72.5,
    "hobbies": [ "Reading", "Traveling", "Music" ],
    "luckeynumbers": [ 7, 13, 21, 34, 42, 56, 63, 77, 88, 99 ],
    "birthDate": 
    {
      "day": 15,
      "month": 8,
      "year": 1990
    },
    "address": 
    {
      "street": "123 Main Street",
      "city": "Kathmandu",
      "state": "Bagmati",
      "zipCode": 44600
    },
    "phones": [
      {
        "type": "Mobile",
        "number": "+977-9800000000"
      },
      {
        "type": "Home",
        "number": "01-4412345"
      }
    ],
    "childrens": [
      {
        "name": "Sita Sharma",
        "age": 10,
        "birthDate": 
        {
          "day": 20,
          "month": 5,
          "year": 2015
        },
        "phones": [
          {
            "type": "Mobile",
            "number": "N/A"
          }
        ]
      },
      {
        "name": "Hari Sharma",
        "age": 6,
        "birthDate": 
        {
          "day": 11,
          "month": 2,
          "year": 2019
        },
        "phones": []
      }
    ]
  }
}

```
### Structure in C:

```c
#include <stdbool.h>

struct Date 
{
    int day;
    int month;
    int year;
};

struct Address 
{
    char street[100];
    char city[50];
    char state[50];
    int zipCode;
};

struct Phone 
{
    char type[20];
    char number[20];
};

struct Child 
{
    char name[50];
    int age;
    struct Date birthDate;
    struct Phone phones[10];
};

struct Person 
{
    int id;
    char name[100];
    int age;
    char gender;
    bool isMarried;
    float height;
    double weight;

    char hobbies[3][30];
    int luckyNumbers[10];

    struct Date birthDate;
    struct Address address;
    struct Phone phones[10];
    struct Child children[10];
};

```
## Task:

- [**Structure Task**](structure-task.md)
