# MongoDB Tasks

## Task 1: Add more students to the students collection;

***Add at least 5 new students to the students collection with unique names, roll numbers, and course enrollments.
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
  },
  {
    "name": "Dev Patel",
    "rollNumber": "CSE1010",
    "department": "Computer Science",
    "year": 1,
    "coursesEnrolled": ["CS101", "CS102", "Math101"]
  },
  {
    "name": "Dharti Raval",
    "rollNumber": "ECE3005",
    "department": "Electronics",
    "year": 3,
    "coursesEnrolled": ["EC201", "CS101"]
  }
]);
```


## Task 2: Insert a new course into the courses collection

**Add a new course with the following details:
**Course Code: CS202
**Name: Data Structures
**Credits: 3
**Instructor: Prof. Krishna;

```js
db.courses.insertOne({
    "courseCode": "CS202",
    "name": "Data Structures",
    "credits": 3,
    "instructor": "Prof. Krishna"
});
```


## Task 3: Fetch a specific student's record by roll number;

**Use find() to fetch a student's information using their roll number (CS1002).

```js
db.students.find({ rollNumber: "CS1002" });
```


## Task 4: Query all students who are enrolled in a particular course

**Retrieve all students who are enrolled in "MATH101".

```js
db.students.find({ coursesEnrolled: "MATH101" });
```


## Task 5: Update a student's courses

**Update the student with roll number CS1001 to enroll in an additional course "CS202".

```js
db.students.updateOne(
    { rollNumber: "CS1001" },
    {
        $push: { coursesEnrolled: "CS202" };
    };
);
```


## Task 6: Remove a course from a student's courses list

**Remove the course MATH101 from the student Mahir's list of enrolled courses.

```js
db.students.updateOne(
    { rollNumber: "CS1001" },
    { $pull: { coursesEnrolled: "MATH101" } };
);
```


## Task 7: Find all courses with 3 credits

**Query the courses collection to find all courses where the credits field equals 3.

```js
db.courses.find({ credits: 3 });
```


## Task 8: Find students who have enrolled in more than 2 courses

**Use $size operator to query students who are enrolled in more than 2 courses.

```js
db.students.find({ coursesEnrolled: { $size: { $gt: 2 } } });
```


## Task 9: Use the $in operator to find students enrolled in multiple courses

**Use the $in operator to find students who are enrolled in either CS101 or MATH202.

```js
db.students.find({ coursesEnrolled: { $in: ["CS101", "MATH202"] } });
```


## Task 10: Fetch all students from a specific department (e.g., CSE);

**Use a query to find all students in the CSE department.

```js
db.students.find({ department: "Computer Science" });