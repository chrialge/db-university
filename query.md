## instruction

Dopo aver creato un nuovo database nel vostro phpMyAdmin e aver importato lo schema allegato, eseguite le query del file allegato.
Cosa consegnare?
Dopo aver testato le vostre query con phpMyAdmin, riportatele in un file query.md e caricatelo nella vostra repo.

1. Selezionare tutti gli studenti nati nel 1990 (160)
2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
3. Selezionare tutti gli studenti che hanno più di 30 anni
4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
6. Selezionare tutti i corsi di laurea magistrale (38)
7. Da quanti dipartimenti è composta l'università? (12)
8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

## task1

<!--  seleziono tutte le colonne della atbella students e cerco nella colonna date_of_birth chi e nato nel 1990 -->

SELECT \* FROM `students` WHERE date_of_birth LIKE '1990%';

## task2

<!-- seleziono tute le colonne della tabella e cerco nella colonna cfu chi e sopra i 10 -->

SELECT \* FROM `courses` WHERE cfu > 10;

## task 3

SELECT \* FROM `students` WHERE date_of_birth BETWEEN '1994-04-24' AND '2024-04-24';

## task 4
