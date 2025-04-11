1. Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * FROM db_university_2.students
WHERE date_of_birth >= '1990-01-01' AND date_of_birth <= '1990-12-31';

OPPURE

SELECT * FROM db_university_2.students
WHERE YEAR(date_of_birth) = '1990';

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * FROM db_university_2.courses
WHERE cfu > 10;

3. Selezionare tutti gli studenti che hanno più di 30 anni (1000)

SELECT * FROM db_university_2.students
WHERE date_of_birth < '1995-01-01';

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT * FROM db_university_2.courses
WHERE period = 'I semestre' AND courses.year = 1

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT * FROM db_university_2.exams
WHERE exams.date = '2020-06-20' AND exams.hour > '14:00:00'

6. Selezionare tutti i corsi di laurea magistrale (38)

SELECT * FROM db_university_2.degrees
WHERE degrees.level = 'magistrale';

7. Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(ID) FROM db_university_2.departments;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(*) FROM db_university_2.teachers
WHERE phone IS NULL
