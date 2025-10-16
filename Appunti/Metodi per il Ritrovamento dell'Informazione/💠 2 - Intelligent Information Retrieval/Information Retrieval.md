#mri 
___
# **Modello di Retrieval**
L'**information retrieval** intelligente si basa sulla definizione di un **modello di retrieval**. 
Un modello di questo tipo specifica i dettagli della rappresentazione di un documento, della rappresentazione della query e della funzione di retrieval. Determina anche la **rilevanza**, che può essere *binaria* oppure *continua*, ovvero puo' essere **rilevante/non rilevante** o avere solo un **punteggio di similarità**.
<u><b>La funzione di ranking assegna punteggi ai documenti a una data query</b></u>.

Un modello di Information Retrieval e' definito come una quadrupla

$$[D,Q,F,R(q_i,d_j)]$$

dove:
- $D$ e' l'insieme delle viste logiche dei **documenti**,
- $Q$ e' l'insieme delle viste logiche delle **query utente**
- $F$ e' il **framework utilizzato per modellare i documenti e le query**,
- $R(q_i, d_j)$ e' la **funzione di ranking**.


I modelli di retrieval possono essere classificati in:
- <u>modelli booleani</u>: *theroetic set*, *extended boolean*,
- <u>modelli vector space</u>: *statistical/algebric*,
- <u>modelli probabilistici</u>.
## **Pre-processing**
Prima che i documenti possano essere indicizzati, e' necessaria una serie di passaggi di *pre-elaborazione*, essenziali per **normalizzare** il testo:
1. **Strip unwanted characters/markup**: Rimozione di caratteri indesiderati, punteggiatura, numeri, ecc.
2. **tokenization**: Il testo viene diviso in **token** (parole chiave), basandosi sugli spazi. Si creano qui due sfide: gestione dei termini ipotetici e dei numeri, che i **sistemi IR** meno recenti tendevano a non indicizzare. Inoltre, alcune lingue asiatiche non utilizzano spazi tra le parole, richiedendo algoritmi specifici.
3. **normalization to terms**: l'obiettivo di questa fase e' di portare le parole indicizzate e i termini della query alla stessa forma standard.
   Si definiscono in questa fase le **classi di equivalenza**. (*case folding*, gestione degli accenti, ecc.)
4. **stopword removal**: Rimozione delle parole più comuni che hanno scarso contenuto semantico (circa il 30% delle *postings*). Questa fase sta pian piano scomparendo grazie al miglioramento di compressione e ottimizzazione delle query.
5. **stemming and lemmatization**:
	- **lemmatization**: Questa fase riduce le forme flessive/varianti alla forma base del dizionario (es. *am*, *are*, *is* $\to$ *be*).
	- **stemming**: Riduce i termini alle loro **radici** tramite un troncamento di affissi (**NOTA BENE: dipende dalla lingua**). L'algoritmo più comune per l'inglese e' l'**algoritmo di Porter**.
Infine, dopo la pre-elaborazione, si procede alla costruzione dell’**indice invertito** (_inverted index_), dove per ogni termine viene conservata una lista di *posting* (identificatori di documento) che contengono quel termine. 

## **Modello Booleano**
Il **modello booleano** e' il modello piu' semplice su cui costruire un **sistema IR**.
In questo modello:
- **rappresentazione**: un documento e' rappresentato come un **insieme di parole chiave**.
- **query**: Le query sono **espressioni booleane** di parole chiave connesse tramite **connettivi logici** (**and**, **or**, **not**), supportando le parentesi.
- **output**: il risultato del modello booleano ovviamente e' binario (documento **rilevante** o **non rilevante**). Non esistono *partial matches* ne' meccanismi di ranking.
- **implementazione**: L'implementazione di un modello booleano si basa su **vettori di incidenza *termine-documento* (0 se la parole non e' presente, 1 se lo e')**. Le query vengono risolte tramite operazioni ***bitwise*** sui vettori.

Il principale vantaggio di questo modello e' essere efficace per utenti esperti che possiedono una comprensione precisa delle loro necessita' informative.
Tuttavia, il modello e' afflitto da problemi significativi che hanno spinto verso modelli di retrieval con sistema di ranking. 
**Il modello booleano infatti presenta alcune criticita':**
1. **rigidità**: l'operatore *bitwise* `and` significa **tutto** (troppi pochi risultati), l'operatore `or` significa **alcuni** (troppi risultati).
2. **problema *feast or famine***: si richiede molta abilita' per formulare una query che restituisca un numero gestibile di risultati: infatti le query booleane spesso producono o troppo pochi o troppi risultati.
3. **mancanza di ranking**: il sistema non classifica l'output, poiche' tutti i documenti corrispondenti sono considerati ugualmente rilevanti.
4. **relevance feedback**: integrare il ***relevance feedback*** (*modifica della query basata sulla valutazione di rilevanza fornita dall'utente*) e' molto complesso.

Il modello booleano adotta una logica di tipo _set-theoretic_: o un documento appartiene all’insieme dei risultati, oppure no.
## **Transizione verso modelli piu' complessi**
Per superare i limiti del modello booleano, si e' passati a **modelli di *ranked retrieval***. In questi modelli (come il *Vector Space Model*), l'obiettivo e' di ordinare i documenti in base a un punteggio di somiglianza con la query (spesso query in linguaggio naturale) invece di espressioni booleane.
Questo approccio permette di mostrare solo i primi $K$ risultati, risolvendo il problema ***feast or famine*** e non sopraffacendo l'utente. Il punteggio di somiglianza tiene conto di vari fattori (che il modello booleano invece ignora):
- **term frequency**: la frequenza dei termini che si trovano sia nella query che nel documento;
- **inverse document frequency**: la rarita' dei termini all'interno della query e del documento.

## **Modello di Jaccard**
Il **coefficiente di Jaccard** e' un modo molto semplice per quantificare quanto due insiemi si sovrappongono:
$$\text{Jaccard(A,B)} = \frac{|A\cap B|}{|A \cup B|}$$
in cui il:
- **il numeratore** indica quante parole hanno in comune (*intersezione*);
- **il denominatore** indica quante parole compaiono in totale nei due insiemi (*unione*).
Il risultato e' sempre tra $0$ e $1$ in cui lo $0$ indica che non ci sono parole in comune, mentre $1$ indica una **perfetta sovrapposizione**.

> **Esempio**:
> 
> Query: {ides, of, march}
> 
> Doc 1: {caesar, died, in, march}
> 
> - Intersezione $\to$ {march} $\to$ 1
> - Unione $\to$ {ides, of, march, caesar, died, in, march} $\to$ 6
> 
> $\text{Jaccard(A, B)} = \frac{1}{6} = 0.166\dots$

Questo metodo tuttavia ha alcuni limiti:
- **rappresenta solo un indice di similarità**, ovvero quanto un documento e' simile alla query cercata;
- **non considera il *term frequency***: non considera quante volte compare una parola;
- **non distingue parole rare da parole comuni**: tutte le parole hanno lo stesso peso (l'*idf* invece si).
## **Modello *Bag of Words***
Il modello **Bag of Words** stabilisce che la rappresentazione vettoriale di un documento non tiene conto dell'ordine delle parole al suo interno.
La *term frequency* $\text{tf}_{\text{t,d}}$ e' definita come il numero di volte in cui il termine $t$ ricorre nel documento $d$. 
Un grosso limite di questo modello e' che la **frequenza grezza del termine non basta**: Un documento con 10 occorrenze di un termine e' piu' rilevante di uno con 1 occorrenza, ma non e' 10 volte piu' rilevante. Pertanto ***la rilevanza non aumenta in modo proporzionale con la frequenza del termine***.
Per ovviare a cio' si utilizza la **ponderazione logaritmica della frequenza**:

$$
w_{t,d} =
\begin{cases}
1 + \log_{10}(\text{tf}_{t,d}) & \text{se } \text{tf}_{t,d} > 0 \\
0 & \text{altrimenti}
\end{cases}
$$

Questa formula definisce la **scalatura sublineare di $\text{tf}$**, ovvero una tecnica matematica usata per ridurre l'impatto (il peso) dei termini molto frequenti in un documento, senza annullarli del tutto: questo significa che la crescita del peso di un termine non e' proporzionale (lineare), ma molto piu' lenta.

> **Esempio**:
> 
> Nel modello _Bag of Words_, se un termine appare:
> - 1 volta → $\text{tf} = 1$
> - 10 volte → $\text{tf} = 10$
> - 100 volte → $\text{tf} = 100$
>
Un modello **lineare** considererebbe il termine 100 volte più importante nel terzo caso.  
Ma questo **non è realistico**: se una parola compare 100 volte, non significa che il documento sia 100 volte più rilevante — spesso si tratta solo di una parola comune nel testo.

Il peso cresce, ma **molto meno rapidamente**: un termine che compare 1000 volte non vale 1000 volte di più, ma solo 4 volte di più.

Il punteggio per una **coppia documento-query** e' calcolato come la somma, sui termini $t$ presenti sia nella query $q$ che nel documento $d$, dei pesi *log-frequency*:

$$\text{score}(d, q) = \sum_{t \in q \cap d} \left( 1 + \log_{10}(\text{tf}_{t,d}) \right)$$

Il punteggio e' 0 se nessuno dei termini della query e' presente nel documento.

## **L'importanza della rarita'**
I termini rari in un'intera collezione sono considerati piu' informativi dei termini molto frequenti (es. *stop words*). Per quantificare questa rarita', si usa la ***document frequency***, definita come il numero dei documenti nella collezione che contengono il termine $t$. $df$ e' una misura inversa dell'informativita' di $t$
L'***inverse document frequency*** (*idf*) di $t$ e' definita come segue: 

$$\text{idf}_t = \log_{10}\left(\frac{N}{\text{df}_t}\right)$$

dove:
- $N$ e' il numero totale di documenti.


Il logaritmo viene usato per smorzare l'effetto dell'*idf*. L'*idf* e' una funzione che dipende solo da $t$ e non dal documento.

> **Nota**:
> È importante notare che l'idf **non ha effetto sul ranking** per le query composte da un solo termine. **Tuttavia, per query con due o più termini, la pesatura $idf$ fa sì che le occorrenze del termine più raro contino molto di più nel ranking finale rispetto a quelle del termine più frequente**.

## **Lo Schema di Pesatura $tf-idf$**
Il peso $tf-idf$ di un termine e' il prodotto del suo peso $tf$ (*spesso logaritmico*) e del suo peso $idf$: 

$$w_{i,d} = (1+\log_{10} tf_{t,d} \times idf_t)$$

Questo è lo schema di pesatura più noto in IR. Il peso tf-idf ha due proprietà desiderate:
- **aumenta con il numero di occorrenza del termine all'interno del documento**;
- **aumenta con la rarita' del termine nella collezione**.

Il punteggio finale per una coppia $(d,q)$ e' dato dalla somma dei pesi $tf - idf$ per tutti i termini $t$ che si trovano sia nella query che nel documento:

$$score(d,q) = \sum_{t\in q\cap d}tf_{t,d} \times idf_t$$


## **Il Modello Spazio Vettoriale (VSM) e la Similarità Cosine**
Il **modello spazio vettoriale*** rappresenta sia la query che i documenti come vettori pesati $tf-idf$. I termini fungono da assi in uno spazio vettoriale di dimensione $|V|$, mentre i documenti sono i punti o i vettori in questo spazio.
L'idea chiave e' quella di rankare i documenti in base alla loro prossimita' al vettore della query in questo spazio.

La distanza euclidea si rivela una **pessima misura di prossimita'**, in quanto e' troppo influenzata dalla lunghezza dei vettori (ovvero dalla *lunghezza dei documenti*). Un documento e la sua copia appesa a se stesso avrebbero una grande distanza euclidea pur avendo lo stesso contenuto semantico.

Per superare questo problema, si e' deciso di utilizzare l'angolo tra i vettori come misura di similarita'.

## **Normalizzazione e Coseno di Similitudine**
Prima di misurare l'angolo, si procede alla normalizzazione della lunghezza: il vettore viene normalizzato **dividendo ciascuna delle sue componenit per la sua norma L2**. Questo produce un vettore unitario. L'effetto risultante e' che i documenti lunghi e corti ora hanno pesi comparabili, e i documenti **semanticamente** ***equivalenti*** avranno vettori identici dopo la normalizzazione.

**Norma L2:**

$$||\vec{x}||_2 = \sqrt{\sum_i x_i^2}$$

Rankare i documenti in modo decrescente dell'angolo e' equivalente a rankarli in ordine crescente del **coseno dell'angolo** (il coseno e' **monotonicamente decrescente nell'intervallo 0 - 180 gradi**)

$$
cos(\vec{q},\vec{d}) = \frac{\vec{q}\cdot\vec{d}}{|\vec{q}||\vec{d}|} = \frac{\vec{q}}{|\vec{q}|}\cdot\frac{\vec{d}}{|\vec{d}|} = \frac{\sum_{i+1}^{|V|}q_i\cdot d_i^2}{\sqrt{\sum_{i=1}^{|V|}q_i^2} \cdot \sqrt{\sum_{i=1}^{|V|}d_i^2}}
$$

dove:
- $q_i$ e' il peso $tf-idf$ del termine i nella query;
- $d_i$ e' il peso $tf-df$ del termine i nel documento.

Per i vettori $q$ e $d$ che sono gia' normalizzati in lunghezza, la **similarita' coseno** e' semplicemente il loro ***prodotto scalare***.P