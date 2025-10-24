L’astrazione è il meccanismo concettuale che permette di descrivere _che cosa fa_ una computazione, senza specificare _come è realizzata al suo interno_. 
In questo modo il programmatore può ragionare su entità complesse utilizzando nomi e modelli semplici, delegando i dettagli a livelli inferiori.
Poiché in un linguaggio di programmazione esistono diverse forme di computazione, esistono anche diverse forme di astrazione. Le sei forme fondamentali sono:

| Astrazione | Oggetto astratto | Output concettuale            |
| ---------- | ---------------- | ----------------------------- |
| Funzione   | espressione      | valore                        |
| Procedura  | comando          | nuovo stato del sistema       |
| Controllo  | sequenza         | ordine di esecuzione          |
| Selettore  | accesso          | L-value                       |
| Tipo       | dato             | rappresentazione + operazioni |
| Generica   | dichiarazione    | nuove dichiarazioni           |
Ognuna di esse nasce per generalizzare un aspetto diverso dell’attività del calcolo.
___

## **Astrazione di funzione**
Una funzione è un’astrazione costruita su un’espressione, e serve a definire un calcolo che produce un valore. Una volta definita, la funzione può essere invocata fornendo opportuni argomenti, e la sua esecuzione restituisce un risultato.
L’idea centrale è che la funzione sia _osservativa_: si limita a calcolare e restituire un valore, senza modificare lo stato del programma. Questa visione la assimila ai calcoli matematici, dove il valore dipende solo dai parametri forniti.

> **SINTESI: la funzione astrae un _valore prodotto da un calcolo_** ed è rappresentata come:
> `function I(FP1;...;FPn) is E` 

## **Astrazione di procedura**
La procedura è l’astrazione costruita su un comando, e rappresenta un’azione che modifica lo stato del sistema. A differenza della funzione, la procedura non restituisce un valore, ma ha lo scopo di produrre un effetto.
Le procedure sono quindi _trasformazionali_: agiscono sullo stato del programma, per esempio aggiornando variabili, strutture dati o risorse esterne.

> **SINTESI: la procedura astrae una trasformazione del sistema** ed è rappresentata come:
> `procedure I(FP1;...;FPn) is C`

## **Astrazione di controllo**
L’astrazione di controllo interviene sull’ordine con cui vengono eseguite le operazioni. A livello più basso, il calcolatore esegue istruzioni in sequenza o tramite salti. Le astrazioni di controllo nascondono questo meccanismo grezzo, introducendo costrutti più espressivi come selezione, iterazione e ricorsione.
Costrutti quali `if`, `for`, `while` e la chiamata ricorsiva permettono di esprimere la logica del controllo in modo dichiarativo, senza fare riferimento a salti o indirizzi.

> **SINTESI: permette di definire quando e quante volte un'azione deve essere eseguita** ed è rappresentata come:
> `control I(FP1;...;FPn) is S`

## **Astrazione di selettore**
Il selettore è un’astrazione sull’accesso alla memoria: il suo ruolo non è restituire un valore, ma restituire un **access path**, cioè un riferimento a una componente del dato, che può essere letta o modificata.
Quando si accede a `x.campo` o `v[i]`, ciò che si ottiene non è semplicemente un valore, ma un _L-value_, una posizione di memoria che può essere assegnata. Il selettore rende quindi possibile un accesso controllato e strutturato alle parti di uno stato complesso.

> **SINTESI: il selettore astrae il modo in cui si raggiunge e si modifica una parte dei dati** ed è rappresentata come:
> `selector I(FP1;...;FPn) is A`

## **Astrazione di tipo**
L’astrazione di tipo permette di introdurre nuovi tipi di dato, definendo:
- quali valori appartengono al tipo,
- quali operazioni è lecito applicare,
- come il tipo viene rappresentato internamente.
Un tipo ben progettato nasconde la propria rappresentazione interna e offre un insieme controllato di operazioni. Questo garantisce coerenza, sicurezza e possibilità di evolvere l’implementazione senza modificare il codice che utilizza il tipo.
Un tipo astratto si descrive attraverso tre categorie di operazioni:
- **costruttori**, che creano valori del tipo
- **osservatori**, che ne estraggono informazioni
- **mutatori**, che ne modificano lo stato (quando previsto)

> **Un efficace meccanismo di astrazione di tipo richiede incapsulamento: chi usa il tipo deve vedere _cosa può fare_, non _com’è fatto_**. Rappresentata come:
> `type I(FP1;...;FPn) is T`

## **Astrazione generica**
L’astrazione generica non produce dati o effetti, ma **produce dichiarazioni**. È un’astrazione a livello sintattico, che permette di definire costrutti parametrici (per esempio tipi o moduli generici) e di ottenere versioni concrete specializzate fornendo parametri al momento dell’istanziazione.

>  È un’astrazione _meta_, perché opera sul codice anziché sull’esecuzione: non calcola, ma _genera nuovo codice coerente e riutilizzabile_. Rappresentata come:
>  `generic I(FP1;...;FPn) is D`
