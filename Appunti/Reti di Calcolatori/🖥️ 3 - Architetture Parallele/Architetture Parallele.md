#reti 
___
Le architetture parallele rappresentano un'evoluzione significativa rispetto al tradizionale computer ***monoprocessore***. Quest'ultimo e' un architettura **monolitica** in cui un unico processore principale e' supportato da coprocessori specializzati per compiti specifici.
Al contrario, le architetture parallele prevedono la presenza di **piu' processori** che elaborano **contemporaneamente** piu istruzioni, appartenenti a uno o piu' programmi. Queste architetture sono importanti per comprendere le **reti moderne**.
## **Obiettivi delle Architetture Parallele**
L'adozione di architetture parallele persegue due obiettivi principali:
- **Miglioramento delle prestazioni** del sistema complessivo;
- **Miglioramento del rapporto costo/prestazioni**.
L'idea di fondo non e' tanto eseguire lo stesso problema in meno tempo, quanto piuttosto di risolvere **problemi piu' grandi e complessi** nello stesso lasso di tempo che sarebbe stato necessario con un'architettura tradizionale.
## **Classificazione di Flynn**
Una tassonomia fondamentale per comprendere le architetture parallele e' la **classificazione di Flynn**, che categorizza i sistemi in base a due caratteristiche essenziali:
- **instruction streams**: numero di *flussi di istruzioni*;
- **data streams**: numero di *flussi di dati*.

Dalle varie combinazioni derivano 4 categorie distinte:
- **SISD (*Single Instruction Single Data*)**: sistemi con un singolo flusso di istruzioni e un singolo flusso di dati. Questa architettura **non consente** l'esecuzione parallela di istruzioni ne il flusso parallelo di dati. In un dato istante, viene eseguita una sola istruzione che manipola un solo insieme di dati.

- **SIMD (*Single Instruction Multiple Data*)**: sistemi in cui una singola istruzione viene applicata **contemporaneamente** a **molti dati**. Ideale per operazioni che coinvolgono molti dati che possono essere processati in parallelo.

- **MISD (*Multiple Instruction Single Data*)**: sistemi con un **flusso di istruzioni multiplo**ma un singolo flusso di dati. Non esistono calcolatori che rientrino **puramente** in questa categoria.

- **MIMD (*Multiple Instruction Multiple Data*)**: sistemi in grado di eseguire **piu' istruzioni** contemporaneamente utilizzando **piu' unita' di calcolo**. All'interno di questa categoria si possono distinguere due importanti sottocategorie:
	- **lousely coupled**: sistemi a **collegamento lasco**: sistemi in cui ogni processore risiede in un **calcolatore diverso**, connesso in rete agli altri; ogni nodo della rete ha le proprie risorse e ogni processore lavora in modo **indipendente** oppure **comunica** con gli altri.
	- **tightly coupled**: sistemi a **collegamento stretto**: sistemi in cui tutti i processori sono situati nello stesso calcolatore; condividono pertanto le stesse risorse, ma portano il vantaggio della velocita' di dialogo.