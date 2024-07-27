<!-- TRACCIA
Modellare la struttura di un database per memorizzare tutti i dati riguardanti una università:

sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);

- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
  
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);

- ogni Corso può essere tenuto da diversi Insegnanti;

- ogni Corso prevede più appelli d'Esame;

- ogni Studente è iscritto ad un solo Corso di Laurea;

- ogni Studente può iscriversi a più appelli di Esame;

- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
-->


# DB University

# table: departments

- id 
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- name
  - VARCHAR(80)
  - NOTNULL

# table: degree_courses

- id 
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- name
  - VARCHAR(80)
  - NOTNULL

- areas
  - VARCHAR(50)
  - NULL

- departments_id
  - UNSIGNED 
  - BIGINT 
  - FK

- admission
  - VARCHAR(40)
  - NULL

- erasmus
  - VARCHAR(80)
  - NOTNULL

# table: admission

- id 
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- degree_courses_id
  - UNSIGNED 
  - BIGINT 
  - FK

- course_name
  - VARCHAR(80)
  - NOTNULL

- price
  - DECIMAL(7,2)
  - NOTNULL

- scholarships
  - VARCHAR(100)
  - NULL

# table: courses

- id
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- degree_courses_id
  - UNSIGNED 
  - BIGINT 
  - FK

- name
  - VARCHAR(80)
  - NOTNULL

- duration
  - VARCHAR(40)
  - NULL

- learning_goals
  - VARCHAR(100)
  - NULL

- description
  - VARCHAR(300)
  - NULL

- career_opportunities
  - VARCHAR(100)
  - NULL

- exam_appeals_id
  - UNSIGNED 
  - BIGINT 
  - FK

# table: teachers

- id
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- name
  - VARCHAR(80)
  - NOTNULL

- degree_courses_id 
  - UNSIGNED 
  - BIGINT 
  - FK

- contacts 
  - VARCHAR(80)
  - NOTNULL

# table: teachers_personal_data

- id
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- teachers_id
  - UNSIGNED 
  - BIGINT 
  - FK

- name
  - VARCHAR(80)
  - NOTNULL

- last_name
  - VARCHAR(80)
  - NOTNULL

- identity_card_num
  - VARCHAR(8)
  - NULL

- adress
  - VARCHAR(80)
  - NULL 

- salary
  - DECIMAL (7,2)
  - NULL


# table: exam_appeals

- id
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- course_name 
  - VARCHAR(80)
  - NOTNULL

- date
  - DATE
  - NOTNULL

- teachers_id
  - UNSIGNED 
  - BIGINT 
  - FK

- available_credits
  - TINYINT
  - NULL

- votes_id
  - TINYINT
  - NULL

# table: votes (courses R(DBMS) - students R(DBMS))

- id
  - BIGINT
  - PK
  - AI
  - UNIQUE
  - NOTNULL

- value

# table: students (degree_courses R(DBMS) - courses R(DBMS) - teachers R(DBMS) - exam_appeals R(DBMS) - votes R(DBMS))