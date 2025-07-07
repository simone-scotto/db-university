Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
-- sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
-- ogni `Dipartimento` offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
-- ogni `Corso di Laurea` prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
-- ogni `Corso` può essere tenuto da diversi `Insegnanti`;
-- ogni `Corso` prevede più appelli d'`Esame`;
-- ogni `Studente` è iscritto ad un solo `Corso di Laurea`;
-- ogni `Studente` può iscriversi a più appelli di `Esame`;
-- per ogni appello d'`Esame` a cui lo `Studente` ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

Utilizzare https://www.drawio.com/ per la creazione dello schema.
Esportare quindi il diagramma in pnge caricarlo nella repo come visto in classe
convermate lettura come al solito e buon divertimento

## entità

- dipartimento
- corso di laurea
- corso
- insegnante
- esame
- studente

## tabelle

- dipartimenti
- corsi di laurea
- corsi
- insegnanti
- esami
- studenti

## dipartimenti (primary)

- id
- nome
- idrizzo

## corsi-di-laurea

- id
- dipartimento_id
- nome
- durata

## studenti

- id
- corsi_di_laurea_id
- matricola
- nome
- cognome
-

## corsi

- id
- corsi_di_laurea_id
- nome
- durata
- crediti

## insegnanti

- corsi_id
- nome
- cognome
- numero
- mail

## appelli-esami

- id
- corsi_id
- data
- luogo

## esami_studenti

- id
- esami_id
- studenti_id
- voto
