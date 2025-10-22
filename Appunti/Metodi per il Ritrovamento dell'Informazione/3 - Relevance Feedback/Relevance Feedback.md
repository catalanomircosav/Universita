#mri 
___
# **Relevance Feedback**
Il concetto di ***relevance feedback*** si basa sull'utilizzo del feedback fornito dall'utente sulla rilevanza dei documenti per migliorare la rappresentazione del bisogno informativo.
## **Il processo**
Il relevance feedback segue due passaggi iterativi:
1. L'utente deve porre una query, **breve e semplice**;
2. Il sistema restituirà un set iniziale di risultati, che l'utente deve esaminare e marcare alcuni documenti come **rilevanti** o **non rilevanti**.
	1. Il feedback può essere **implicito** (*operazioni fatte dall'utente*) o **esplicito** (*riformulazione della query*)
3. Con questo feedback, il sistema calcola una rappresentazione della query che sia migliore e più vicina al reale bisogno informativo dell'utente.

> **NB: QUESTO PROCESSO PUO' ESSERE RIPETUTO PIU' E PIU' VOLTE**

L'idea al centro di questo sistema è che l'utente non è capace di formulare una query efficace se non conosce la collezione di documenti, e l'iterazione fornisce una soluzione a questa difficoltà.

> **CENTROIDE: Il centroide è il centro di massa di un set di punti, di cui la definizione matematica (*centroide non normalizzato*) è:**
> $$\vec\mu(C) = \frac{1}{|C|}\times \sum_{d\in C}\vec d$$
> dove $C$ è un insieme di documenti.

## **Algoritmo di Rocchio**
L'*algoritmo di Rocchio* è un metodo che sfrutta il modello dello *spazio vettoriale* per determinare una query di *relevance feedback*. L'obiettivo è di trovare una query **ottimale**che **riesca a separare i documenti *rilevanti* da quelli *non rilevanti***:
(*centroide dei documenti rilevanti meno il centroide dei documenti non rilevanti*)

$$\vec q_{opt} = \frac{1}{|C_r|}\times\sum_{\vec d_j \in C_r}\vec d_{j}\space - \frac{1}{N - |C_r|}\times\sum_{\vec d_j\not\in C_r} \vec{d_j}$$

dove:
- $\vec{q}_{opt}$ è il vettore di risultati perfetti; 
- $D_r$ è l'insieme dei documenti (*D*) rilevanti (*r*) tra i documenti ritrovati;
- $N_r$ è la cardinalità di $D_r$;
- $D_n$ è l'insieme dei documenti (*D*) **non** rilevanti (*n*) tra i documenti ritrovati;
- $C_r$ è l'insieme dei documenti rilevanti nell'**intera collezione** (*diverso da $D_r$*);
- $N$ è la cardinalità dell'intera collezione;
- $\alpha, \beta, \gamma$ sono **costanti di Tuning**, usate per bilanciare i contributi dei diversi fattori nella formula.

> **PROBLEMA: NON SI CONOSCE A PRIORI L'INTERA COLLEZIONE, PERCIO' PRIMA DI APPLICARE L'ALGORITMO BISOGNA EFFETTUARE UNA QUERY DI ESPLORAZIONE.**
> **SOLUZIONE: LA SOLUZIONE E' QUELLA DI AVERE UN SOTTOINSIEME DI DOCUMENTI SCELTI DALL'UTENTE**.

La **query modificata** viene definita come una combinazione lineare della query originale, del centroide dei documenti rilevanti noti e del centroide dei documenti non rilevanti noti:

$$q_m = \alpha\cdot q_0 + \beta\times\frac{1}{|D_r|}\times\sum_{d_j\in D_r} d_j - \gamma\cdot\frac{1}{|D_n|}\times\sum_{d_j\in D_n}d_j$$

in questa formula, $\alpha,\beta,\gamma$ sono peso scelti **empiricamente** o **a mano**. L'effetto è che **la nuova query si sposta verso i documenti rilevanti noti e si allontana da quelli non rilevanti noti**.

Tuttavia, l'algoritmo di per se porta alcuni problemi:
- l'allungamento della query porta **inefficienza**;
- mancanza di feedback o svogliatezza dell'utente;
- inconsistenza nel ritrovamento delle informazioni con le stesse query;
- necessità di avere risultati diversi in momenti diversi;