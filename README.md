# Student Registration Management System

## Overview
The **Student Registration Management System** is designed to manage student enrollments, courses, instructors, and payments efficiently. It allows students to register for courses, instructors to manage class schedules, and administrators to oversee the entire process.

## Features
- **Student Registration:** Register students with personal details.
- **Course Management:** Manage available courses and their details.
- **Instructor Management:** Assign instructors to courses.
- **Enrollment System:** Track student enrollments in different courses.
- **Class Scheduling:** Schedule classes with instructors and timings.
- **Payment Processing:** Handle student payments for courses.

## Database Schema

### 1. **Students**
- `student_id` (Primary Key, INT, AUTO_INCREMENT)
- `first_name` (VARCHAR)
- `last_name` (VARCHAR)
- `date_of_birth` (DATE)
- `email` (VARCHAR, UNIQUE)
- `phone` (VARCHAR)
- `address` (TEXT)
- `gender` (ENUM: Male, Female, Other)
- `registration_date` (TIMESTAMP)
- `status` (ENUM: Active, Inactive)

### 2. **Courses**
- `course_id` (Primary Key, INT, AUTO_INCREMENT)
- `course_name` (VARCHAR)
- `course_code` (VARCHAR, UNIQUE)
- `description` (TEXT)
- `credit_hours` (INT)
- `department_id` (Foreign Key)

### 3. **Departments**
- `department_id` (Primary Key, INT, AUTO_INCREMENT)
- `department_name` (VARCHAR, UNIQUE)
- `head_of_department` (VARCHAR)

### 4. **Instructors**
- `instructor_id` (Primary Key, INT, AUTO_INCREMENT)
- `first_name` (VARCHAR)
- `last_name` (VARCHAR)
- `email` (VARCHAR, UNIQUE)
- `phone` (VARCHAR)
- `specialization` (VARCHAR)
- `department_id` (Foreign Key)

### 5. **Enrollments** (Mapping Table for Students and Courses)
- `enrollment_id` (Primary Key, INT, AUTO_INCREMENT)
- `student_id` (Foreign Key)
- `course_id` (Foreign Key)
- `enrollment_date` (TIMESTAMP)
- `grade` (VARCHAR)

### 6. **Class Schedules**
- `schedule_id` (Primary Key, INT, AUTO_INCREMENT)
- `course_id` (Foreign Key)
- `instructor_id` (Foreign Key)
- `day_of_week` (ENUM: Monday-Sunday)
- `start_time` (TIME)
- `end_time` (TIME)
- `room_number` (VARCHAR)

### 7. **Payments**
- `payment_id` (Primary Key, INT, AUTO_INCREMENT)
- `student_id` (Foreign Key)
- `amount` (DECIMAL)
- `payment_date` (TIMESTAMP)
- `payment_status` (ENUM: Paid, Pending, Overdue)

## Relationships
- A **student** can enroll in multiple **courses**.
- A **course** belongs to one **department**.
- An **instructor** teaches multiple **courses**.
- A **student** makes multiple **payments**.
- A **course** has a **schedule** with an **instructor** assigned.

## Setup Instructions
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/student-registration-system.git
   ```
2. Navigate to the project folder:
   ```sh
   cd student-registration-system
   ```
3. Set up the database:
   - Import the provided SQL script into MySQL or PostgreSQL.
4. Configure the environment variables for database connection.
5. Run the application:
   ```sh
   npm start  # If using Node.js
   python app.py  # If using Python
   ```

## Contributing
Feel free to submit pull requests and contribute to the project.
