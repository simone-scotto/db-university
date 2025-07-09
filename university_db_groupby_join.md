/_GROUP BY_/

/_1. Contare quanti iscritti ci sono stati ogni anno_/

SELECT COUNT(`id`), YEAR(`enrolment_date`)
FROM `students`
GROUP BY YEAR(`enrolment_date`);

/_2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio_/

SELECT COUNT(`id`) AS `office_teachers`, `office_address`
FROM `teachers`
GROUP BY `office_address`
HAVING COUNT(`id`) > 1;

/_3. Calcolare la media dei voti di ogni appello d'esame_/

SELECT DISTINCT `exam_student`.`exam_id` AS `exam_numb`,
AVG(`exam_student`.`vote`) AS `vote_avg`,
`exams`.`date`, `exams`.`location`,
`exams`.`address`
FROM `exam_student`
JOIN `exams` ON `exam_id` = `exams`.`id`
GROUP BY `exam_student`.`exam_id`;
/_ JOIN solo per indicare data e altre informazioni_/

/_4. Contare quanti corsi di laurea ci sono per ogni dipartimento_/

SELECT COUNT(`degrees`.`id`) AS `degrees_numb`, `departments`.`name`
FROM `degrees`
JOIN `departments` ON `department_id` = `departments`.`id`
GROUP BY `degrees`.`department_id`

/_ JOIN solo per indicare il nome del dipatimento_/

/_JOIN_/
/_1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia_/

SELECT `students`.`id` AS `student_id`,
`students`.`name` AS `student_name`,
`students`.`surname` AS `student_surname`
FROM `students`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

/_2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze_/

SELECT `degrees`.`name` AS `degree_name`,
`degrees`.`level` AS `degree_level`,
`degrees`.`address` AS `degree_address`,
`degrees`.`email` AS `degree_email`,
`degrees`.`website` AS `degree_website`,
`departments`.`name`
FROM `degrees`
JOIN `departments` ON `department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'magistrale';

/_3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)_/

SELECT `courses`.`name` AS `course_name`,
`teachers`.`name` AS `teacher_name`,
`teachers`.`surname` AS `teacher_surname`
FROM `courses`
JOIN `course_teacher` ON `course_id` = `courses`.`id`
JOIN `teachers` ON `teacher_id` = `teachers`.`id`
WHERE `course_teacher`.`teacher_id` = 44;

/_4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento,
in ordine alfabetico per cognome e nome_/

SELECT `students`.`name` AS `student_name`,
`students`.`surname` AS `student_surname`,
`students`.`registration_number` AS `student_reg_numb`,
`students`.`enrolment_date` AS `student_enrol_date`,
`degrees`.`name` AS `degree_name`,
`degrees`.`level` AS `degree_level`,
`degrees`.`address` AS `degree_address`,
`degrees`.`email` AS `degree_email`,
`degrees`.`website` AS `degree_website`,
`departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
JOIN `departments` ON `department_id` = `departments`.`id`
ORDER BY `student_surname` ASC;

/_5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti_/
/_6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)_/
/_7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18_/
