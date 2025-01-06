# TASK: Create a "Codinggita Students" database

## Create a new MongoDB database called CodingGita. Add two collections:

```js
use codinggita
```

```js
db.createCollection("students");
```

```js
db.createCollection("subjects");
```

## Insert multipledata in both collections


# Task 1: Add multiple students
```js
db.students.insertMany([
  { 
    "name": "Dev",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS", "MongoDB"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Circuit Theory", "Electrical Machines"]
  },
  { 
    "name": "Kalpan",
    "rollNumber": 104,
    "department": "Computer Science",
    "year": 3,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  { 
    "name": "Dax",
    "rollNumber": 105,
    "department": "Electrical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Circuit Theory", "Electrical Machines"]
  }
]);
```


# Task 2: Add multiple subjects
**Add data in "subjects" collection;
```js
db.subjects.insertMany([
  { 
    "subjectName": "React",
    "topics": [
      "JSX", 
      "Components", 
      "State", 
      "Props", 
      "Hooks"
    ]
  },
  { 
    "subjectName": "NodeJS", 
    "topics": [
      "Modules", 
      "Express", 
      "File System", 
      "Asynchronous Programming"
    ]
  },
  { 
    "subjectName": "MongoDB", 
    "topics": [
      "Database Design", 
      "CRUD Operations", 
      "Aggregation", 
      "Indexes"
    ]
  }
]);
```

# Task 3: Query students based on subject enrollment

**Query the students collection to find all students who are enrolled in NodeJS.

```js
db.students.find({ "coursesEnrolled": "NodeJS" });
```


# Task 4: Add a new topic to a subject

**Add a new topic to the NodeJS subject.

```js
db.courses.updateOne(
  { "courseCode": "NodeJS" },  
  { $push: { "topics": "Asynchronous Programming" } }  
);
```


# Task 5: Query subjects with multiple topics

**Query the subjects collection to find subjects that contain at least 4 topics.

```js
db.subjects.find({
  "topics": { $size: { $gte: 4 } }
});
```

# Task 6: Update student enrollment

**Add the subject "React Native" to Dev's subjects.

```js
db.students.updateOne(
  { "name": "Dev Patel" },  
  { $push: { "subjects": "React Native" } }  
);
```

# Task 7: Query all students 

**Query all students in the database and print out their names and enrolled subjects.

```js
db.students.find({}, { "name": 1, "coursesEnrolled": 1 });
```

# Task 8: Update multiple students' year

**Update the year for all students in the Computer Science department to year 3.

```js
db.students.updateMany(
  { "department": "Computer Science" },
  { $set: { "year": 3 } }
);
```

# Task 9: Add new topics to multiple subjects

**Add new topics to React, NodeJS, and MongoDB subjects. Ensure each subject gets at least one new topic.

```js
db.courses.updateOne(
  { "courseCode": "React" },
  { $push: { "topics": "React Hooks" } }
);

db.courses.updateOne(
  { "courseCode": "NodeJS" },
  { $push: { "topics": "Express.js" } }
);

db.courses.updateOne(
  { "courseCode": "MongoDB" },
  { $push: { "topics": "Aggregation Framework" } }
);
```

# Task 10: Remove a topic from a subject

**Remove the topic "Express" from the NodeJS subject.

```js
db.courses.updateOne(
  { "courseCode": "NodeJS" },
  { $pull: { "topics": "Express" } }
);
```

# Task 11: Query all students in a specific year

**Query and return all students in year 2 or year 3.

```js
db.students.find({ "year": { $in: [2, 3] } });
```

# Task 12: Delete a student by roll number

**Delete a student from the database using their roll number.

```js
db.students.deleteOne({ "rollNumber": 101 });
```

# Task 13: Delete all students from a department

**Delete all students who belong to the Electrical Engineering department.

```js
db.students.deleteMany({ "department": "Electrical Engineering" });
```

# Task 14: Retrieve all topics for a subject

**Query the MongoDB subject and retrieve all topics listed for it.

```js
db.courses.find({ "courseCode": "MongoDB" }, { "topics": 1 });
```

# Task 15: Count the number of subjects in which a student is enrolled

**Write a query that returns the number of subjects each student is enrolled in.

```js
db.students.aggregate([
  { $project: { name: 1, coursesCount: { $size: "$coursesEnrolled" } } }
]);
```