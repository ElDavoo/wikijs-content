---
title: Domande teoria basi
description: 
published: true
date: 2022-12-28T21:58:35.258Z
tags: public, disable-comments
editor: markdown
dateCreated: 2022-12-28T21:22:12.087Z
---

# 2 - Introduzione

## Si definiscano brevemente le nozioni di (sistema organizzativo), sistema informativo e sistema informatico esplicitando le relazioni che intercorrono tra di essi.

Il sistema organizzativo è un insieme di risorse e regole che consentono il funzionamento di una qualunque struttura sociale per il raggiungimento dei suoi obiettivi. Ad esempio, una biblioteca.

Il sistema informativo <u>organizza</u> e <u>gestisce</u> le informazioni necessarie per assicurare il funzionamento del sistema organizzativo. Può essere parzialmente o totalmente manuale, ad esempio un registro cartaceo dei libri.

Il sistema informatico è la parte automatizzata del sistema informativo, composta da archivi elettronici di dati e, sistemi di calcolo per la gestione dei dati e terminali per l’uso dei sistemi di calcolo.

## ACID

### Elencare le proprietà fondamentali di una transazione e descrivere brevemente ognuna di esse.

Una transazione è una sequenza di azioni di lettura e scrittura sulla base di dati e di elaborazioni di dati in memoria temporanea. Il DBMS deve garantire il rispetto delle proprietà ACID nelle transizioni.

### Descrivere brevemente cosa sono le ACID properties, a cosa servono e da dove deriva l’espressione “ACID”.

ACID, acronimo di Atomicity, Consistency preservation, Isolation, Durability, sono quattro proprietà che un buon DBMS deve rispettare.

L’Atomicity assicura che non si possano lasciare transazioni a metà, completandole o annullandole.

La Consistency preservation serve ad assicurarsi che il DB rimanga sempre consistente, ovvero il rispetto continuo dei vincoli di integrità.

Isolation: Le transazioni devono essere “invisibili” fra loro, i loro risultati (e il loro esito di successo/fallimento) non devono alterare l’esito delle altre transazioni da eseguire.

Durability: Una transazione pienamente eseguita deve essere permanente, ovvero non possono essere alterate da eventuali malfunzionamenti successivi al completamento della transazione.

## Data una base di dati si dica quale sia la sua parte invariante e la sua parte variabile e perché.

Lo schema, ovvero l’insieme di definizioni che descrivono struttura, restrizioni e relazioni sui dati, tendono a non variare nel tempo, in quanto generalmente variano solo si decide, dopo la progettazione e la messa in funzione, di ampliare o ristrutturare la base di dati. I dati stessi invece (le istanze), variano ad ogni inserimento, modifica o cancellazione da parte dell’utente e sono quindi la parte variabile.

## Descrivere brevemente cosa sia un modello dei dati ed elencare i modelli dei dati conosciuti.

Un modello di dati è un insieme di costrutti utilizzati per organizzare dati e descriverne la struttura in maniera programmatica, ovvero comprensibile da un calcolatore.

Il modello gerarchico, degli anni 60, si basava su strutture ad albero.

Il modello reticolare, degli anni 70, si basava su strutture reticolari.

Il modello relazionale, degli anni 80, si basa sull’uso di relazioni, ovvero insiemi di record a struttura fissa con campi di tipo primitivo.

Il modello a oggetti, degli anni 90, si fonda sull’uso di classi e relative istanze (oggetti)

Il modello XML, degli anni 2000, rivisita il modello gerarchico, presentando insieme descrizione dei dati e dati che non sono limitati ad un’unica struttura logica

Infine, i modelli semi-strutturati e flessibili organizzano dati in maniera flessibile, per aumentare le performance.

## Si descriva brevemente cosa siano indipendenza logica e fisica dai dati e quale/i modello di basi di dati consente/ono di realizzarle. --- Descrivere brevemente cosa siano indipendenza logica e fisica dai dati del modello relazione, esplicitando quale caratteristica fondamentale del modello relazionale le consentano

L’indipendenza fisica dei dati rende possibile modificare la rappresentazione fisica dei dati (ad esempio, la struttura del file nel file system), senza dover modificare lo schema dei dati (e quindi i programmi che ci operano sopra).

L’indipendenza logica consente di avere uno schema logico “di base” su cui costruire livelli e schema esterni. I programmi si interfacceranno con gli schemi esterni e sarà possibile cambiare lo schema logico senza interferire coi programmi.

Il primo modello in grado di garantire queste proprietà è il modello relazionale, grazie al fatto che l’informazione viene conservata nelle tuple (e quindi negli insiemi di tuple ovvero le relazioni), che sono insiemi di attributi, che non fanno in alcun modo riferimento a supporti fisici.

# 3- Modello Relazionale

## Date le relazioni R1 di grado 3 e cardinalità 10 ed R2 di grado 5 e cardinalità 20, definire grado e cardinalità di una relazione, quindi stabilire grado e cardinalità di R1 x R2 nonché le precondizioni per l’applicazione dell’operatore, se esistenti.

Una relazione è un sottoinsieme del prodotto cartesiano di più domini, il suo grado è il numero di domini di cui si effettua il prodotto, mentre la cardinalità è il numero di n-uple della relazione. Il grado del prodotto cartesiano di due relazioni è la somma dei loro gradi, mentre la cardinalità è data dalla moltiplicazione delle cardinalità degli operandi. R1xR2 avrà quindi grado 8 e cardinalità 200.

## Descrivere brevemente perché il modello relazionale è anche detto modello “basato su valori” ed in cosa si differenzia rispetto ai modelli basati su “record e puntatori”. Specificare quale/i modello/i logico/i dei dati è/sono detto/i basato/i su “record e puntatori” ed il significato delle due espressioni.

Il modello relazionale è basato su valori proprio perché l’informazione è contenuta nelle tuple (insiemi di attributi che associano ad ogni attributo un valore del dominio dell’attributo), e quindi nelle relazioni, che sono insiemi di tuple. Il modello gerarchico, basato su record, e reticolare, basato su puntatori, usano delle strutture che fanno riferimento all’infrastruttura fisica dei dati, e che quindi non permettono di realizzare la proprietà di indipendenza dei dati dalla loro struttura fisica.

## Si definisca cosa è un vincolo di integrità per una base di dati relazionale; quindi, si riportano brevemente i vincoli di integrità conosciuti.

Un vincolo d’integrità è una proprietà che deve essere soddisfatta da una istanza di basi di dati per essere considerata corretta. È un predicato che associa ad ogni istanza il valore vero (l’istanza soddisfa il vincolo) o falso. I vincoli si dividono in intrarelazionali (coinvolgono una sola relazione alla volta) ed interrelazionali. I vincoli intrarelazionali si dividono a loro volta in vincoli di chiave (un attributo deve avere un valore unico in tutte le n-uple della relazione), vincoli di tupla (che può essere valutata a livello di tupla) e vincoli su valori (di dominio sull’attributo). Dei vincoli interrelazionali il più utilizzato è il vincolo di integrità referenziale, ovvero un vincolo in cui i valori di un attributo di una relazione compaiono come valori di chiave primaria di un’altra relazione.

## DBMS

### Si definisca brevemente cosa sia un DBMS (incluso il significato dell'acronimo), le sue principali caratteristiche e le diverse tipologie di utenti esistenti per esso.

Un Data Base Management System è un complesso sistema software in grado di gestire basi di dati che siano grandi (decine di miliardi di record…), condivise (con controlli su accesso e scrittura concorrente) persistenti (con un ciclo di vita separato rispetto alle applicazioni che le utilizzano), private (con access control lists) e che esegua transizioni che rispettino le ACID properties. Deve essere affidabile e resistente ai malfunzionamenti. Un DBMS rispetta un modello di dati, il che può introdurre vari livelli di astrazione dei dati (fisico e logico).

Oltre al DBA, Database Administrator, un DBMS viene usato dai progettisti della base di dati, responsabili di gestire lo schema della base di dati, dai programmatori che scrivono programmi che si interfacciano alla base di dati e dagli utenti, che possono usare il DB in modo regolare o occasionale, eseguendo operazioni diverse o prevedibili.

### Si descrivano brevemente i diversi livelli di isolamento di una transazione ed il motivo per cui sono stati introdotti.

La proprietà dell’Isolation di ACID richiede che le transazioni non si alterino fra di loro. Questa proprietà può essere difficile da rispettare senza sacrificare le performance, in quanto richiede l’assenza quasi totale di concorrenza (e quindi l’accodamento di transazioni concorrenti). Sono stati quindi classificati i problemi nati dalla concorrenza e sono stati definiti dei livelli di isolamento per “proteggere” una transazione da alcuni o tutti i problemi di concorrenza. I livelli sono:

1)  Read uncommitted: La transazione è vulnerabile ad anomalie di lettura sporca (lettura di valori intermedi di un’altra transizione), lettura inconsistente (lettura prima e dopo l’operazione di aggiornamento effettuata da un’altra transizione), aggiornamento fantasma (alterazione di parte delle variabili da parte di un’altra transazione), inserimento fantasma (comparsa improvvisa di una nuova tupla in una o più aggregazioni).

2)  Read committed: Evita solamente la lettura sporca

3)  Repeatable read: Non evita solamente l’inserimento fantasma

4)  Serializable: Evita tutte le anomalie (consigliato per tutte le transazioni che scrivono)

Sta al programmatore scegliere in base alle circostanze e ai requisiti di correttezza e/o di performance il livello di isolamento di ogni singola transazione.

# 4 - Algebra relazionale

## Si descriva brevemente l’operatore di join naturale, eventuali precondizioni per l’applicazione dell’operatore, qualora esistano, e quando un join naturale si dice completo.

Date due relazioni con attributi comuni definiti sugli stessi domini (precondizione), un join naturale è una relazione definita sull’unione degli insiemi degli attributi degli operandi. Le tuple del join naturale si ottengono combinando solamente le tuple degli operandi con valori uguali sugli attributi comuni.

Un join naturale viene definito completo quando ogni tupla di ciascun operando contribuisce ad almeno una tupla del risultato. Non esistono quindi dangling tuples, ovvero tuple che non possono essere utilizzate per la join in quanto l’altro operando non contiene tuple con gli stessi valori dell’attributo comune.

Al contrario, se gli operandi non hanno attributi comuni, tutte le tuple saranno dangling e il risultato sarà l’insieme vuoto.

### Si descriva brevemente quando un join naturale si dice completo.

Un join naturale viene definito completo quando ogni tupla di ciascun operando contribuisce ad almeno una tupla del risultato. Non esistono quindi dangling tuples, ovvero tuple che non possono essere utilizzate per la join in quanto l’altro operando non contiene tuple con gli stessi valori dell’attributo comune.

# 5 - Calcolo relazionale

### Descrivere brevemente i difetti del calcolo relazionale su domini per correggere i quali è stato introdotto il calcolo relazionale su tuple con dichiarazione di range. (Descrivere brevemente i difetti del calcolo relazionale su domini e come il calcolo relazionale su tuple con dichiarazioni di range ha permesso di correggere tali difetti)

Il calcolo relazione su domini, come dice il nome, è dipendente dal dominio e quindi il cambio del dominio implica il cambio della risposta all’interrogazione. Nel calcolo relazionale su tuple, il difetto è risolto tramite il costrutto della dichiarazione di range. Altro difetto è che ogni valore richiede una variabile, il che può portare a un grande numero di variabili, mentre nel calcolo relazionale su tuple le variabili indicano tuple.

# 6 – SQL

## Descrivere le caratteristiche principali di una procedura definita in SQL-2 standard e le eventuali differenze, se esistenti, rispetto alle procedure che possono essere scritte in SQL-3.

Il SQL 3 supporta i trigger (eventi composti da triplette evento-condizione-azione, che rendono una base di dati attiva). In SQL-2, si devono implementare sotto forma di vincoli di integrità, oppure integrare nelle applicazioni che si interfacciano alla base di dati. Inoltre, SQL-3 supporta il dominio elementare Boolean, che in SQL 2 si può “imitare” usando uno Smallint con dominio limitato ai parametri 0 e 1. SQL-3, infine, supporta le viste ricorsive.

## È possibile creare domini complessi in SQL? Quali sono i domini che SQL mette a disposizione?

È possibile creare dei domini personalizzati a partire da quelli elementari, ma è possibile solamente “restringere” il dominio attraverso la specifica di vincoli e di valori predefiniti. Non è generalmente possibile estendere i domini elementari (ad esempio non si possono creare record e array), a meno che non si usino estensioni non ufficiali del SQL pensate per basi di dati ad oggetti.

I domini elementari sono:

1)Stringhe: Character, character varying

2)Numeri: Numeric, decimal, integer, smallint

3)Numeri approssimati: float, double precision, real

4)Date (da SQL-2): date, time, timestamp e intervalli temporali (interval)

5\) Boolean, da SQL 3

# 7 – Diagrammi E-R

## Si descrivano brevemente le peculiarità e le finalità delle fasi di progettazione concettuale, logica e fisica.

La progettazione concettuale traduce le specifiche dei requisiti in uno schema concettuale, ovvero un riferimento a un modello concettuale, che consente di descrivere l’organizzazione dei dati in modo indipendente dallo schema logico (ovvero senza tenere conto del DBMS), dallo schema fisico e dal carico applicativo.

La progettazione logica traduce uno schema concettuale in uno schema logico che dipende dal modello dei dati scelto per la base di dati e quindi dalle ottimizzazioni necessarie.

La progettazione fisica, infine, produce lo schema fisico, che arricchisce lo schema logico con informazioni relative all’organizzazione fisica dei dati. Il modello fisico dipende dal DBMS specifico scelto.

# 9 – Progettazione logica

## Si descriva brevemente quali e quante sono le forme di ridondanza individuabili all’interno di un modello E-R.

Le forme di ridondanza individuabili sono gli attributi derivabili per ogni occorrenza, sia da altri attributi della stessa entità o associazione, sia da attributi di altre entità o associazioni, spesso tramite funzioni di aggregazione; Associazioni derivabili dalla composizione di altre associazioni, ovvero presenza di cicli (nota: la presenza di cicli non garantisce la presenza di una ridondanza).

## Illustrare brevemente: a) i motivi per cui è necessario effettuare l’analisi della ridondanza in fase di progettazione; b) i diversi tipi di ridondanza che si possono rilevare in un modello; c) i pro ed i contro che la presenza di ridondanza determina in particolar modo rispetto alle operazioni da svolgere e che vengono prese in considerazione in fase di analisi della ridondanza.

Quando bisogna ristrutturare un modello E-R per tenere conto del modello logico e del carico applicativo, bisogna effettuare l’analisi delle ridondanze, ovvero la decisione di introdurre, mantenere o cancellare le ridondanze rilevate. Le forme di ridondanza individuabili sono gli attributi derivabili per ogni occorrenza, sia da altri attributi della stessa entità o associazione, sia da attributi di altre entità o associazioni, spesso tramite funzioni di aggregazione; Associazioni derivabili dalla composizione di altre associazioni, ovvero presenza di cicli (nota: la presenza di cicli non garantisce la presenza di una ridondanza). Mantenere una ridondanza semplifica le interrogazioni, ma appesantisce (sia dal punto di vista del calcolo sia dal punto di vista dello spazio occupato) una base di dati. Bisogna decidere se “il gioco vale la candela” calcolando e confrontando il numero di accessi sia in presenza che in assenza di ridondanza.

# 10 – Normalizzazione

## Descrivere brevemente cosa è la normalizzazione e quali problemi risolve.

Una base di dati può soffrire di determinati difetti:

1)  Ridondanza, spreco inutile di spazio per ripetizione degli stessi dati.

2)  Anomalia di aggiornamento: per modificare un valore ridondante bisogna cambiare tutte le tuple in cui appare

3)  Anomalia di cancellazione: Per eliminare delle informazioni è necessario eliminarne anche altre

4)  Anomalia di inserimento: Per inserire dei dati bisogna inserirne (inventarsene) altri.

La normalizzazione è una procedura che trasforma schemi non normalizzati in schemi che soddisfano una forma normale. Una forma normale garantisce l’assenza di difetti come quelli elencati sopra.

## Si definisca cosa è una decomposizione senza perdita di informazione e quali condizione è possibile utilizzare per verificare tale proprietà. Opzionalmente fornire un esempio di decomposizione con perdita di informazione ed un esempio di decomposizione senza perdita di informazione.

Una relazione r si decompone senza perdita di informazione su due insieme di attributi X1 e X2 se il join naturale delle proiezioni su X1 e X2 della relazione è uguale a r (non contiene tuple spurie). La non perdita è garantita se gli attributi comuni formano una chiave per almeno una delle relazioni risultanti.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 35%" />
<col style="width: 32%" />
</colgroup>
<thead>
<tr class="header">
<th><u>Alunno</u></th>
<th><u>Professore</u></th>
<th>Università</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Palma</td>
<td>D’Amato</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Scigliuto</td>
<td>De Santis</td>
<td>Pisa</td>
</tr>
<tr class="odd">
<td>Palma</td>
<td>Fanizzi</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Melero</td>
<td>D’Amato</td>
<td>Bari</td>
</tr>
<tr class="odd">
<td>Melero</td>
<td>Impedovo</td>
<td>Bari</td>
</tr>
</tbody>
</table>

Con Alunno -\> Università (ogni alunno è iscritto a una sola università) e Professore -\> Università (ogni professore insegna in una sola università). Separando in base alle dipendenze funzionali:

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Professore</th>
<th>Università</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D’Amato</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Fanizzi</td>
<td>Bari</td>
</tr>
<tr class="odd">
<td>Impedovo</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>De Santis</td>
<td>Pisa</td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Alunno</th>
<th>Università</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Palma</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Scigliuto</td>
<td>Pisa</td>
</tr>
</tbody>
</table>

Se la definizione viene rispettata, quando effettuiamo il join naturale dovremmo riottenere r.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 35%" />
<col style="width: 32%" />
</colgroup>
<thead>
<tr class="header">
<th>Alunno</th>
<th>Professore</th>
<th>Università</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Palma</td>
<td>D’Amato</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Scigliuto</td>
<td>De Santis</td>
<td>Pisa</td>
</tr>
<tr class="odd">
<td>Palma</td>
<td>Fanizzi</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Melero</td>
<td>D’Amato</td>
<td>Bari</td>
</tr>
<tr class="odd">
<td>Melero</td>
<td>Impedovo</td>
<td>Bari</td>
</tr>
<tr class="even">
<td>Melero</td>
<td>Fanizzi</td>
<td>Bari</td>
</tr>
<tr class="odd">
<td>Palma</td>
<td>Impedovo</td>
<td>Bari</td>
</tr>
</tbody>
</table>

Abbiamo due tuple in più

TODO esempio senza perdita

# 11 – Progettazione fisica

## Illustrare brevemente quali sono i dati gestiti dal buffer (manager) e come avviene la sua gestione delle richieste.

I dati gestiti dal buffer manager sono il buffer stesso (un’area di memoria centrale organizzata in pagine) e una lista di variabili per ogni pagina gestita, ovvero il file e l’offset a cui si riferisce la pagina, un contatore per indicare quanti programmi la stanno utilizzando e un bit per indicare se la pagina è “sporca”, ovvero è stata modificata. In una richiesta di lettura, il BM incrementa il contatore di utilizzo (decrementandolo a richiesta terminata) e restituisce il riferimento alla pagina (leggendola prima dalla memoria secondaria se non presente nel buffer). In una richiesta di scrittura, la pagina viene segnata come sporca e poi scritta su memoria necessaria quando opportuno (ad esempio quando non c’è carico sul disco), o quando richiesto dal gestore dell’affidabilità.

## Elencare ed illustrare brevemente le strutture usate da un DBMS per organizzare i file (e le strutture primarie dei file) a livello fisico.

Nella struttura sequenziale, un file è costituito da vari blocchi di memoria logicamente consecutivi e le tuple sono inserite in questi blocchi, rispettando una sequenza seriale (in ordine di immissione), di array (la loro posizione dipende dal valore assunto dalla tupla in un campo di indice) e ordinata (la sequenza dipende dal valore assunto in un campo).

Struttura ad hash: di ogni chiave viene calcolato un hash che determina la locazione fisica della tupla. È efficiente per accessi diretti ma non per ricerche ad intervalli. Bisogna inoltre gestire le collisioni hash e dare agli hash uno spazio.

Struttura ad albero, dette anche indici, favoriscono entrambi i tipi di accesso ed infatti vengono utilizzate sia nelle strutture primarie (ovvero che contengono i dati), sia in quelle secondarie (che favoriscono l’accesso ai dati senza contenerli).

## B Tree

### Illustrare brevemente cosa sia un B+-Tree, le sue caratteristiche principali e per quali scopi viene utilizzato.

Il B+ tree è un B-tree, ovvero un albero di ricerca in cui ogni foglia contiene n chiavi, in cui i nodi foglia sono collegati tra loro tramite una linked list, nell’ordine della chiave. Ciò consente di rendere efficienti le ricerche su interi intervalli. A differenza del b-tree, i nodi intermedi di un b+tree non possono contenere chiavi. Viene utilizzato come implementazione fisica per un indice in un DBMS, in modo da rendere più efficiente l’accesso ad una chiave.

### Determinare quali azioni possono essere necessarie su una struttura dati di tipo B-Tree, in caso inserimenti e cancellazioni di tuple. Descrivere tali azioni motivandone la necessità.

Un B-tree è un albero di ricerca in cui ogni foglia ha una capienza di n chiavi viene mantenuta parzialmente piena. permette di evitare bilanciamenti dell’albero ad ogni operazione. I nodi contengono puntatori a figli ma anche dati. Ciò

Nell’inserimento, se non c’è più spazio nella foglia, essa va suddivisa (split) salvando il nuovo puntatore nel nodo genitore, ma se non c’è posto nel nodo genitore, si deve salire ancora, fino eventualmente al nodo radice. Al contrario, nella cancellazione di tuple, bisogna unire fra loro le foglie troppo vuote (merge) e rimuovere il puntatore alla vecchia foglia dal genitore, il che, come nel caso precedente, può causare un merge ricorsivo.

## Si descriva brevemente i/il criterio di ottimizzazione delle query implementato dal gestore di query di un DBMS.

Il gestore delle query deve partire da un’istruzione SQL e scegliere la strategia realizzativa più ottimizzata possibile. Per far ciò, viene costruito un albero di decisione che contiene i vari piani di esecuzione, scegliendo il piano di costo minore (ma non minimo, essendo un problema di ricerca euristica). I piani di esecuzione vengono ottimizzati sia sfruttando le proprietà dell’algebra relazionale (“spingere” le selezioni verso le relazioni, infatti, diminuisce il grado di eventuali join e prodotti cartesiani, diminuendone quindi il costo di esecuzione), sia attraverso analisi statistiche ed euristiche sul volume di dati.

# 12 - SQL e applicazioni

## Si definisca brevemente cosa siano i trigger, il paradigma su cui sono basati, vantaggi e svantaggi per essi.

Il meccanismo dei trigger consente di rendere una base di dati reattiva al cambiamento. Un trigger è una tripla Evento-Condizione-Azione. All’accadere dell’Evento, tipicamente un aggiornamento, il DBMS controlla se la Condizione è soddisfatta; se lo è, il DBMS esegue l’Azione prevista. I trigger di solito vengono usati per Calcolare dati derivati da inserimenti, gestire eccezioni, rispetto di vincoli di integrità complicati. L’uso dei trigger “sposta” l’applicazione delle regole dalle applicazioni che usano la base di dati alla base di dati; in questo modo, non bisogna programmare più volta la stessa regola nei vari linguaggi di programmazione

## Descrivere brevemente in cosa consiste SQL Embedded e per quale motivo viene introdotto.

SQL embedded introduce e integra le istruzioni SQL in un linguaggio di programmazione, tramite un precompilatore che riconosce costrutti speciali per la connessione a un database e per l’esecuzione di query SQL. In questo modo i programmatori non devono abbandonare completamente il linguaggio di programmazione per usare una base di dati ma devono solo imparare la sintassi del precompilatore

## Illustrare brevemente cosa sia il conflitto di impedenza e quali soluzioni esistano per gestirlo.

Quando si usa SQL embedded, ovvero si integra SQL in un linguaggio di programmazione, accade un conflitto di impedenza quando il linguaggio di programmazione non supporta una struttura dati del tipo “insieme di righe”, ma opera solo su righe singole (approccio tuple-oriented). SQL, infatti, opera su tabelle e restituisce tabelle. Per risolvere questo problema si può usare un altro linguaggio che supporti l’insieme di righe (di solito i linguaggi OO), oppure si introduce il cursore, struttura dati ausiliaria che trasmette le ennuple al programma una alla volta. Facendo avanzare il cursore, si può accedere a tutte le ennuple.

## Nello sviluppo di applicazioni mediante linguaggi che ospitano SQL, illustrare quando è possibile utilizzare SQL statico e quando invece è necessario utilizzare SQL dinamico. Illustrare quindi la differenza tra SQL statico e SQL dinamico.

SQL statico viene usato per le interrogazioni che hanno una struttura costante ma con parametri variabili; SQL dinamico invece viene usato per interrogazioni con struttura variabile. SQL statico viene precompilato per una maggiore efficienza, mentre l’interrogazione SQL dinamica va prima preparata se possibile (con il comando PREPARE), ad esempio se si viene a conoscenza dell’interrogazione da effettuare poco prima delle variabili da utilizzare nell’interrogazione, altrimenti può anche essere eseguita immediatamente (col comando EXECUTE IMMEDIATE). In questo caso, però, il DBMS non potrà ottimizzare la query in anticipo.

## Si descriva brevemente cosa sia un cursore e per risolvere quale problema viene introdotto. Si chiarisca inoltre la differenza tra cursori statici e dinamici ed in quale circostanza vengono usati gli uni o gli altri.

Il cursore è un meccanismo che consente di risolvere il conflitto di impedenza, ovvero l’impossibilità di un linguaggio di programmazione di agire su intere tabelle (linguaggi tuple-oriented). Il cursore “punta” a una determinata tupla del risultato, ed è possibile leggere la tupla puntata e spostare il cursore. I cursori statici vengono usati in SQL statico, mentre i cursori dinamici nel SQL dinamico. Nel caso del SQL dinamico, è possibile specificare parametri di ingresso e di uscita usando rispettivamente le clausole USING e INTO.

## Si descriva brevemente cosa siano le operazioni di COMMIT e ROLLBACK e quando esse vengono usate.

Un programma applicativo viene trattato dal sistema come un’unica transazione. Per gestire gli errori e per evitare lunghi blocchi a causa della lunga durata del programma, è necessario suddividere il lavoro in più transizioni, confermandole quando concluse con l’operazione di COMMIT, che finalizza e conferma la transazione, o annullandole con ROLLBACK, ad esempio in caso di errore.

## Descrivere brevemente cosa sia un privilegio, a cosa serve, come può essere concesso e revocato e rispetto a quali risorse e/o azioni

Il permesso è la concessione di una determinata azione (inserzione, modifica, cancellazione, lettura, obbligo di rispetto di vincoli di integrità referenziale, utilizzo in definizione di dominio) ad un determinato utente o gruppo di utenti (si concedono i permessi a un ruolo e si assegnano gli utenti al ruolo), dando opzionalmente la possibilità di trasmettere questo permesso ad altri utenti. L’azione viene limitata a una singola risorsa (un attributo, una relazione, un database…). I permessi ovviamente vengono usati per restringere l’utilizzo e la modifica della base di dati ai soli dati richiesti dall’applicazione, per motivi di sicurezza, di privacy e di affidabilità (per prevenire la cancellazione accidentale di dati richiesti da altri).

Si possono concedere/revocare permessi col comando GRANT/REVOKE permesso ON risorsa to Utente (with grant option, per trasmettere)

# 13 - RDF

## Descrivere brevemente RDF e quale sia il suo linguaggio di interrogazione.

L’RDF (Resource Description Framework), nato per il semantic web, descrive dati con conformazione irregolare, rappresenta informazioni tramite un grafo in cui i nodi sono soggetti e oggetti e gli archi sono predicati. Il soggetto può essere un IRI (Internationalized Resource Identifier), ovvero una stringa che identifica una risorsa o un blank node (identificatori per risorse anonime, preceduti da underscore). Il predicato deve essere un IRI, mentre l’oggetto può essere un IRI, un letterale (un valore che descrive la risorsa) o un blank node. Esistono tre rappresentazioni fisiche di RDF: 1) N-Triples: Lista di triple soggetto-predicato-oggetto 2) N3: Descrizione di una risorsa alla volta con tutte le sue proprietà 3) XML

SPARQL (Simple Protocol and RDF Query Language) è un linguaggio di interrogazione simile a SQL. Come in SQL, infatti, è possibile effettuare interrogazioni con SELECT, DESCRIBE, specificando gli endpoint con FROM, condizioni con WHERE e modificando il risultato con ORDER BY e LIMIT.

## Definire cosa siano RDF ed RDFS e le differenze tra di essi.

L’RDF (Resource Description Framework) descrive dati di conformazione irregolare rappresentando informazioni tramite un grafo in cui i nodi sono soggetti e oggetti e gli archi sono predicati. L’RDF descrive solamente istanze di triple, senza alcuno schema, il che porta ad una bassa espressività del linguaggio.

RDFS (RDF Schema) aggiungere a RDF dei costrutti per descrivere metadati, ovvero per descrivere le risorse di un RDF e le relazioni tra esse. È quindi possibile strutturare una istanza RDF e anche definire relazioni di generalizzazione fra classi e proprietà.

# Vario

## Illustrare brevemente cosa siano: algebra relazionale, calcolo relazionale ed SQL, le loro peculiarità e la relazione che intercorre tra di essi. 

L’algebra relazionale è un linguaggio procedurale basato su concetti algebrici (operatori su relazioni che producono relazioni). Il calcolo relazionale, invece, è una famiglia di linguaggi dichiarativi di interrogazione, basati sul calcolo dei predicati del primo ordine, che comprende il calcolo relazionale su domini (il cui risultato dipende dal dominio) e il calcolo relazionale su tuple con dichiarazione di range (che non consente di esprimere le unioni indipendenti), a cui si ispira SQL (Structured Query Language), che è sia un Data Definition Language sia un Data Manipulation Language. Ingloba quindi il calcolo relazionale e lo completa con l’espressione UNION.
