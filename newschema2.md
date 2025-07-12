Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(enrolment_date) AS anno, COUNT(*) AS numero_iscritti
FROM students
GROUP BY anno
ORDER BY anno;

Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT office_address, COUNT(*) AS numero_docenti
FROM teachers
GROUP BY office_address
ORDER BY numero_docenti DESC;

Calcolare la media dei voti di ogni appello d'esame

SELECT exam_id, AVG(vote) AS media_voto
FROM exam_student
GROUP BY exam_id;

Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT department_id, COUNT(*) AS numero_corsi_laurea
FROM degrees
GROUP BY department_id;





Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT s.*
FROM students s
JOIN degrees d ON s.degree_id = d.id
WHERE d.name LIKE '%Economia%';

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT d.*
FROM degrees d
JOIN departments dp ON d.department_id = dp.id
WHERE dp.name = 'Dipartimento di Neuroscienze' AND d.level = 'magistrale';

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT c.*
FROM courses c
JOIN course_teacher ct ON c.id = ct.course_id
WHERE ct.teacher_id = 44;

Studenti con info sul corso di laurea e dipartimento, ordinati per cognome e nome

SELECT s.name, s.surname, d.name AS corso_di_laurea, dp.name AS dipartimento
FROM students s
JOIN degrees d ON s.degree_id = d.id
JOIN departments dp ON d.department_id = dp.id
ORDER BY s.surname, s.name;

Corsi di laurea con relativi corsi e insegnanti

SELECT deg.name AS corso_di_laurea, c.name AS corso, t.name, t.surname
FROM degrees deg
JOIN courses c ON c.degree_id = deg.id
JOIN course_teacher ct ON c.id = ct.course_id
JOIN teachers t ON ct.teacher_id = t.id;

Docenti che insegnano nel Dipartimento di Matematica

SELECT DISTINCT t.*
FROM teachers t
JOIN course_teacher ct ON t.id = ct.teacher_id
JOIN courses c ON ct.course_id = c.id
JOIN degrees d ON c.degree_id = d.id
WHERE d.department_id = 5;




BONUS: Per ogni studente il numero di tentativi per esame e voto massimo, solo voti ≥18

SELECT student_id, exam_id, COUNT(*) AS numero_tentativi, MAX(vote) AS voto_massimo
FROM exam_student
WHERE vote >= 18
GROUP BY student_id, exam_id;