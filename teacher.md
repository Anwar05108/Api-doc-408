## Teacher

### Create account

Create a new teacher account.
- **API Endpoint**: `api/teacher/createAccount`
- **HTTP Method**: POST
- **Status Code**: 201
- **Request Body**:
  ```json
  {
    "name": "John Doe",
    "email": "John@teacher.com",
    "phone": "1234567890",
    "password": "test123",
    "mentoring_topics": ["Mathematics", "Physics"]

    }

- **Response Body**:
  ```json
  {
    "message": "Account created successfully"
  }
  ```

## Create mcq exam
- **API Endpoint**: `api/teacher/exams/create`
- **HTTP Method**: POST
- **Request Body**:
  ```json
  {
    "course_id": 1,
    "subject": "Mathematics",
    "class": 11,
    "type": "MCQ",
    "title": "Math Exam 1",
    "duration": 45,
    "questionsNumber": 60,
    "marks": 60,
    "questions": [
      {
        "question": "A triangle has sides of length 12, 14, and 16 units. Find its area.",
        "options": ["72 sq units", "80 sq units", "84 sq units", "90 sq units"],
        "correct_option": "B"
      },
      {
        "question": "Determine the number of primitive roots of 17",
        "options": ["2", "4", "8", "16"],
        "correct_option": "D"
      },
      ...
    ]

  }



- **Response Body**:
    ```json
    {
        "message": "Exam created successfully"
    }
  
    ```

## Create written exam
- **API Endpoint**: `api/teacher/exams/create`
- **HTTP Method**: POST
- **Status Code**: 201
- **Request Body**:
  ```json
  {
    "course_id": 1,
    "subject": "Science",
    "class": "8",
    "type": "Written",
    "title": "Science Exam 1",
    "duration": 60,
    "questionsNumber": 10,
    "questions": [
  {
    "question": "Describe the process of photosynthesis in plants.",
    "marks": 10
  },
  {
    "question": "Explain the concept of gravitational waves.",
    "marks": 10
  },
  ...]
}
    ```
- **Response Body**:
    ```json
    {
        "message": "Exam created successfully"
    }
  
    ```


## Update Exam
- **API Endpoint**: `api/teacher/exams/update/{exam_id}`
- **HTTP Method**: PUT
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "course_id": 1,
    "subject": "Mathematics",
    "class": "8",
    "type": "MCQ",
    "title": "Math Exam 1",
    "duration": 60,
    "questionsNumber": 10,
    "questionsToBeUpdated": 
      {
        "id": 2,
        "question": "What is 2 + 2?",
        "options": ["3", "4", "5", "6"],
        "correct_option": "B"
      } 

  }

## Get scripts of student
- **API Endpoint**: `api/teacher/exams/scripts/`
- **HTTP Method**: GET
- **Status Code**: 200
- **Request Body**: None
- **Response Body**:
    ```json
    {
        "scripts": [
          {
            "student_id": 1,
            "exam_id": 1,
          },
          {
            "student_id": 2,
            "exam_id": 1,
          },

          {
            "student_id": 1,
            "exam_id": 2,
          }
          ...
        ]
    }
    ```

## Get the script of a student
- **API Endpoint**: `api/teacher/exams/scripts/{exam_id}/{student_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200

- **Response Body**:
    ```json
    {
        "script": [
          {
            "question": "Describe the process of photosynthesis in plants."
            "marks": 10
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          {
            "question": "Explain the concept of gravitational waves."
            "marks": 10
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          ...
        ]
    }
    ```




## Evaluate script of a student
- **API Endpoint**: `api/teacher/exams/scripts`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "exam_id": 1
    "student_id": 1
    "answers": [
          {
            "question": "Describe the process of photosynthesis in plants.",
            "marks": 10,
            "marks_obtained": 8,
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          {
            "question": "Explain the concept of gravitational waves.",
            "marks": 10,
            "marks_obtained": 10,
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          ...
        ]
  }

- **Response Body**:
    ```json
    {
        "message": "Grades given successfully"
    }
    ```

## Chat with Student

- **API Endpoint**: `api/teacher/exams/chat/{student_id}`
- **HTTP Method**: GET
- **Status Code**: 200
- **Request Body**: None
- **Response Body**:
```json
{
    "message": "Hello, I need help in the topic of Algebra."
    "timeStamp": "2021-05-01T12:00:00"
}

```







- **API Endpoint**: `api/teacher/exams/chat/{student_id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
```json
 {
  "message": "In which topic of algebra are you facing problem"
  "timeStamp" : "2021-05-01T12:00:00"
}
```
- **Response Body**:
  ```json
    {
        "message": "Message sent successfully"
    }
    ```


## Reply to a qustion of a student in a specific exam

- **API Endpoint**: `api/teacher/exams/chat/{exam-id}/{question-id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
```json
 {
  "message": "Yes the answer is correct"
  "timeStamp" : "2021-05-01T12:00:00"
}
```
- **Response Body**:
  ```json
    {
        "message": "Message sent successfully"
    }
    ```

## Get data of a student activity
- **API Endpoint**: `api/teacher/exams/activity`
- **HTTP Method**: POST
- **Request Body**: 
```json
{
  "exam_id": 14,
  "student_id": 10,
  "tabMinimizedFlag": true,
  "tooManyTabsFlag": true,
  "time": "09/10/2023 12:30:00"
}
```
- **Status Code**: 200
- **Response Body**: None



## Cancel an exam of a student

- **API Endpoint**: `api/teacher/exams/cancel/{exam_id}/{student_id}`
- **HTTP Method**: POST
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
    ```json
    {
        "message": "Exam cancelled successfully"
    }
    ```









