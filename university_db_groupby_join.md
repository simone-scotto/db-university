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
