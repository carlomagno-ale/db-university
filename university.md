# Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:  
*sono presenti **diversi Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);  
ogni **Dipartimento** offre **più Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..);  
ogni **Corso di Laurea** prevede **diversi Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);  
ogni **Corso** può essere tenuto da **diversi Insegnanti**;  
ogni **Corso** prevede **più appelli d'Esame**;  
ogni **Studente** è iscritto ad un solo **Corso di Laurea**;  
ogni **Studente** può **iscriversi** a **più appelli di Esame**;  
per ogni **appello d'Esame** a cui lo Studente ha partecipato, è necessario memorizzare il **voto ottenuto**, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.*


**TABELLE:**

**dipartimenti**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- nome_dipartimento VARCHAR(40)

**corsi_laurea**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- nome_corso_laurea	VARCHAR(40)
- id_dipartimento INT FOREIGN KEY

**corsi**
- id INT PRIMARY KEY, AUTO_INCREMENT	
- nome_corso VARCHAR(50)
- id_corso_laurea INT FOREIGN KEY

**insegnanti**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- nome_insegnante VARCHAR(50)
- cognome_insegnante VARCHAR(50)
- id_corsi INT FOREIGN KEY

**appelli_esame**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- corso_appello VARCHAR(50)
- orario DATETIME
- id_corsi INT FOREIGN KEY

**studente**
- matricola_studente INT, PRIMARY KEY, AUTO_INCREMENT, UNIQUE
- nome_studente VARCHAR(50)
- cognome_studente VARCHAR(50)
- id_corsi_laurea INT FOREIGN KEY

**appelli_esame_studente**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- id_appelli_esame INT FOREIGN KEY
- matricola_studente INT FOREIGN KEY
- id_voto INT FOREIGN KEY

**voto**
- id INT, PRIMARY KEY, AUTO_INCREMENT
- voto: INT da 1 a 30
- lode: TINYINT(1) DEFAULT(0)