SELECT \*
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;

SELECT \*
FROM `courses`
WHERE `cfu` > 10;

SELECT \*
FROM `students`
WHERE YEAR(CURDATE()) - YEAR (date_of_birth) > 30;

SELECT \*
FROM `courses`
WHERE `period` = 'I semestre'
AND `year` = 1;

SELECT \*
FROM `exams`
WHERE TIME(`hour`) >= '14:00:00'
AND DATE(`date`) = '2020-06-20';

SELECT \*
FROM `degrees`
WHERE `level` = 'magistrale';

SELECT COUNT(`id`)
FROM `departments`;

SELECT \*
FROM `teachers`
WHERE `phone` IS NULL;
