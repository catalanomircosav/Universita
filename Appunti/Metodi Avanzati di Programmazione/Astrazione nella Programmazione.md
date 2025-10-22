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
