# Tyr DB Schema

## Mongo Collection Types

-  Users
-  Courses
-  Assignments
-  Submissions

### Users Collection

```json
{
   "_id": ObjectId,
   "email": String,
   "firstName": String,
   "lastName": String,
   "password": String,
   "enrolledCourses": [
      {
         "courseID": Courses._id,
         "enrollmentType": String
      }
   ]
}
```

### Courses Collection

```json
{
   "_id": ObjectId,
   "department": String,
   "number": Number,
   "section": String,
   "professors": [Users._id],
   "assistants": [Users._id],
   "students": [Users._id],
   "assignments": [Assignments._id]
}
```

### Assignments Collection

```json
{
   "_id": ObjectId,
   "name": String,
   "description": String,
   "supportingFiles": String,
   "dueDate": ISODate,
   "published": Boolean,
   "testScripts": {
      "studentFacing": String,
      "adminFacing": String
   },
   "submissions": [Submissions._id]
}
```

### Submissions

```json
{
   "_id": ObjectID,
   "userId": Users._id,
   "submissionDate": ISODate,
   "file": String,
   "errorTesting": Boolean,
   "cases": {
      "studentFacing": {
         "pass": Number,
         "fail": Number
      },
      "adminFacing": {
         "pass": Number,
         "fail": Number
      }
   }
}
```
