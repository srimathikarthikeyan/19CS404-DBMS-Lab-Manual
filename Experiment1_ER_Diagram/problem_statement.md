# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Srimathi K

## Scenario Chosen:
University

## ER Diagram:
![University ER Diagram](https://github.com/user-attachments/assets/67fd65ba-2697-4a07-94a4-ecfdb52a3388)


## Entities and Attributes:
### Entities:
   1. Department
         - Dept_ID(Primary Key)
         - Dept_Name
   2. Program
         - Program_ID(Primary Key)
         - Program_Name
         - Dept_ID(Foreign Key)
   3. Student
         - Admission_No(Primary Key)
         - Name
         - DOB
         - Contact_Info
         - Program_ID(Foreign Key)
   4. Instructor
         - Staff_No(Primary Key)
         - Name
         - Contact_Info
         - Dept_ID(Foreign Key)
   5. Course
         - Course_No(Primary Key)
         - Course_Name
         - Credits
         - Program_ID(Foreign Key)
   6. Enrollment
         - Enrollment_ID(Primary Key)
         - Admission_No(Foreign Key)
         - Course_No(Foreign Key)
         - Prerequisite_Course_No(Foreign Key)

## Relationships and Constraints:
1. Department - offers - Program (1:N, Total on Program)
2. Department - employs - Instructor (1:N, Partial on Instructor)
3. Program - has - Student (1:N, Total on Student)
4. Program - offers - Course (1:N, Total on Course)
5. Student – enrolls – Course (via Enrollment) (M:N, Total on Student, Partial on Course)
6. Course – requires – Course (Prerequisite relationship) (M:N, Partial on both sides)
   
## Extension (Prerequisite):
- For the prerequisite in the University system, I modeled it by creating a relationship between courses where one course can have another course as a prerequisite. For example, you can't enroll in Data Structures course without first completing an Introduction to Programming course. This ensures that students follow the proper sequence of courses and gain the necessary knowledge before moving on to more advanced topics.
- This relationship helps keep track of which courses are dependent on others, and it ensures students aren't missing key information needed for more complex subjects.

## Design Choices:
### Entities:
   - **Department:** I included the Department entity because it serves as the core unit that organizes academic programs and manage instructors effectively.
   - **Program:** The Program entity is essential for defining the different academic programs students can pursue. It ties back to the department and holds the courses specific to each program.
   - **Student:** Students are the focus of the system as they are the primary entities that interact with programs and courses. I included Admission_No as the primary key to uniquely identify each student.
   - **Instructor:** I included Instructor as an entity because instructors are responsible for teaching courses and are associated with specific departments. Their Staff_No uniquely identifies them.
   - **Course:** Course entities represent the academic subjects offered by programs. Each course has its own set of attributes (name, credits) and is tied to a specific program.
   - **Enrollment:** The Enrollment entity tracks which students are enrolled in which courses. It acts as a bridge between Student and Course in a many-to-many relationship.

### Relationships:
   - **Department -> offers -> Program:** I modeled this relationship as 1:N because each department can offer multiple programs, but a program can only belong to one department.
   - **Department -> employs -> Instructor:** This is also a 1:N relationship. A department can employ multiple instructors, but an instructor can only be associated with one department. I made this relationship partial on the instructor side to reflect that not every instructor must be associated with a department, like part-time instructors or external guest lecturers.
   - **Program -> has -> Student:** This is a 1:N relationship because a program can have many students, but each student belongs to exactly one program. It’s total on the student side because every student must belong to a program.
   - **Program -> offers -> Course:** This relationship is 1:N, where each program offers many courses, but a course belongs to only one program. It’s total on the course side to ensure every course is tied to a program.
   - **Student –> enrolls –> Course (via Enrollment):** This is a M:N relationship, tracked by the Enrollment entity. A student can enroll in many courses, and a course can have many students. It’s total on the student side because every student must enroll in at least one course, and partial on the course side to reflect that some courses might not have students enrolled.
   - **Course –> requires –> Course (Prerequisite relationship):** I included this M:N relationship to handle prerequisites for courses. Some courses require students to complete other courses before enrolling. This relationship is partial on both sides to accommodate the fact that not all courses have prerequisites, and not all courses are prerequisites for others.

### Assumptions:
   - A student can only belong to one program at a time.
   - A course belongs to only one program, and programs can have many courses.
   - Instructors are linked to only one department, but a department can have multiple instructors.
   - Every student must be enrolled in at least one course (via the Enrollment entity).
   - Not every course has prerequisites, but if it does, it's tracked in the Prerequisite_Course_No attribute of the Enrollment entity.

## RESULT
The Enitty_Relationship (ER) diagram for the University database was successfully designed by identifying entities, attributes, and relationships along with cardinality and participation constraints. The prerequisite relationship between courses was modeled effectively to ensure proper course sequencing. Thus, the objective of understanging and applying ER modeling concepts was achieved.
