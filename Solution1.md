# TASK 1: Create a "Codinggita Students" database

## Create a new MongoDB database called CodingGita. Add two collections:

```js
use codinggita
```

```js
db.createCollection("students");
```

```js
db.createCollection("courses");
```

## Insert multipledata in both collections


**Add data in "students" collection;
```js
db.students.insertMany([
  { 
    "name": "Dev",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Kalpan",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);
```



**Add data in "courses" collection;
```js
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Sharma" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Gupta" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Kapoor" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Verma" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Yadav" 
  }
]);
```


# TASK 2: Perform CRUD operation

## Add few more students and courses;

** Add data in "students";

```js
db.students.insertMany([
  { 
    "name": "Dax",
    "rollNumber": 104,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Jenil",
    "rollNumber": 105,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Mohit",
    "rollNumber": 106,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);
```

**search data based on querries

### search student based on department
```js
db.students.find({ "department": "Computer Science" });
```

### search student based on year
```js
db.students.find({ "year": 2 });
```

### search student based on course enrolled
```js
db.students.find({ "coursesEnrolled": "CS101" });
```

### Update the courses for a specific student (e.g., adding a new course).
```js
db.students.updateOne(
  { "name": "Kalpan" },  
  { $push: { "coursesEnrolled": "CS102" } }  
);
```

### Delete a student or course from the database.
```js
db.students.deleteMany({ "department": "Electrical Engineering" });
```