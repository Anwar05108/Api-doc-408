## Student

### Create Account

Create a new student account.
- **API Endpoint**: `api/student/createAccount`
- **HTTP Method**: POST
- **Status Code**: 201
- **Request Body**:
  ```json
  {
    "name": "John Doe",
    "email": "John@test.com",
    "phone": "1234567890",
    "password": "test123",
    "class": "8",
  }
  ```
- **Response Body**:
  ```json
  {
    "message": "Account created successfully"
  }
  ```


## Get Courses according to class


- **API Endpoint**: `api/student/courses?class={class}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```json
  {
    "class": "8",
    
    "courses": [
      {
        "id": 1,
        "subject": "Mathematics",
        "rating": 4.5,
        "name": "Mathematics 1",
        "description": "This course focuses on the basics of mathematics",
        "price": 1000,
        "no_of_exams": 30,
      },
      {
        "id": 2,
        "subject": "Science",
        "rating": 4.5,
        "name": "Science 1",
        "description": "This course focuses on the basics of science",
        "price": 1200,
        "no_of_exams": 45,
      },
      ...
    ]
  }
  ```
## Get Courses according to subject


- **API Endpoint**: `api/student/subject={subject}&class={class}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```json
  {
    "subject": "Mathematics",
    "class": "8",
    "courses": [
      {
        "id": 1,
        "name": "Mathematics 1",
        "rating": 4.5,
        "description": "This course focuses on the basics of mathematics",
        "price": 1000,
        "no_of_exams": 30,
      },
      {
        "id": 2,
        "name": "Mathematics 2",
        "rating": 4.5,
        "description": "This course focuses on some advanced topics of mathematics",
        "price": 1200,
        "no_of_exams": 45,

      },
      ...
    ]
  }
  ```




## Enroll in a course


- **API Endpoint**: `api/student/courses/{course_id}/enroll`
- **HTTP Method**: POST
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```json
  {
    "message": "Enrolled successfully"
  }
  ```


## Make Payment for a course

- **API Endpoint**: `api/student/courses/{course_id}/pay`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**: 
  ```json
  {
    "amount": 1000
  }
  ```
- **Status Code**: 200
- **Response Body**:
  ```json
  {
    "message": "Payment successful"
  }
  ```

## Get Exams in a course
- **API Endpoint**: `api/student/courses/{course_id}/exams`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "course_id": 1,
  "exams": [
    {
      "id": 1,
      "subject": "Mathematics",
      "type": "MCQ",
      "title": "Math Exam 1",
      "duration": 60,
      "questions": 10,
      "due_date": "2021-05-20T00:00:00.000Z"
    },
    {
      "id": 2,
      "subject": "Mathematics",
      "type": "Written",
      "title": "Math Exam 2",
      "duration": 40,
      "questions": 7,
      "due_date": "2021-05-20T00:00:00.000Z"
    },
    ...
  ]
}
```



## Get Exams
- **API Endpoint**: `api/student/exams?class={class}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```
  {
    "class" = "9",
    "exams": [
      {
        "id": 1,
        "course_id": 1,
        "subject": "Mathematics",
        "type": "MCQ",
        "title": "Math Exam 1",
        "duration": 60,
        "questions": 10
      },
     
      {
        "id": 3,
        "course_id": 1,
        "subject": "Science",
        "type": "Written",
        "title": "Science Exam 1",
        "duration": 40,
        "questions": 7
      }
    ]
    }

## Subject Wise exams
- **API Endpoint**: `api/student/exams?subject={subject}`


- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```
{
   
    "subject" = "Mathematics
    "exams": [
      {
        "id": 1,
        "class": "9",
        "course_id": 1,
        "type": "MCQ",
        "title": "Math Exam 1",
        "duration": 60,
        "questions": 10
      },
     
      {
        "id": 3,
        "class": "9",
        "course_id": 1,
        "type": "Written",
        "title": "Math Exam 2",
        "duration": 40,
        "questions": 7
      }
    ]
}
```


## Give MCQ Exam



- **API Endpoint**: `/api/student/exams/mcq/{exam_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "id": 1,
  "title": "Math Exam",
  "questions": [
    {
      "id": 1,
      "question": "What is 2 + 2?",
      "options": ["3", "4", "5", "6"]
    },
    {
      "id": 2,
      "question": "What is the square root of 16?",
      "options": ["2", "4", "8", "16"]
    },
    ...
  ]
}
```

## Submit MCQ Exam

Submit answers for a specific exam.

- **API Endpoint**: `/api/student/exams/mcq/{exam_id}/submit`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "answers": [
      {
        "question_id": 1,
        "selected_option": "A"
      },
      {
        "question_id": 2,
        "selected_option": "C"
      },
      ...
    ]
  }
- **Response Body**:
    ```json
    {
        "score": 80,
        "total_questions": 10,
        "percentage": 80,
        "correct_answers": 8,
        "incorrect_answers": 2,
        "unanswered": 0,
        "merit_position": 211
    }
    ```


## Give Written Exam

- **API Endpoint**: `/api/student/exams/written/{exam_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
-**Response Body**:
```json
{
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

## Submit Written Exam

Submit answers for a specific exam.

- **API Endpoint**: `/api/student/exams/written/{exam_id}/submit`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "answers": [
      {
        "question_id": 1,
        "answer": "Photosynthesis is the process by which plants make their own food using carbon dioxide, water and sunlight."
      },
      {
        "question_id": 2,
        "answer": "Gravitational waves are disturbances in the curvature of spacetime, generated by accelerated masses, that propagate as waves outward from their source at the speed of light."
      },
      ...
    ]
  }
- **Response Body**:
    ```json
    {
        "message": "Exam submitted successfully"
    }
    ```

## Get Results 
It is for both written or mcq exam.
- **API Endpoint**: `/api/student/exams/{examId}/results`

- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "exam_id": 1,
  "exam_title": "Science Exam",
  "score": 80,
  "total_questions": 10,
  "percentage": 80
}
```


## Request a mentor

- **API Endpoint**: `/api/student/get-mentor`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "subject": "Mathematics"
  }
- **Response Body**:
    ```json
    {
        "message": "Request sent successfully"
    }
    ```


## Chat with Mentor
- **API Endpoint**: `/api/student/chat/{mentor_id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "message": "Hello, I need help in the topic of Algebra."
    "timeStamp": "2021-05-01T12:00:00"
  }

- **Response Body**:
    ```json
    {
        "message": "Message sent successfully"
    }
    ```

- **API Endpoint**: `/api/student/chat/{mentor_id}`
- **HTTP Method**: GET
- **Status Code**: 200
- **Request Body**: None
- **Response Body**:
```json
{
  "message": "In which topic of algebra are you facing problem"
  "timeStamp" : "2021-05-01T12:00:00"
}
```

## Exam Analytics
- **API Endpoint**: `/api/student/analytics/{student_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```json
{
  "student_id": 1,
  "student_name": "John Doe",
  "class": "9",
  "total_exams": 10,
  "total_exams_taken": 5,
  "total_exams_left": 5,
  "average_score": 80,
  "merit_position": 120,  
  "exams": [
    {
      "exam_id": 1,
      "exam_title": "Science Exam",
      "score": 80,
      "total_questions": 10,
      "percentage": 80
    },
    {
      "exam_id": 2,
      "exam_title": "Math Exam",
      "score": 70,
      "total_questions": 10,
      "percentage": 70
    },
    ...
  ]
}
```

## Discussion Forum

Post a question in the discussion forum for a specific exam.
- **API Endpoint**: `/api/student/discussion-forum/{exam-id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "question": "Is the answer of question 3 correct?",
    "timeStamp" : "2021-05-01T12:00:00"
  }

- **Response Body**:
    ```json
    {
        "message": "Question posted successfully"
    }
    ```


Reply to a question in the discussion forum for a specific exam.

- **API Endpoint**: `/api/student/discussion-forum/{exam-id}/{question-id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "reply": "Yes, the answer is correct.",
    "timeStamp" : "2021-05-01T12:00:00"

  }

  ```

- **Response Body**:
    ```json
    {
        "message": "Reply posted successfully"
    }
    ```

## Give rating to course

- **API Endpoint**: `/api/student/rating/{course_id}`
- **HTTP Method**: POST
- **Status Code**: 200
- **Request Body**:
  ```json
  {
    "rating": 4
  }
  ```
- **Response Body**:
    ```json
    {
        "message": "Rating submitted successfully"
    }
    ```

 