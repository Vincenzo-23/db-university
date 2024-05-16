## JOIN QUERY

### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name` FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


### 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';


### 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`name` AS `course_name`, CONCAT(`teachers`.`name`, ' ', `teachers`.`surname`) AS `teacher_full_name` FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`id` = 44;


### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT CONCAT(`students`.`surname`, ' ', `students`.`name`) AS `student_full_name`, `degrees`.*, `departments`.* FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` ORDER BY `student_full_name`ASC;



### 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, CONCAT(`teachers`.`name`, ' ', `teachers`.`surname`) AS `teacher_full_name` FROM `degrees` INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;


### 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT CONCAT(`teachers`.`name`, ' ', `teachers`.`surname`) AS `teacher_full_name`, `departments`.`name` AS `department_name` FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `degrees` ON `courses`.`degree_id`= `degrees`.`id` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica' ORDER BY `teacher_full_name` ASC;


### 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18




## GROUP BY QUERY

### 1. Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS `numero_iscritto`, YEAR(`enrolment_date`) AS `anno_iscrizione` FROM `students` GROUP BY YEAR(`enrolment_date`);


### 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS `numero_insegnanti`, `office_address` FROM `teachers` GROUP BY `office_address`;



### 3. Calcolare la media dei voti di ogni appello d'esame
SELECT `exams`.`id` AS `exam_id`, `exams`.`date` AS `exam_date`, AVG (`exam_student`.`vote`) AS `average_vote` FROM `exams` INNER JOIN `exam_student` ON `exams`.`id` = `exam_student`.`exam_id` GROUP BY `exams`.`id`;


### 4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(*) AS `number_of_degrees`, `departments`.`name` AS `department_name` FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` GROUP BY `department_id`;