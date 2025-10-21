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

> **CENTROIDE: Il centroide è il centro di massa di un set di punti, di cui la definizione matematica è:**
> $$\vec\mu(C) = \frac{1}{|C|}\times \sum_{d\in C}\vec d$$
> dove $C$ è un insieme di documenti.



