### Student
## API Endpoint: `/exams?grade={grade}`

- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```
  {
    "class" = 9,
    "exams": [
      {
        "id": 1,
        "subject": "Mathematics",
        "type": "MCQ",
        "title": "Math Exam 1",
        "duration": 60,
        "questions": 10
      },
     
      {
        "id": 3,
        "subject": "Science",
        "type": "Written",
        "title": "Science Exam 1",
        "duration": 40,
        "questions": 7
      }
    ]
    }


## API Endpoint: `/exams?subject={subject}&class={class}`

- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
```
{
    "class" = 9,
    "subject" = "Mathematics
    "exams": [
      {
        "id": 1,
        "subject": "Mathematics",
        "type": "MCQ",
        "title": "Math Exam 1",
        "duration": 60,
        "questions": 10
      },
     
      {
        "id": 3,
        "subject": "Mathematics",
        "type": "Written",
        "title": "Math Exam 2",
        "duration": 40,
        "questions": 7
      }
    ]
}
```


## Give Exam

Retrieve details of a specific exam for the student to attempt.

- **API Endpoint**: `/exams/{exam_id}`
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
      "text": "What is 2 + 2?",
      "options": ["3", "4", "5", "6"]
    },
    {
      "id": 2,
      "text": "What is the square root of 16?",
      "options": ["2", "4", "8", "16"]
    },
    ...
  ]
}
```

## Submit Exam

Submit answers for a specific exam.

- **API Endpoint**: `/exams/{exam_id}/submit`
- **HTTP Method**: POST
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
        "percentage": 80
    }
    ```







