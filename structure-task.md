# Structure Task:

## Simple Array 

### JSON Prototype:

```json
{
  "marks": [85, 90, 78, 88, 92]
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
