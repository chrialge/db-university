## instruction

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

-   sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
-   ogni `Dipartimento` offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
-   ogni `Corso di Laurea` prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
-   ogni `Corso` può essere tenuto da diversi `Insegnanti`;
-   ogni `Corso` prevede più appelli d'`Esame`;
-   ogni `Studente` è iscritto ad un solo `Corso di Laurea`;
-   ogni `Studente` può iscriversi a più appelli di `Esame`;
-   per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.

-   departement
-   course
-   student
-   exams
-   professor

Table name: departement

-   ID | INDEX| PK | AI, BIGINIT, NOTNULL, UNIQUE,
-   name |VARCHAR(25)

Table name: courses laurea:

-   ID | INDEX| PK | AI, BIGINIT, NOTNULL, UNIQUE,
-   departement_id
-   name VARCHRA(40)

Table name: courses

-   ID | INDEX | PK| AI, BIGINIT, NOTNULL, UNIQUE,
-   corso_laurea_id |FK|
-   nome_course VARCHAR(40)
-   address VARCHAR(100)

Table name: students

-   ID | INDEX | AI, BIGINIT, NOTNULL, UNIQUE,
-   name | VARCHAR(30)
-   lastname | VARCHAR
-   corso_laurea_id | FK

Table name: exams

-   ID | INDEX | AI, BIGINIT, NOTNULL, UNIQUE,
-   course_id |FK|
-   name_materia | VARCHAR(30),
-   data | DATETIME
-   vote | TINYINT

Table name: professore

-   ID | INDEX | AI, BIGINIT, NOTNULL, UNIQUE,
-   course_id | FK
-   name | VARCHAR(30)
-   lastname | VARCHAR(30)
