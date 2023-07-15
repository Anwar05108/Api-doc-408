## Teacher

### Create account

Create a new teacher account.
- **API Endpoint**: `api/teacher/createAccount`
- **HTTP Method**: POST
- **Status Code**: 200
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

## create mcq exam
- **API Endpoint**: `api/teacher/exams/create`
- **HTTP Method**: POST
- **Request Body**:
  ```json
  {
    "course_id": 1,
    "subject": "Mathematics",
    "type": "MCQ",
    "title": "Math Exam 1",
    "duration": 60,
    "questionsNumber": 10,
    "questions": [
      {
        "text": "What is 2 + 2?",
        "options": ["3", "4", "5", "6"],
        "correct_option": "B"
      },
      {
        "text": "What is the square root of 16?",
        "options": ["2", "4", "8", "16"],
        "correct_option": "B"
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

## create written exam
- **API Endpoint**: `api/teacher/exams/create`
- **HTTP Method**: POST
- **Request Body**:
  ```json
  {
    "course_id": 1,
    "subject": "Mathematics",
    "type": "Written",
    "title": "Math Exam 1",
    "duration": 60,
    "questionsNumber": 10,
    "questions": [
  {
    "text": "Describe the process of photosynthesis in plants."
    marks": 10
  },
  {
    "text": "Explain the concept of gravitational waves."
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


## Get the script of a student
- **API Endpoint**: `api/teacher/exams/scripts/{exam_id}/{student_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200

-**Response Body**:
```json
{
  "exam_id": 1,
  "student_id": 1,
  "script": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl",
  "TimeSubmitted": "2021-07-01T12:00:00Z"

}
```


## check the script of a student
- **API Endpoint**: `api/teacher/exams/scripts`
- **HTTP Method**: POST
- **Request Body**:
  ```json
  {
    "exam_id": 1
    "student_id": 1
  }
- **Response Body**:
    ```json
    {
        "answers": [
          {
            "text": "Describe the process of photosynthesis in plants."
            "marks": 10
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          {
            "text": "Explain the concept of gravitational waves."
            "marks": 10
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          ...
        ]
    }
    ```

## give grades to the script of a student
- **API Endpoint**: `api/teacher/exams/scripts`
- **HTTP Method**: POST
- **Request Body**:
  ```json
  {
    "exam_id": 1
    "student_id": 1
    "answers": [
          {
            "text": "Describe the process of photosynthesis in plants."
            "marks": 10
            "marks_obtained": 8
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          {
            "text": "Explain the concept of gravitational waves."
            "marks": 10
            "marks_obtained": 10
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl"
          },
          ...
        ]
  }











