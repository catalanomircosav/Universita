#map 
___
# **L'astrazione**
L'astrazione e' un processo mediante il quale e' possibile concentrarsi su aspetti rilevanti di un determinato problema, dimenticando gli elementi incidentali.
Essa sottintende:
- **un processo**: l'estrazione delle informazioni **essenziali** e **rilevanti**;
- **una entità**: una descrizione semplificata del sistema che enfatizza alcuni dei dettagli trascurandone altri.

Nella **programmazione**, l'astrazione allude alla distinzione tra **cosa** fa un pezzo di codice e **come** esso e' implementato: per l'utente del codice e' essenziale sapere cosa fa il codice, non come questo codice e' implementato.

L'astrazione e' utile per **padroneggiare la complessità** di problemi complessi, risolvendoli in modo **organizzato** e **gestibile**.

L'efficacia di un'astrazione puo' essere migliorata mediante l'uso di **parametri**: quando un'astrazione e' chiamata, ciascun **parametro formale** viene legato al **parametro effettivo**, associando ogni **parametro effettivo** al corrispondente argomento.
## **Astrazione funzionale**
L'astrazione funzionale e' una tecnica di progettazione del software che prevede di dover specificare i dati di input e output di un **modulo**, nascondendone i dettagli implementativi.
- Il **consumatore** del modulo conosce solo le convenzioni di chiamata (*specifica sintattica*) e cosa fa il modulo (*specifica semantica*) e deve fidarsi del risultato.
	- La **specifica sintattica** indica il nome, i dati di input e il tipo di output del modulo, permettendo cosi la sua corretta chiamata;
	- La **specifica semantica** indica la funzione calcolata, ma non e' nota la sua **realizzazione**.

### **Specifica semantica**
La **specifica semantica** e' espressa tramite due predicati:
- la **precondizione**, che deve essere vera sui dati di input;
- la **postcondizione** che e' vera $\iff$ il primo predicato e' vero e il programma termina sui dati di input.

Un limite molto importante dell'astrazione funzionale e' che **non permette di progettare e sviluppare moduli software invarianti ai cambiamenti nei dati**.

## **Astrazione dati**
Per risolvere il problema dell'astrazione funzionale, si e' introdotta l'**astrazione dati**, che sfrutta il principio dell'*information hiding*, secondo il quale **non si puo' accedere direttamente alla rappresentazione di un dato qualunque esso sia, ma solo attraverso un insieme di operazioni considerate lecite**.

Questo risolve il problema dell'astrazione dati, perche' qualsiasi cambiamento alla rappresentazione **interna** di un dato si ripercuote solo sulle operazioni lecite e non sul codice che usa il dato astratto.

### **Incapsulamento**
L'incapsulamento e' una tecnica di progettazione che consiste nell'impacchettare una collezione di entita', creando una barriera concettuale. I pacchetti potranno quindi essere:
- **trasparenti**: il contenuto **non e' nascosto** all'esterno del pacchetto;
- **traslucidi**: il contenuto e' **parzialmente nascosto** all'esterno del pacchetto;
- **opachi**: il contenuto e' **completamente nascosto** all'esterno del pacchetto.

L'astrazione dati, combinata con l'**incapsulamento**, permette di:
- **nascondere la rappresentazione di un dato**, il cui accesso deve passare solo attraverso operazioni lecite;
- **impacchettare le operazioni lecite insieme al dato astratto** stesso.

L'**astrazione dati** permette di estendere l'**astrazione funzionale**, poiche' si passa da una progettazione ***function centered*** a una ***data centered***.
___
## **Specifica**
Per descrivere una specifica occorre ricorrere a dei **linguaggi di specifica**, che sono diversi dai linguaggi usati per descrivere le astrazioni.
Una specifica di divide in:
- **specifica sintattica**: stabilisce gli identificatori (nomi) associati all'astrazione.
- **specifica semantica**: definisce il risultato della computazione dell'astrazione.