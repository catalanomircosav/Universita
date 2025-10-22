#map 
____
# **Principio di astrazione**
> "*E' possibile costruire astrazione su una qualunque classe sintattica, purché le frasi di quella classe specifichino un qualche tipo di computazione.*"

Al momento, esistono sei classi sintattiche, che corrispondono a sei tipi di astrazione differenti:
- **espressione** $\to$ *astrazione di funzione* (valutazione di un espressione)
- **comando** $\to$ *astrazione di procedura* (esecuzione di un comando)
- **controllo di sequenza** $\to$ *astrazione di controllo* (controllo di sequenza)
- **accesso a un'area di memoria** $\to$ *astrazione di selettore* (accesso a una variabile)
- **definizione di un dato** $\to$ *astrazione di tipo* (dichiarazione di nuovi tipi)
- **dichiarazione** $\to$ *astrazione generica* (binding di tipi)

## **Astrazione di funzione**
Un'astrazione di funzione include un'**espressione da valutare** e, quando chiamata, **dara' un valore come risultato**.

E' definita come: 
```
function I(FP1;...;FPn) is E
```
dove `I` e' un **identificatore**, `FP1;...;FPn` sono **parametri formali** ed `E` l'**espressione** da valutare.

In questo modo si lega `I` all'astrazione di funzione che restituira' un risultato ogni volta che verra' chiamata con parametri appropriati.
- Se l'astrazione di funzione include un'espressione `E` da valutare, non ci sono comandi da eseguire. 
	- Tuttavia, molti linguaggi di programmazione hanno dato la possibilita' di inserire comandi all'interno delle funzioni in modo da sfruttare a pieno la potenza computazionale.

**NB: IN ADA LE FUNZIONI SONO CITTADINI DI TERZA CLASSE, OVVERO POSSONO ESSERE SOLO CHIAMATE, MENTRE IN ALTRI SONO DI SECONDA (es. PASCAL), IN ALTRI ANCORA SONO DI PRIMA CLASSE.**

## **Astrazione di procedura**
Un'astrazione di procedura include un **comando da eseguire** e, quando chiamata, **aggiornera' le variabili che rappresentano lo stato del sistema**.
E' definita come:
```
procedure I(FP1;...;FPn) is C
```
dove `C` e' il **blocco di comandi** da eseguire.

In questo modo si lega `I` all'astrazione di procedura che cambiera' lo stato del sistema ogni volta che verra' chiamata con parametri appropriati.

**NB: IN ADA LE PROCEDURE SONO CITTADINI DI PRIMA CLASSE, OVVERO NON HANNO RESTRIZIONI SULL'UTILIZZO PERCHE' POSSONO ESSERE USATE COME VARIABILI, MENTRE IN ALTRI LINGUAGGI (es. PASCAL, C) SONO CITTADINI DI SECONDA CLASSE**.

> La decisione su quale sia la tecnica migliore da usare tra l'astrazione di *funzione* o *procedura* dipende dal **tipo di operatore progettato** e dai **limiti del linguaggio** di programmazione.

## **Astrazione di controllo**
Un'astrazione di controllo include delle **espressioni di ordine di esecuzione** delle istruzioni.
- Il **linguaggio macchina** mette a disposizione del programma costrutti banali come l'**elaborazione in sequenza** e il **salto**.
	- Il salto e' rappresentato mediante l'istruzione `jump to <indirizzo simbolico o label>`
		- Quest'ultimo e' di scarsa importanza per il programmatore, perche' la cosa importante e' riuscire a indicare le prossime istruzioni da eseguire. Questo e' il motivo per cui i linguaggi di programmazione ad alto livello hanno introdotto strutture di controllo.
- I **linguaggi ad alto livello** hanno introdotto strutture come la **selezione**, l'**iterazione** e chiamate **ricorsive** (*tramite l'utilizzo dello stack*).
	- L'attuale tendenza porta a offrire strutture di controllo iterative per dati che sono collezioni omogenee di valori.

La struttura di controllo iterativa ha due parametri, il **dato astratto** e una variabile alla quale assegnarne il contenuto. Il meccanismo di visita e' incapsulato come operazione lecita all'interno del dato astratto.
> esempio: 
> - `for-each`
> - `iterator()`

E' definita come:
```
control I(FP1; FPn) is S
```
dove `S` e' l'**espressione di controllo** che definisce l'ordine di esecuzione delle istruzioni

