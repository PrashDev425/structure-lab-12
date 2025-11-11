# Employee CRUD

Write a C program to store and manage employee details using structure.


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

## Program Code

```c
#include <stdio.h>
#include <string.h>

#define MAX 100

struct Employee 
{
    int id;
    char name[30];
    char department[20];
    char position[20];
    float salary;
};

struct Employee emp[MAX];
int count = 0;

void addEmployee(); // Add employee
void displayEmployees(); // Display employees
void updateEmployee(); // Update employee
void deleteEmployee(); // Delete employee
void searchEmployee(); // Search employee by name
void filterBySalary(); // Filter employees by salary
int isUniqueID(int id); // Check unique ID

int main(void) 
{
    int choice;
    do 
    {
        printf("\n=== Employee System ===\n");
        printf("1. Add Employee\n");
        printf("2. Display All Employees\n");
        printf("3. Update Employee\n");
        printf("4. Delete Employee\n");
        printf("5. Search Employee by Name\n");
        printf("6. Filter Employees by Salary\n");
        printf("7. Exit\n");
        printf("=============================\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice) 
        {
            case 1:
                addEmployee();
                break;
            case 2:
                displayEmployees();
                break;
            case 3:
                break;
            case 4:
                break;
            case 5:
                break;
            case 6:
                break;
            case 7:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 7);

    return 0;
}

int isUniqueID(int id) 
{
    for (int i = 0; i < count; i++)
        if (emp[i].id == id) return 0;
    return 1;
}

void addEmployee() 
{
    if (count >= MAX) 
    {
        printf("Employee list full!\n");
        return;
    }

    int id;
    printf("Enter ID: ");
    scanf("%d", &id);

    if (!isUniqueID(id)) 
    {
        printf("ID already exists!\n");
        return;
    }

    emp[count].id = id;

    getchar(); // clear newline left by scanf

    printf("Enter Name: ");
    fgets(emp[count].name, sizeof(emp[count].name), stdin);
    emp[count].name[strcspn(emp[count].name, "\n")] = '\0'; // remove newline

    printf("Enter Department: ");
    fgets(emp[count].department, sizeof(emp[count].department), stdin);
    emp[count].department[strcspn(emp[count].department, "\n")] = '\0';

    printf("Enter Position: ");
    fgets(emp[count].position, sizeof(emp[count].position), stdin);
    emp[count].position[strcspn(emp[count].position, "\n")] = '\0';

    printf("Enter Salary: ");
    scanf("%f", &emp[count].salary);

    count++;
    printf("Employee added successfully!\n");
}

void displayEmployees() 
{
    if (count == 0) 
    {
        printf("No employees to show.\n");
        return;
    }
    printf("\n%-5s %-30s %-20s %-20s %-10s\n", "ID", "Name", "Department", "Position", "Salary");
    for (int i = 0; i < count; i++) {
        printf("%-5d %-30s %-20s %-20s %-10.2f\n",
            emp[i].id,
            emp[i].name,
            emp[i].department,
            emp[i].position,
            emp[i].salary);
    }
}
```
