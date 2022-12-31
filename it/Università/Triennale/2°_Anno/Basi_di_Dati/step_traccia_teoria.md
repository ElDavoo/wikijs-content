---
title: Come fare traccia basi
description: 
published: true
date: 2022-12-28T21:36:10.445Z
tags: public, disable-comments
editor: markdown
dateCreated: 2022-12-28T21:22:25.520Z
---

# Analisi dei requisiti

## Riscrivere il testo in input

1)  Scegliere il corretto livello di astrazione, scegliendo termini normali

2)  Standardizzare la struttura delle frasi

3)  Linearizzare le frasi, suddividendo quelle articolate.

4)  Individuare omonimi e sinonimi, unificando i termini

5)  Rendere esplicito il riferimento fra termini

6)  Riorganizzare le frasi per concetti

    1.  Frasi di carattere generale

    2.  Frasi relative a feature N

7)  Scrivere SOLO le specifiche sui dati, non quelle sulle operazioni

## Costruire glossario di termini

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Termine</th>
<th>Descrizione</th>
<th>Sinonimi</th>
<th>Collegamenti</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Partecipante</td>
<td>Un partecipante ai corsi, può essere dipendente o libero</td>
<td>Studente</td>
<td>Corso, Società</td>
</tr>
</tbody>
</table>

## Riscrivere le frasi sulle operazioni/funzioni, con frequenza delle operazioni

Il sistema deve essere in grado di gestire, tra le altre, le seguenti operazioni:

1)  visualizzare l'insieme delle fografie per un certo tipo di soggetto e la loro dislocazione fisica (50 volte al gg)

# Progettazione Concettuale

Strategia Ibrida:

1)  partendo dalle specifiche si rappresentano tutte le informazioni in uno **SCHEMA SCHELETRO** iniziale usando pochi concetti astratti.

2)  Successivamente ogni entità e/relazione dello schema è **RAFFINATA.**

    1.  Vengono incluse solo le entità, non le relazioni

    2.  Scrivere separatemente valori ammessi e vincoli

3)  i diversi schemi ottenuti sono **INTEGRATI**, giungendo allo schema E-R finale, più dettagliato di quello iniziale.

Includere le scelte che si sono effettuate, la lista degli enum e i vincoli di integrità (sotto forma di asserzione, ovvero deve/non deve).

Se è troppo complicato aggiungere gli attributi nello schema si possono non disegnare e aggiungerli in un dizionario dei dati

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Enetità</th>
<th>Descrizione</th>
<th>Attributi</th>
<th>Identificatore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Impiegato</td>
<td>Un impiegato che lavora</td>
<td>Codice, Cognome, Stipendio</td>
<td>Codice</td>
</tr>
</tbody>
</table>

# Progettazione logica

## Determinazione carico applicativo

### Tavola dei volumi

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 32%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Concetto</th>
<th>Tipo</th>
<th>Volume</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Sede</td>
<td>E</td>
<td>10</td>
</tr>
</tbody>
</table>

### Tavola delle operazioni

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 32%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Operazione</th>
<th>Tipo</th>
<th>Frequenza</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Op.1</td>
<td>I</td>
<td>50 al giorno</td>
</tr>
</tbody>
</table>

### Tavola degli accessi

Costo di una lettura = 1, costo di una scrittura = 2

Per ogni operazione spiegare il perché della stima e costruire una tavola degli accessi

Operazione 1

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 24%" />
<col style="width: 24%" />
</colgroup>
<thead>
<tr class="header">
<th>Concetto</th>
<th>Costrutto</th>
<th>Accessi</th>
<th>Tipo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Impiegato</td>
<td>Entità</td>
<td>1</td>
<td>L</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Operazione N…

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 24%" />
<col style="width: 24%" />
</colgroup>
<thead>
<tr class="header">
<th>Concetto</th>
<th>Costrutto</th>
<th>Accessi</th>
<th>Tipo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Afferenza</td>
<td>Relazione</td>
<td>1</td>
<td>L</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Analisi delle ridondanze

Forme di ridondanza da eliminare:

1)  attributi derivabili per ogni occorrenza, sia da altri attributi della stessa entità o associazione, sia da attributi di altre entità o associazioni, spesso tramite funzioni di aggregazione

2)  Associazioni derivabili dalla composizione di altre associazioni, ovvero presenza di cicli (nota: la presenza di cicli non garantisce la presenza di una ridondanza).

La decisione fra mantenere o eliminare una ridondanza va presa confrontando:

1)  Il costo di esecuzione delle operazioni, con/senza ridondanza

    1.  Per ogni operazione:

        1.  Prendi la tavola degli accessi con/senza ridondanza ed esegui la somma degli accessi

        2.  Moltiplica la somma del costo di accesso per la frequenza giornaliera (che troverai nella tavola delle operazioni)

    2.  Somma tutto

sommatoria, per ogni operazione, di: (somma tavola accessi) \*frequenza giornaliera

2)  Lo spazio occupato dal dato ridondante (non importante da fare)

## Eliminazione delle generalizzazioni 

1)  Accorpamento delle figlie nel genitore

    1.  Le entità figlie sono eliminate e le loro proprietà aggiunte al padre. Viene inoltre aggiunto un attributo per distinguere il tipo di occorrenza di padre.

    2.  Accorpamento del padre nelle figlie: Si elimina il padre, i suoi attributi vengono aggiunti alle figlie, le relazioni vengono divise in due. Si può fare solo se totale.

    3.  Sostituzione della generalizzazione con associazioni (relazioni 0,1 1,1 (parziale) 1,1,1,1 (totale)), con chiave esterna che lega figlie alla relazione. Conviene farlo se gli accessi alle entità figlie sono separatai dagli accessi del padre.

## Partizionamento/accorpamento di entità e associazioni

Partizionamento verticale di entità:

si suddivida un’entità in due entità legate da una relazione. <img src="media/image1.png" style="width:3.82298in;height:1.84287in" />

### Partizionamento orizzontale di entità

Ripartizione di Impiegato in Analista e Venditore (sulle occorrenze di un’entità e non sugli attributi).

### Eliminazione di attributi multivalore

Attributi che possono avere più istanze, tipo una agenzia che ha più numeri di telefono

### Accorpamento di entità

## Scelta degli identificatori primari

L’identificatore primario di una relazione:

1)  Non deve avere valori nulli

2)  Deve essere semplice

3)  Deve essere usato nelle operazioni più frequenti

# Traduzione verso il modello logico

Le entità diventano relazioni

Le associazioni diventano relazioni

Impiegato(<u>Matricola</u>, Cognome, Stipendio)

Progetto(C<u>odice</u>, Nome, Budget)

Partecipazione(<u>Matricola, Codice</u>, DataInizio)

Se c’è una relazione uno-a-molto, prestare attenzione alla chiave, alcuni attributi potrebbero essere non necessari

Se due relazioni hanno la stessa chiave, si possono fondere

Indicare <u>chiavi,</u> possibili valori nulli\* e vincoli di integrità referenziale con le frecce

# Normalizzazione

Una dipendenza funzionale è un attributo il cui valore dipende sempre da un altro attributo, ad esempio “tipolavoro” determina “stipendio”. Questa è una generalizzazione della definizione di vincolo di chiave.

Le anomalie si verificano in corrispondenza delle dipendenze funzionali che non derivano dalle chiavi

Si tratta di Dipendenza Funzionale “banale” (sempre soddisfatta) • Y → A è non banale se A non appartiene a Y • Y → Z è non banale se nessun attributo in Z appartiene a Y

Una relazione r è in forma normale di Boyce e Codd (BCNF) se, per ogni dipendenza funzionale (“non banale”) X◊Y “definita” su r, X è (super)chiave.

Def. Una relazione r è in terza forma normale (3NF) se, per ogni dipendenza funzionale (“non banale”) X◊Y definita su r, almeno una delle seguenti condizioni è verificata: • X contiene una chiave K di r • ogni attributo in Y è contenuto in almeno una chiave di r.

Di solito si decompone una relazione, ma si può anche introdurre un altro attributo
