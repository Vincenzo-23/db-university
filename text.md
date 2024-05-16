## JOIN QUERY

### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name` FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


### 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';


### 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`name` AS `course_name`, CONCAT(`teachers`.`name`, ' ', `teachers`.`surname`) AS `teacher_full_name` FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`id` = 44;


### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome



### 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti



### 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)



### 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18




## GROUP BY QUERY

### 1. Contare quanti iscritti ci sono stati ogni anno



### 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio



### 3. Calcolare la media dei voti di ogni appello d'esame



### 4. Contare quanti corsi di laurea ci sono per ogni dipartimento