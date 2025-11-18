# Employee CRUD

Write a modular C program using functions and structures to store and manage employee details. The program should be menu-based.


## JSON Prototype

```json
{
  "employees": [
    {
      "id": 101,
      "name": "Ram Sharma",
      "department": "HR",
      "position": "Manager",
      "salary": 35000.0
    },
    {
      "id": 102,
      "name": "Sita Rai",
      "department": "IT",
      "position": "Developer",
      "salary": 45000.0
    },
    {
      "id": 103,
      "name": "Hari Karki",
      "department": "Finance",
      "position": "Clerk",
      "salary": 20000.0
    }
  ]
}

```
[View JSON Grid](https://jsongrid.com/)

## Basic Setup

```c
#include <stdio.h>
#include <string.h>

#define MAX 100

// ====================== Data Structure ======================

struct Employee 
{
    int id;
    char name[30];
    char department[20];
    char position[20];
    float salary;
};

// Repository Storage
struct Employee emp[MAX];
int count = 0;

// ====================== Global Table Formats ======================

const char *HEADER_FORMAT = "%-5s %-30s %-20s %-20s %-10s\n";
const char *EMP_FORMAT    = "%-5d %-30s %-20s %-20s %-10.2f\n";
```

## Function Prototypes

```c

// ====================== Function Prototypes ======================

// Utility Functions
void readString(char *str, int size);
void printEmployee(struct Employee e);

// Repository Layer
int repo_isFull();
int repo_isEmpty();
int repo_isUniqueID(int id);
int repo_findIndexByID(int id);
void repo_add(struct Employee e);
void repo_update(int index, struct Employee e);
void repo_delete(int index);

// Service Layer
void addEmployee();
void displayEmployees();
void updateEmployee();
void deleteEmployee();
void searchEmployee();
void filterBySalary();

```

## Main Function

```c
// ====================== Main Menu ======================

int main(void) 
{
    int choice;

    do {
        printf("\n==== Employee System ====\n");
        printf("1. Add Employee\n");
        printf("2. Display Employees\n");
        printf("3. Update Employee\n");
        printf("4. Delete Employee\n");
        printf("5. Search Employee by Name\n");
        printf("6. Filter by Salary\n");
        printf("7. Exit\n");
        printf("=========================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        getchar();
        switch (choice) 
        {
            case 1: addEmployee(); break;
            case 2: displayEmployees(); break;
            case 3: updateEmployee(); break;
            case 4: deleteEmployee(); break;
            case 5: searchEmployee(); break;
            case 6: filterBySalary(); break;
            case 7: printf("Exiting...\n"); break;
            default: printf("Invalid choice!\n");
        }

    } while (choice != 7);

    return 0;
}
```

## Program Code

```c
#include <stdio.h>
#include <string.h>

#define MAX 100

// ====================== Data Structure ======================

struct Employee 
{
    int id;
    char name[30];
    char department[20];
    char position[20];
    float salary;
};

// Repository Storage
struct Employee emp[MAX];
int count = 0;

// ====================== Global Table Formats ======================

const char *HEADER_FORMAT = "%-5s %-30s %-20s %-20s %-10s\n";
const char *EMP_FORMAT    = "%-5d %-30s %-20s %-20s %-10.2f\n";

// ====================== Function Prototypes ======================

// Utility Functions
void readString(char *str, int size);
void printEmployee(struct Employee e);

// Repository Layer
int repo_isFull();
int repo_isEmpty();
int repo_isUniqueID(int id);
int repo_findIndexByID(int id);
void repo_add(struct Employee e);
void repo_update(int index, struct Employee e);
void repo_delete(int index);

// Service Layer
void addEmployee();
void displayEmployees();
void updateEmployee();
void deleteEmployee();
void searchEmployee();
void filterBySalary();

// ====================== Main Menu ======================

int main(void) 
{
    int choice;

    do {
        printf("\n==== Employee System ====\n");
        printf("1. Add Employee\n");
        printf("2. Display Employees\n");
        printf("3. Update Employee\n");
        printf("4. Delete Employee\n");
        printf("5. Search Employee by Name\n");
        printf("6. Filter by Salary\n");
        printf("7. Exit\n");
        printf("=========================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        getchar();
        switch (choice) 
        {
            case 1: addEmployee(); break;
            case 2: displayEmployees(); break;
            case 3: updateEmployee(); break;
            case 4: deleteEmployee(); break;
            case 5: searchEmployee(); break;
            case 6: filterBySalary(); break;
            case 7: printf("Exiting...\n"); break;
            default: printf("Invalid choice!\n");
        }

    } while (choice != 7);

    return 0;
}

// ====================== Implementations ======================

// Utility Functions

void readString(char *str, int size) 
{
    fgets(str, size, stdin);
    str[strcspn(str, "\n")] = '\0';
}

void printEmployee(struct Employee e) 
{
    printf(EMP_FORMAT, e.id, e.name, e.department, e.position, e.salary);
}

// Repository Layer

int repo_isFull() 
{
    return (count >= MAX);
}

int repo_isEmpty() 
{
    return (count == 0);
}

int repo_isUniqueID(int id) 
{
    for (int i = 0; i < count; i++)
        if (emp[i].id == id) return 0;
    return 1;
}

int repo_findIndexByID(int id) 
{
    for (int i = 0; i < count; i++)
        if (emp[i].id == id) return i;
    return -1;
}

void repo_add(struct Employee e) 
{
    emp[count++] = e;
}

void repo_update(int index, struct Employee e) 
{
    emp[index] = e;
}

void repo_delete(int index) 
{
    for (int i = index; i < count - 1; i++)
        emp[i] = emp[i + 1];
    count--;
}

// Service Layer

void addEmployee() 
{
    if (repo_isFull()) {
        printf("Employee list full!\n");
        return;
    }

    struct Employee e;
    printf("Enter ID: ");
    scanf("%d", &e.id);
    getchar();

    if (!repo_isUniqueID(e.id)) {
        printf("ID already exists!\n");
        return;
    }

    printf("Enter Name: ");
    readString(e.name, sizeof(e.name));

    printf("Enter Department: ");
    readString(e.department, sizeof(e.department));

    printf("Enter Position: ");
    readString(e.position, sizeof(e.position));

    printf("Enter Salary: ");
    scanf("%f", &e.salary);

    repo_add(e);
    printf("Employee added successfully!\n");
}

void displayEmployees() 
{
    if (repo_isEmpty()) {
        printf("No employees.\n");
        return;
    }

    printf("\n");
    printf(HEADER_FORMAT, "ID", "Name", "Department", "Position", "Salary");

    for (int i = 0; i < count; i++)
        printEmployee(emp[i]);
}

void updateEmployee() 
{
    int id;
    printf("Enter ID to update: ");
    scanf("%d", &id);
    getchar();

    int index = repo_findIndexByID(id);
    if (index == -1) {
        printf("Employee not found!\n");
        return;
    }

    struct Employee e;
    e.id = id;

    printf("Enter new Name: ");
    readString(e.name, sizeof(e.name));

    printf("Enter new Department: ");
    readString(e.department, sizeof(e.department));

    printf("Enter new Position: ");
    readString(e.position, sizeof(e.position));

    printf("Enter new Salary: ");
    scanf("%f", &e.salary);

    repo_update(index, e);
    printf("Employee updated successfully!\n");
}

void deleteEmployee() 
{
	if (repo_isEmpty()) 
	{
        printf("No employees.\n");
        return;
    }
    
    int id;
    printf("Enter ID to delete: ");
    scanf("%d", &id);
    getchar();

    int index = repo_findIndexByID(id);
    if (index == -1) 
    {
        printf("Employee not found!\n");
        return;
    }

    repo_delete(index);
    printf("Employee deleted successfully!\n");
}
```
