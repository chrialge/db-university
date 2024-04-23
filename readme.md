## DB


Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.


## Dipartimenti

    - id BIGINT | UNIQUE | AI | PK | INDEX | 
    - nome VARCHAR(25) | NOTNULL

## Corsi di Laurea
    - id BIGINT | UNIQUE | AI | PK | INDEX
    - nome VARCHAR(40) | NOTNULL
    - id_dipartimento FK | BIGINT | 

## Corsi
    - id BIGINT | UNIQUE | AI | PK | INDEX
    - nome_corso VARCHAR(40) | NOTNULL
    - id_corso_laurea FK | BIGINT 
    - indirizzo_fisico VARCHAR(100) | NULL


## Insegnanti
    - id BIGINT | UNIQUE | AI | PK | INDEX
    - nome VARCHAR(25) | NOTNULL
    - cognome VARCHAR(25) | NOTNULL
    - cf CHAR(16) | NULL
    - id_corso FK | BIGINT | 


## Appelli

    - id BIGINT | UNIQUE | AI | PK | INDEX
    - id_corso FK | BIGINT 
    - materia VARCHAR(25) | NOTNULL
    - data DATATIME | NOTNULL

## Studenti

    - id BIGINT | UNIQUE | AI | PK | INDEX
    - Nome VARCHAR(25) | NOTNULL
    - Cognome VARCHAR(25) | NOTNULL
    - id_corso_laurea FK | BIGINT 
    - foto VARCHAR(255) | NULL

## Iscrizione Esami

    - id BIGINT | UNIQUE | AI | PK | INDEX
    - id_appello FK | BIGINT 
    - id_studente FK | BIGINT 
    - voto TINYINT | NOTNULL




