#mri 
___
# **Modello di retrieval**
L'**information retrieval** intelligente si basa sulla definizione di un **modello di retrieval**. 
Un modello di questo tipo specifica i dettagli della rappresentazione di un documento, della rappresentazione della query e della funzione di retrieval. Determina anche la **rilevanza**, che può essere *binaria* oppure *continua*. <u><b>La funzione di ranking assegna punteggi ai documenti a una data query</b></u>

Un modello di Information Retrieval e' definito come una quadrupla:
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
Tuttavia, il modello e' afflitto da problemi significativi che hanno spinto verso modelli di retrieval con sistema di ranking. Il modello booleano infatti presenta alcune criticita':
1. **rigidità**: l'operatore *bitwise* `and` significa **tutto** (troppi pochi risultati), l'operatore `or` significa **alcuni** (troppi risultati).
2. **problema *feast or famine***: si richiede molta abilita' per formulare una query che restituisca un numero gestibile di risultati: infatti le query booleane spesso producono o troppo pochi o troppi risultati.
3. **mancanza di ranking**: il sistema non classifica l'output, poiche' tutti i documenti corrispondenti sono considerati ugualmente rilevanti.
4. **relevance feedback**: integrare il ***relevance feedback*** (*modifica della query basata sulla valutazione di rilevanza fornita dall'utente*) e' molto complesso.
## **Transizione verso modelli piu' complessi**
Per superare i limiti del modello booleano, si e' passati a **modelli di *ranked retrieval***. In questi modelli (come il *Vector Space Model*), l'obiettivo e' di ordinare i documenti in base a un punteggio di somiglianza con la query (spesso query in linguaggio naturale) invece di espressioni booleane.
Questo approccio permette di mostrare solo i primi $K$ risultati, risolvendo il problema ***feast or famine*** e non sopraffacendo l'utente. Il punteggio di somiglianza tiene conto di vari fattori (che il modello booleano invece ignora):
- **term frequency**: la frequenza dei termini che si trovano sia nella query che nel documento;
- **inverse document frequency**: la rarita' dei termini all'interno della query e del documento.

## **Indice di Jaccard**
Il **coefficiente di Jaccard** e' un modo molto semplice per quantificare quanto due insiemi si sovrappongono:
$$\text{Jaccard(A,B)} = \frac{|A\cap B|}{|A \cup B|}$$
in cui il:
- **il numeratore** indica quante parole hanno in comune (*intersezione*);
- **il denominatore** indica quante parole compaiono in totale nei due insiemi (*unione*).
Il risultato e' sempre tra $0$ e $1$ in cui lo $0$ indica che non ci sono parole in comune, mentre $1$ indica una **perfetta sovrapposizione**.

> Esempio
> Query: {ides, of, march}
> Doc 1: {caesar, died, in, march}
> 
> - Intersezione $\to$ {march} $\to$ 1
> - Unione $\to$ {ides, of, march, caesar, died, in, march} $\to$ 6
> 
> $\text{Jaccard(A, B)} = \frac{1}{6} = 0.166\dots$

Questo metodo tuttavia ha alcuni limiti:
- **rappresenta solo un indice di similarità**, ovvero quanto un documento e' simile alla query cercata;
- **non considera il *term frequency***: non considera quante volte compare una parola;
- **non distingue parole rare da parole comuni**: tutte le parole hanno lo stesso parole (l'*idf* invece si).