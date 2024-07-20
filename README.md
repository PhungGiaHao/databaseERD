# University Database Design
This repository contains the design and structure of a comprehensive university database. The database is intended to manage various aspects of university operations, including student enrollment, faculty assignments, courses, research projects, and more.
## Overview
The database is designed to handle:
- Student and faculty information
- Course and enrollment details
- Research projects and related publications and grants
- Various student services such as career counseling and mental health support
- Library resources and student organizations
- Building facilities management
## Entity Relationship Diagram (ERD)
**Open with drawio**
[ERD](https://drive.google.com/file/d/13gVax-Wpt-Cz1b2n6AIK8vevdWWaXR1h/view?usp=sharing)
**Image**
[database drawio](https://github.com/user-attachments/assets/d5120bf4-aa95-463d-ba7a-c4eb2b0d375f)
## Entities and Attributes
### Student
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| student_id     | INT           | Primary Key, Auto Increment        |
| first_name     | VARCHAR(50)   | Student's first name               |
| last_name      | VARCHAR(50)   | Student's last name                |
| email          | VARCHAR(100)  | Unique, Student's email address    |
| phone_number   | VARCHAR(15)   | Student's phone number             |
| date_of_birth  | DATE          | Student's date of birth            |
| enrollment_date| DATE          | Date of student's enrollment       |

### Faculty
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| faculty_id     | INT           | Primary Key, Auto Increment        |
| first_name     | VARCHAR(50)   | Faculty's first name               |
| last_name      | VARCHAR(50)   | Faculty's last name                |
| email          | VARCHAR(100)  | Unique, Faculty's email address    |
| phone_number   | VARCHAR(15)   | Faculty's phone number             |
| hire_date      | DATE          | Date of faculty's hire             |
| department_id  | INT           | Foreign Key, references Department(department_id) |

### Department
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| department_id  | INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Unique, Department name            |
| head           | INT           | Foreign Key, references Faculty(faculty_id) |

### Course
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| course_id      | INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Course name                        |
| description    | TEXT          | Course description                 |
| credits        | INT           | Number of credits                  |
| department_id  | INT           | Foreign Key, references Department(department_id) |

### Enrollment
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| enrollment_id  | INT           | Primary Key, Auto Increment        |
| student_id     | INT           | Foreign Key, references Student(student_id) |
| course_id      | INT           | Foreign Key, references Course(course_id) |
| semester       | VARCHAR(10)   | Semester of enrollment             |
| year           | YEAR          | Year of enrollment                 |
| grade          | VARCHAR(2)    | Grade received                     |

### Research Project
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| research_id    | INT           | Primary Key, Auto Increment        |
| faculty_id     | INT           | Foreign Key, references Faculty(faculty_id) |
| title          | VARCHAR(100)  | Research project title             |
| description    | TEXT          | Research project description       |
| start_date     | DATE          | Start date of the project          |
| end_date       | DATE          | End date of the project            |

### Publication
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| publication_id | INT           | Primary Key, Auto Increment        |
| research_id    | INT           | Foreign Key, references Research_Project(research_id) |
| title          | VARCHAR(100)  | Publication title                  |
| type           | VARCHAR(50)   | Type of publication                |
| publication_date | DATE        | Date of publication                |
| publisher      | VARCHAR(100)  | Publisher name                     |

### Grant
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| grant_id       | INT           | Primary Key, Auto Increment        |
| research_id    | INT           | Foreign Key, references Research_Project(research_id) |
| name           | VARCHAR(100)  | Grant name                         |
| amount         | DECIMAL(10,2) | Grant amount                       |
| funding_agency | VARCHAR(100)  | Funding agency                     |
| start_date     | DATE          | Start date of the grant            |
| end_date       | DATE          | End date of the grant              |

### Career Counseling
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| counseling_id  | INT           | Primary Key, Auto Increment        |
| student_id     | INT           | Foreign Key, references Student(student_id) |
| counseling_date| DATE          | Date of counseling session         |
| description    | TEXT          | Description of the session         |

### Mental Health Support
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| support_id     | INT           | Primary Key, Auto Increment        |
| student_id     | INT           | Foreign Key, references Student(student_id) |
| support_date   | DATE          | Date of support session            |
| description    | TEXT          | Description of the session         |

### Financial Transaction
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| transaction_id | INT           | Primary Key, Auto Increment        |
| student_id     | INT           | Foreign Key, references Student(student_id) |
| amount         | DECIMAL(10,2) | Transaction amount                 |
| transaction_date | DATE        | Date of transaction                |
| description    | TEXT          | Description of the transaction     |

### Scholarship
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| scholarship_id | INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Scholarship name                   |
| amount         | DECIMAL(10,2) | Scholarship amount                 |
| student_id     | INT           | Foreign Key, references Student(student_id) |

### Library
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| library_id     | INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Library name                       |
| location       | VARCHAR(100)  | Library location                   |

### Book
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| book_id        | INT           | Primary Key, Auto Increment        |
| library_id     | INT           | Foreign Key, references Library(library_id) |
| title          | VARCHAR(100)  | Book title                         |
| author         | VARCHAR(100)  | Book author                        |
| isbn           | VARCHAR(20)   | Unique, Book ISBN                  |
| publication_year | YEAR        | Year of publication                |

### Journal
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| journal_id     | INT           | Primary Key, Auto Increment        |
| library_id     | INT           | Foreign Key, references Library(library_id) |
| title          | VARCHAR(100)  | Journal title                      |
| volume         | INT           | Volume number                      |
| issue          | INT           | Issue number                       |
| publication_year | YEAR        | Year of publication                |

### Digital Resource
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| resource_id    | INT           | Primary Key, Auto Increment        |
| library_id     | INT           | Foreign Key, references Library(library_id) |
| title          | VARCHAR(100)  | Resource title                     |
| url            | VARCHAR(255)  | Resource URL                       |

### Student Organization
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| organization_id| INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Unique, Organization name          |
| description    | TEXT          | Organization description           |

### Club
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| club_id        | INT           | Primary Key, Auto Increment        |
| organization_id| INT           | Foreign Key, references Student_Organization(organization_id) |
| name           | VARCHAR(100)  | Unique, Club name                  |
| description    | TEXT          | Club description                   |

### Building
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| building_id    | INT           | Primary Key, Auto Increment        |
| name           | VARCHAR(100)  | Unique, Building name              |
| location       | VARCHAR(100)  | Building location                  |

### Classroom
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| classroom_id   | INT           | Primary Key, Auto Increment        |
| building_id    | INT           | Foreign Key, references Building(building_id) |
| room_number    | VARCHAR(10)   | Room number                        |
| capacity       | INT           | Room capacity                      |

### Laboratory
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| lab_id         | INT           | Primary Key, Auto Increment        |
| building_id    | INT           | Foreign Key, references Building(building_id) |
| room_number    | VARCHAR(10)   | Room number                        |
| capacity       | INT           | Room capacity                      |

### Office
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| office_id      | INT           | Primary Key, Auto Increment        |
| building_id    | INT           | Foreign Key, references Building(building_id) |
| room_number    | VARCHAR(10)   | Room number                        |

### Common Area
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| area_id        | INT           | Primary Key, Auto Increment        |
| building_id    | INT           | Foreign Key, references Building(building_id) |
| description    | TEXT          | Area description                   |

### Payroll
| Attribute      | Data Type     | Description                        |
|----------------|---------------|------------------------------------|
| payroll_id     | INT           | Primary Key, Auto Increment        |
| faculty_id     | INT           | Foreign Key, references Faculty(faculty_id) |
| amount         | DECIMAL(10,2) | Payment amount                     |
| payment_date   | DATE          | Date of payment                    |
| description    | TEXT          | Payment description                |

## Relationships

### Department and Faculty
- **One-to-Many**: A department can have multiple faculty members.
- **Foreign Key**: `department_id` in Faculty refers to `department_id` in Department.

### Department and Course
- **One-to-Many**: A department can offer multiple courses.
- **Foreign Key**: `department_id` in Course refers to `department_id` in Department.

### Faculty and Research_Project
- **One-to-Many**: A faculty member can lead multiple research projects.
- **Foreign Key**: `faculty_id` in Research_Project refers to `faculty_id` in Faculty.

### Research_Project and Publication
- **One-to-Many**: A research project can have multiple publications.
- **Foreign Key**: `research_id` in Publication refers to `research_id` in Research_Project.

### Research_Project and Grant
- **One-to-Many**: A research project can receive multiple grants.
- **Foreign Key**: `research_id` in Grant refers to `research_id` in Research_Project.

### Student and Course
- **Many-to-Many**: A student can enroll in multiple courses, and a course can have multiple students.
- **Associative Entity**: Enrollment table with `student_id` and `course_id` as foreign keys referring to Student and Course respectively.

### Course and Assignment/Quiz/Exam/Project
- **One-to-Many**: A course can have multiple assignments, quizzes, exams, and projects.
- **Foreign Key**: `course_id` in Assignment, Quiz, Exam, and Project refers to `course_id` in Course.

### Student and Career_Counseling/Mental_Health_Support/Financial_Transaction/Scholarship
- **One-to-Many**: A student can have multiple counseling sessions, support, transactions, and scholarships.
- **Foreign Key**: `student_id` in Career_Counseling, Mental_Health_Support, Financial_Transaction, and Scholarship refers to `student_id` in Student.

### Library and Book/Journal/Digital_Resource
- **One-to-Many**: A library can have multiple books, journals, and digital resources.
- **Foreign Key**: `library_id` in Book, Journal, and Digital_Resource refers to `library_id` in Library.

### Student_Organization and Club
- **One-to-Many**: A student organization can have multiple clubs.
- **Foreign Key**: `organization_id` in Club refers to `organization_id` in Student_Organization.

### Building and Classroom/Laboratory/Office/Common_Area
- **One-to-Many**: A building can have multiple classrooms, laboratories, offices, and common areas.
- **Foreign Key**: `building_id` in Classroom, Laboratory, Office, and Common_Area refers to `building_id` in Building.

### Faculty and Payroll
- **One-to-Many**: A faculty member can have multiple payroll records.
- **Foreign Key**: `faculty_id` in Payroll refers to `faculty_id` in Faculty.

## Access Patterns (Queries)
Here are some common queries that users would likely perform on the database, along with their SQL representations:
1. **List all students enrolled in a specific course, along with their grades.**
   ```sql
   SELECT s.student_id, s.first_name, s.last_name, e.grade
   FROM Student s
   JOIN Enrollment e ON s.student_id = e.student_id
   WHERE e.course_id = ?;```
2. **Find all projects (assignments, quizzes, exams, and research projects) related to a specific course.**
   ```sql
    SELECT 'Assignment' AS project_type, a.assignment_id AS project_id, a.title, a.due_date AS date, a.max_score
    FROM Assignment a
    WHERE a.course_id = ?
    UNION
    SELECT 'Quiz', q.quiz_id, q.title, q.date, q.max_score
    FROM Quiz q
    WHERE q.course_id = ?
    UNION
    SELECT 'Exam', e.exam_id, e.title, e.date, e.max_score
    FROM Exam e
    WHERE e.course_id = ?
    UNION
    SELECT 'Research Project', rp.research_id, rp.title, rp.start_date AS date, NULL AS max_score
    FROM Research_Project rp
    JOIN Faculty f ON rp.faculty_id = f.faculty_id
    JOIN Course c ON f.department_id = c.department_id
    WHERE c.course_id = ?;
3. **Retrieve the details of all financial transactions made by a specific student.**
    ```sql
    SELECT t.transaction_id, t.amount, t.transaction_date, t.description
    FROM Financial_Transaction t
    JOIN Student s ON t.student_id = s.student_id
    WHERE s.student_id = ?;
4. **Calculate the average GPA of students in a specific major.**
    ```sql
    SELECT AVG(e.grade) as average_gpa
    FROM Enrollment e
    JOIN Student s ON e.student_id = s.student_id
    JOIN Course c ON e.course_id = c.course_id
    JOIN Department d ON c.department_id = d.department_id
    WHERE d.name = ?;
5. **Retrieve the schedule of courses offered by a department in a given semester.**
    ```sql
    SELECT c.course_id, c.name, e.semester, e.year
    FROM Course c
    JOIN Enrollment e ON c.course_id = e.course_id
    JOIN Department d ON c.department_id = d.department_id
    WHERE d.name = ? AND e.semester = ? AND e.year = ?;
6. **Identify students who have utilized specific support services.**
    ```sql
    SELECT s.student_id, s.first_name, s.last_name
    FROM Student s
    JOIN Mental_Health_Support mhs ON s.student_id = mhs.student_id
    WHERE mhs.description LIKE ?;
7. **List all assignments for a particular course along with their due dates.**
    ```sql
    SELECT a.assignment_id, a.title, a.due_date
    FROM Assignment a
    JOIN Course c ON a.course_id = c.course_id
    WHERE c.course_id = ?;
8. **Get a list of all journals available in a specific library.**
    ```sql
    SELECT j.journal_id, j.title, j.volume, j.issue, j.publication_year
    FROM Journal j
    JOIN Library l ON j.library_id = l.library_id
    WHERE l.name = ?;
9. **List all scholarships awarded to a particular student.**
      ```sql
      SELECT sc.scholarship_id, sc.name, sc.amount
      FROM Scholarship sc
      JOIN Student s ON sc.student_id = s.student_id
      WHERE s.student_id = ?;
10. **Get the payroll details for a specific faculty member.**
      ```sql
      SELECT p.payroll_id, p.amount, p.payment_date, p.description
      FROM Payroll p
      JOIN Faculty f ON p.faculty_id = f.faculty_id
      WHERE f.faculty_id = ?;
11. **List all exams scheduled for a specific course.**
      ```sql
      SELECT e.exam_id, e.title, e.date, e.max_score
      FROM Exam e
      JOIN Course c ON e.course_id = c.course_id
      WHERE c.course_id = ?;

### Notes

- The average GPA calculation assumes that grades are stored in a format that can be averaged directly. If grades are letter-based, additional mapping to numeric values would be required.

- The database design follows normalization principles to reduce redundancy and ensure data integrity. Foreign key constraints are used to enforce relationships between tables.

- Indexes should be created on frequently queried columns, especially foreign keys and any columns used in WHERE clauses to improve query performance.

- The design assumes that optional fields like phone_number in Student and Faculty can have null values. Queries should account for possible null values where appropriate.

