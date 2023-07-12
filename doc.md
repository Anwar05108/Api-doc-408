## Student
### Get Courses according to class

Retrieve all courses for a specific class.
- **API Endpoint**: `api/courses?class={class}`
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
        "name": "Mathematics",
        "teacher": "Mr. John Doe"
      },
      {
        "id": 2,
        "name": "Science",
        "teacher": "Ms. Jane Doe"
      },
      ...
    ]
  }
  ```
### Get Courses according to subject

Retrieve all courses for a specific subject.
- **API Endpoint**: `api/courses?subject={subject}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
- **Response Body**:
  ```json
  {
    "subject": "Mathematics",
    "courses": [
      {
        "id": 1,
        "name": "Mathematics 1",
        "teacher": "Mr. John Doe"
      },
      {
        "id": 2,
        "name": "Mathematics 2",
        "teacher": "Ms. Jane Doe"
      },
      ...
    ]
  }
  ```




## Enroll in a course

Enroll a student in a course.
- **API Endpoint**: `/courses/{course_id}/enroll`
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

- **API Endpoint**: `/courses/{course_id}/pay`
- **HTTP Method**: POST
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

## Get Exams
- **API Endpoint**: `api/exams?class={class}`
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

### Subject Wise exams
- **API Endpoint**: `api/exams?subject={subject}`


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

## Teacher

## create mcq exam
- **API Endpoint**: `/exams/create`
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
- **API Endpoint**: `/exams/create`
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


### Get the script of a student
- **API Endpoint**: `/exams/scripts/{exam_id}/{student_id}`
- **HTTP Method**: GET
- **Request Body**: None
- **Status Code**: 200
<!-- the response body will be the data of written document -->
-**Response Body**:
```json
{
  "exam_id": 1,
  "student_id": 1,
  "script": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod, nisl vitae ultricies ultricies, nisl nisl luctus nisl, vitae ultricies nisl",
  "TimeSubmitted": "2021-07-01T12:00:00Z"

}
```


### check the script of a student
- **API Endpoint**: `/exams/scripts`
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

### give grades to the script of a student
- **API Endpoint**: `/exams/scripts`
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











