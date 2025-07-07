dalla traccia estraggo:

-Dipartimenti
-Corsi di laure
-Corsi (singole materie)
-Insegnati
-Appelli d'esame
-Studenti


le relazioni sono:
 
 un dipartimento ha molti corsi di laurea
 quindi DIPARTIMENTO--->CORSI DI LAUREA 1 TO MANY

 un corso di laurea ha molte materie
 quindi CORSI DI LAUREA--->CORSI 1 to MANY

 un corso può avere piu prof, e un prof può insegnare in più corsi
 quindi CORSI---->INSEGANTI MANY TO MANY

 un corso ha molti appelli d'esame
 quindi CORSI----->ESAME 1 TO MANY

 uno studente può avere un solo corso di laurea
 quindi STUDENTE----->CORSI DI LAUREA  1 TO MANY

 uno studente puo' fare molti esami un esame puo' avere molti studenti 
 quindi STUDENTI------>ESAMI MANY TO MANY


# Dipartimenti

id
nome

# corsi_laurea

id 
nome 
dipartimento_id

# corsi

id 
nome 
corso_laurea_id

# insegnanti

id
nome
coignome

# esami

id
data
corso_id

# studenti

id
nome
cognome
matricola
corso_laurea_id