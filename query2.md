### Instruction

Utilizzando lo stesso database della volta scorsa, eseguite le query in allegato.
Caricate un secondo file nella stessa repo di ieri db-university con le query di oggi.

## Group by

1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

# Task 1

<!-- Contare quanti iscritti ci sono stati ogni anno -->

```SQL
SELECT COUNT(id), YEAR(`enrolment_date`) AS `enrolment_year`
FROM `students`
GROUP BY `enrolment_year`
ORDER BY `enrolment_year` DESC;
```

# Task 2

<!-- Contare gli insegnanti che hanno l'ufficio nello stesso edificio -->

```SQL
SELECT COUNT(`id`), `office_number`
FROM `teachers`
GROUP BY `office_number`;
```

# Task 3

<!-- Calcolare la media dei voti di ogni appello d'esame -->

```SQL
SELECT ROUND(AVG(`vote`), 2), `exam_id`
FROM `exam_student`
GROUP BY `exam_id`
ORDER BY `exam_id` ASC;

```

# Task 4

<!-- Contare quanti corsi di laurea ci sono per ogni dipartimento -->

```SQL

SELECT COUNT(`department_id`), `department_id`
FROM `degrees`
GROUP BY `department_id`;

```

## Joins

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
   BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18

# Task 1

<!-- Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia -->

```SQL

SELECT `students`.`*`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

```

# Task 2

<!-- Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze -->

```SQL
SELECT `degrees`.`name`, `degrees`.`level` , `departments`.`*`
FROM `degrees`
JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'magistrale';
```

# Task 3

<!-- Selezionare tutti i corsi in cui insegna Fulvio Amato  -->

```SQL
SELECT *
FROM `course_teacher`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `course_teacher`.`teacher_id` = 44;
```

# Task 4

<!-- Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome -->

```SQL
SELECT `students`.`surname`, `students`.`name` , `degrees`.`name`, `departments`.`name`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname`, `students`.`name`;
```

# Task 5

<!-- Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti -->

```SQL

SELECT `degrees`.`name` AS `Degrees`, `departments`.`name` AS `Departement`, `courses`.`name` AS `Courses`
FROM `degrees`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`;

```

# Task 6

<!-- Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) -->

```SQL
SELECT DISTINCT `teachers`.`surname`, `teachers`.`name`, `departments`.`name`
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
WHERE `degrees`.`department_id` = 5
ORDER by `teachers`.`surname`, `teachers`.`name`;
```

# Bonus

<!-- BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18 -->

```SQL
SELECT `students`.`surname`, `students`.`name`, `courses`.`name`, COUNT(`exams`.`course_id`) AS `appelli`, MAX(`exam_student`.`vote`)
FROM `students`
JOIN `exam_student` ON `students`.`id` = `exam_student`.`student_id`
JOIN `exams` ON `exams`.`id` = `exam_student`.`exam_id`
JOIN `courses` ON `courses`.`id` = `exams`.`course_id`
WHERE  `exam_student`.`vote`>= 18
GROUP BY `students`.`surname`, `students`.`name`, `courses`.`name`
ORDER BY `students`.`surname`, `students`.`name`;
```
