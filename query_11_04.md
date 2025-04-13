# JOIN
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT *
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT *
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE degrees.level = 'magistrale'
AND departments.name = 'Dipartimento di Neuroscienze'

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT *
FROM courses
JOIN course_teacher ON course_id = course_teacher.course_id
WHERE course_teacher.teacher_id = 44

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT students.name, students.surname, degrees.name AS degree_name, departments.name AS department_name
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname ASC, students.name ASC;


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT degrees.name AS degree_name, courses.name AS courses_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM degrees
JOIN courses ON degrees.id = courses.degree_id
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT teachers.name AS teacher_name, teachers.surname AS teacher_surname, departments.name AS departement_name
FROM teachers
JOIN course_teacher ON teachers.id = course_teacher.teacher_id
JOIN courses ON course_teacher.course_id = courses.id
JOIN degrees ON courses.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name= 'Dipartimento di Matematica';

# GROUP BY
1. Contare quanti iscritti ci sono stati ogni anno

SELECT
    YEAR(students.enrolment_date) AS 'Year',
    COUNT(*) AS 'Students'
FROM students
GROUP BY YEAR(students.enrolment_date)
ORDER BY year;

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT office_address,
COUNT(*) AS Teachers
FROM teachers
GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame

SELECT exams.date, AVG(exam_student.vote) AS average_vote
FROM exam_student
JOIN exams ON exam_student.exam_id = exams.id
GROUP BY exams.date

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT departments.name AS department_name, COUNT(degrees.id) AS degrees_number
FROM departments
JOIN degrees ON departments.id = degrees.department_id
GROUP BY departments.name

# RIPASSINO SELECT:

1. Selezionare tutti gli insegnanti

SELECT *
FROM teachers

OPPURE

SELECT teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM teachers

2. Selezionare tutti i referenti per ogni dipartimento

SELECT departments.name AS departments, departments.head_of_department AS head_of_department
FROM departments

3. Selezionare tutti gli studenti il cui nome inizia per "E" (373)

SELECT *
FROM students
WHERE students.name LIKE 'E%'

4. Selezionare tutti gli studenti che si sono iscritti nel 2021 (734)

SELECT *
FROM students
WHERE YEAR(enrolment_date) = '2021'

5. Selezionare tutti i corsi che non hanno un sito web (676)

SELECT *
FROM courses
WHERE courses.website IS NULL


6. Selezionare tutti gli insegnanti che hanno un numero di telefono (50)

SELECT *
FROM teachers
WHERE teachers.phone IS NOT NULL

7. Selezionare tutti gli appelli d'esame dei mesi di giugno e luglio 2020 (2634)

SELECT *
FROM exams
WHERE YEAR(exams.date) = '2020' AND MONTH(exams.date) = 6 OR MONTH(exams.date) = 7


8. Qual è il numero totale degli studenti iscritti? (5000)

SELECT COUNT(*)
FROM students

