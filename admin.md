## Admin


## Add a course
- **API Endpoint**: `/api/admin/courses/add`
- **HTTP Method**: POST
- **Status Code**: 201
- **Request Body**:
```json
{
  "name": "Mathematics",
  "description": "Mathematics course for class 8",
  "class": "8"
}

```

- **Response Body**:
```json
{
  "message": "Course created successfully"
}
```

## Get all students
- **API Endpoint**: `/api/admin/students`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "students": [
    {
      "id": 1,
      "name": "John Doe",
      "class": "8",
      "roll": 1,
      "email": "John@test.com"
     
    },
    {
      "id": 2,
      "name": "Jane Doe",
      "class": "8",
      "roll": 2,
      "email": "Jane@test.com"
    },
    ...
    ]
}

```

## Get details of a student
- **API Endpoint**: `/api/admin/students/{id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "id": 1,
  "name": "John Doe",
  "class": "8",
  "roll": 1,
  "email": "John@gmail.com",
  "phone": "1234567890",
  "courses": [
    {
      "id": 1,
      "name": "Mathematics",
      
    },
    {
      "id": 2,
      "name": "Science",
      
    },
    ...
  ]
}
```

## Get all teachers

- **API Endpoint**: `/api/admin/teachers`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "teachers": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "John@teacher.com",
      "phone": "1234567890"
    },
    {
      "id": 2,
      "name": "Jane Doe",
      "email": "Jane@teacher.com",
      "phone": "1234567890"
    },
    ...
    ]
}
```


## Get details of a teacher

- **API Endpoint**: `/api/admin/teachers/{id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "id": 1,
  "name": "John Doe",
  "email": "John@teacher.com",
  "phone": "1234567890",
  "dueTasks":
  [
    {
    "exam_id": 1,
    "student_id": 1,
    },
    {
    "exam_id": 2,
    "student_id": 1,
    },
  ]
}
```


## See exams 
- **API Endpoint**: `/api/admin/exams`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "exams": [
    {
      "id": 1,
      "name": "Mathematics",
      "class": "8",
      "subject": "Mathematics",
      "teacher_id": 1,
      "date": "2021- 05- 01",
      "time": "10:00:00",
      "type": "MCQ",
      "duration": 60,
      "total_marks": 100,
      "passing_marks": 40
    },
    {
      "id": 2,
      "name": "Science",
      "class": "8",
      "subject": "Science",
      "teachear_id": 2,
      "date": "2021- 05- 01",
      "time": "10:00:00",
      "type": "written",
      "duration": 60,
      "total_marks": 100,
      "passing_marks": 40
    },
    ...
    ]
}
```


    
