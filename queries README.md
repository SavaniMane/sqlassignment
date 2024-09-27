--QUESTION 1 -- INIT database -- Create the Students table CREATE TABLE Students ( student_id INT PRIMARY KEY, name VARCHAR(50), age INT, grade_level INT );

-- Create the Courses table CREATE TABLE Courses ( course_id INT PRIMARY KEY, course_name VARCHAR(50), credits INT );

-- Create the Enrollments table CREATE TABLE Enrollments ( enrollment_id INT PRIMARY KEY, student_id INT, course_id INT, grade DECIMAL(3, 2), FOREIGN KEY (student_id) REFERENCES Students(student_id), FOREIGN KEY (course_id) REFERENCES Courses(course_id) );

-- Insert sample data into Students INSERT INTO Students (student_id, name, age, grade_level) VALUES (1, 'Alice', 20, 3), (2, 'Bob', 21, 4), (3, 'Charlie', 19, 3), (4, 'Diana', 22, 4), (5, 'Ethan', 20, 3);

-- Insert sample data into Courses INSERT INTO Courses (course_id, course_name, credits) VALUES (1, 'Math', 3), (2, 'Science', 4), (3, 'History', 3), (4, 'Art', 2);

-- Insert sample data into Enrollments INSERT INTO Enrollments (enrollment_id, student_id, course_id, grade) VALUES (1, 1, 1, 3.5), (2, 1, 2, 4.0), (3, 2, 1, 2.5), (4, 2, 3, 3.0), (5, 3, 2, 3.0), (6, 3, 4, 2.0), (7, 4, 1, 3.5), (8, 4, 3, 4.0), (9, 5, 2, 3.0), (10, 5, 4, 3.5); SELECT AVG(grade) AS average_grade FROM Enrollments;

![image](https://github.com/user-attachments/assets/e11789bb-a546-49a0-b4b4-0c011b1cf584)

--QUESTION 2

SELECT Students.name, Courses.course_name FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id INNER JOIN Courses ON Enrollments.course_id = Courses.course_id; 1

![image](https://github.com/user-attachments/assets/f1bfdeb9-fff3-4cf5-9df8-12d2e7c758fa) 

--QUESTION 3

SELECT grade_level, COUNT(*) AS student_count FROM Students GROUP BY grade_level;

![image](https://github.com/user-attachments/assets/014c5fbe-1435-48dc-af4f-1c71751be1c0) 

--QUESTION 4

SELECT Courses.course_name, MAX(Enrollments.grade) AS max_grade FROM Courses INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id GROUP BY Courses.course_name;

![image](https://github.com/user-attachments/assets/5063168f-5b8d-4bea-8132-571fc749c53d) 

--QUESTION 5

SELECT AVG(grade) AS average_grade FROM Enrollments INNER JOIN Students ON Enrollments.student_id = Students.student_id WHERE Students.grade_level = 3;

![image](https://github.com/user-attachments/assets/6929aee6-8a76-40f3-b83f-fc8a738ef389)

--QUESTION 6

SELECT Students.name, Courses.course_name, Courses.credits FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id INNER JOIN Courses ON Enrollments.course_id = Courses.course_id;

![image](https://github.com/user-attachments/assets/0ac3f385-3a9b-4e27-b3f6-c1cf76d6f2a0)

--QUESTION 7

SELECT Courses.course_name FROM Courses INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id GROUP BY Courses.course_id HAVING AVG(Enrollments.grade) > 3.0;

![image](https://github.com/user-attachments/assets/52f4c330-8f7e-4ae2-bb9e-c8d53ee807d6)

--QUESTION 8

SELECT Students.student_id, Students.name FROM Students LEFT JOIN Enrollments ON Students.student_id = Enrollments.student_id WHERE Enrollments.grade IS NULL OR Enrollments.grade <> 4.0 GROUP BY Students.student_id, Students.name HAVING MAX(Enrollments.grade) IS NULL OR MAX(Enrollments.grade) <> 4.0;

![image](https://github.com/user-attachments/assets/a8976870-8b45-4225-a0cd-65ebde7fa68c)

--QUESTION 9

SELECT Students.name FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id GROUP BY Students.student_id HAVING AVG(Enrollments.grade) > (SELECT AVG(grade) FROM Enrollments);

![image](https://github.com/user-attachments/assets/cfb1d387-7034-4852-848a-c04e0337db68)

--QUESTION 1O

SELECT Students.name, COUNT(Enrollments.course_id) AS total_courses, AVG(Enrollments.grade) AS average_grade FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id GROUP BY Students.student_id;

![image](https://github.com/user-attachments/assets/f96b8b03-2f46-414e-ab41-8954807d13ab)







