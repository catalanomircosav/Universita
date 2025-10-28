## **Introduzione al paradigma OO**
La programmazione orientata agli oggetti (OOP, *Object-Oriented Programming*) nasce come evoluzione naturale della programmazione imperativa.
- Nella programmazione imperativa classica (come nel `C`), il programma è una sequenza di istruzioni che modificano lo stato globale del sistema. Le variabili e le funzioni esistono, ma non sono “legate” fra loro in modo organico: il programmatore deve gestire manualmente la coerenza dei dati e la loro visibilità.

- Con il paradigma OO, tutto cambia:
	- Gli **oggetti diventano il centro della progettazione**.
	- Il software viene visto come una rete di entità autonome che collaborano, ognuna con il proprio stato interno e un insieme di operazioni (metodi) che ne definiscono il comportamento.
	- L’attenzione passa da “cosa deve fare il programma” a “chi fa cosa”.

## **Principi fondanti**
### **Incapsulamento**
L’incapsulamento è il cuore del paradigma OO. Significa racchiudere **stato e comportamento** in un’unica entità.  
Gli oggetti sono come “scatole nere”: espongono solo ciò che serve (*metodi pubblici*) e nascondono i dettagli interni (*variabili private*).  
Questo riduce le dipendenze tra le parti del programma e protegge l’integrità dei dati.
### **Information Hiding**
È strettamente legato all’incapsulamento. Consiste nel nascondere le informazioni interne di un oggetto, mostrando solo ciò che è necessario all’esterno.  
In pratica, un modulo o una classe dichiara **un’interfaccia pubblica** che stabilisce come interagire con essa, ma **non come** le operazioni vengono realizzate.  
Questo riduce gli errori, favorisce la manutenzione e permette di modificare l’implementazione senza influire sul resto del sistema.
### **Conseguenze progettuali**
- La complessità viene gestita **per astrazione**: ogni oggetto si occupa di un solo sottoinsieme del problema.  
- I sistemi diventano **modulari e scalabili**, perché si possono aggiungere o modificare classi senza riscrivere l’intero programma.
- Le relazioni tra oggetti (ereditarietà, composizione, aggregazione) permettono di costruire modelli complessi partendo da concetti semplici e riutilizzabili.
___
## **Gli Oggetti**
Un **oggetto** è un’entità software che combina tre aspetti fondamentali:
1. **Stato** – rappresenta le informazioni o i dati che descrivono la condizione dell’oggetto in un dato momento.
2. **Comportamento** – definisce le azioni che l’oggetto può compiere o subire, solitamente implementate tramite metodi.
3. **Identità** – ogni oggetto è distinto da tutti gli altri, anche se due oggetti hanno lo stesso stato.

L’identità di un oggetto è ciò che lo distingue da tutti gli altri, anche quando lo stato è identico.  
Nei linguaggi OO, questa identità è rappresentata da un **Object Identifier (OID)** o **riferimento**, spesso coincidente con l’indirizzo di memoria.
- L’OID è **immutabile**: non cambia nel tempo, a differenza dello stato.  
- Due variabili possono riferirsi allo stesso oggetto → si parla di **alias**.  
- La presenza di alias non toglie unicità: significa solo che più nomi puntano alla stessa entità.
### **Oggetti e relazioni**
Gli oggetti raramente esistono in isolamento.  
Spesso **contengono riferimenti ad altri oggetti**, stabilendo relazioni complesse:
- Un **oggetto A** può “puntare” a un **oggetto B**, ossia mantenere un riferimento a esso.
- Questa relazione è **asimmetrica**: se A punta a B, non è detto che B punti ad A.
- La simmetria (reciprocità) deve essere esplicitamente progettata, ad esempio per mantenere coerenza bidirezionale (come tra “Docente” e “Corso”).

Queste relazioni costituiscono la base per la modellazione concettuale dei sistemi e saranno espresse in `UML` tramite **associazioni**, **aggregazioni** e **composizioni**.

| Concetto           | Significato                                                      | Implicazione pratica                                                          |
| ------------------ | ---------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Stato**          | Informazioni che definiscono la condizione attuale dell’oggetto. | Gli attributi cambiano nel tempo e rappresentano il “contenuto” dell’oggetto. |
| **Comportamento**  | Le azioni che l’oggetto può eseguire.                            | I metodi implementano la logica operativa e l’interazione con altri oggetti.  |
| **Identità (OID)** | Riconoscimento univoco dell’oggetto.                             | Permette di distinguere due oggetti anche se hanno lo stesso stato.           |
| **Alias**          | Più riferimenti che puntano allo stesso oggetto.                 | Possono generare effetti collaterali se non gestiti correttamente.            |
| **Relazioni**      | Collegamenti logici fra oggetti.                                 | Permettono di costruire modelli complessi e interdipendenti.                  |
___
## **UML**
**UML (Unified Modelling Language)** è un linguaggio visuale per definire, progettare, realizzare e documentare sistemi orientati agli oggetti.

### **Oggetti in UML**
In UML puoi disegnare un’**istanza** di oggetto indicando:
- solo il **nome dell’istanza**,
- nome dell’istanza **e** della **classe** (`oggetto:classe`),
- solo la **classe** (`:classe`)
- perfino un’**istanza orfana** se la classe non è nota.

### **Classi in UML**
Una **classe** descrive una famiglia di oggetti con **struttura** (attributi) e **comportamento** (operazioni). In UML è un rettangolo con fino a tre sezioni: **nome**, **attributi**, **operazioni**.

**Operazioni vs metodi.** UML distingue il **servizio dichiarato** (operazione) dalla **sua implementazione** (metodo). Nel modello ti interessa la **firma** e le **proprietà**, non il codice.

### **Visibilità e molteplicità**
Gli attributi e i metodi di una classe possono avere diversi livelli di visibilità. Un elemento (attributo o metodo) ha visibilità:
- **pubblica**: quando può essere visto (utilizzato, invocato) da altre classi,
- **privata**: quando può essere visto solo dalla classe di appartenenza,
- **protected**: quando puo' essere visto solo all'interno del package e ai discendenti,
- **package**: quando puo' essere visto solo all'interno del package.

`+` **public**, `#` **protected**, `-` **private**, `~` **package**.  
Usala per comunicare **contratti** e **incapsulamento**, non per ribadire tutto il design del linguaggio. Mantieni il diagramma focalizzato su cosa è **pubblico** per i clienti della classe.
![[Pasted image 20251028105645.png]]
**Molteplicità**:
- **di classe**: quante istanze possono esistere (es. `1` per un **Singleton**; utile per vincoli architetturali).
![[Pasted image 20251028105603.png]]
- **di attributo**: quante istanze di un tipo collego a un oggetto (es. `porte[2..*]:Port`).  
    Ricordati che indicare la molteplicità negli attributi chiarisce subito **cardinalità e collezioni** senza dover introdurre per forza un’associazione separata.
![[Pasted image 20251028105611.png]]
**Proprietà degli attributi** (quando serve rigore): `changeable` (*senza restrizioni*), `addOnly` (*valori che non possono essere rimossi*), `frozen` (*valore non modificabili)*. Sono preziose per vincoli d’invarianza (es. ID immutabili).
### **Operazioni “con proprietà” e classi attive**
Nei sistemi concorrenti compaiono le **classi attive** (bordo raddoppiato): le loro istanze hanno **thread** proprio. Usale solo quando la **concorrenza** è parte dell’astrazione del dominio.
![[Pasted image 20251028105539.png]]
### **Classe Template**
Una **classe template** definisce una famiglia di classi parametrizzate per tipo (in Java: **generics**). In UML indichi il **parametro di tipo** (es. `ArrayList<E>`).
![[Pasted image 20251028105519.png]]
## 5. Ereditarietà
L’**ereditarietà** è una relazione tra classi che permette di definire una nuova classe (“sottoclasse”) a partire da un’altra (“superclasse”), **riusando** struttura e comportamento e **specializzandoli** dove serve:
- **Ereditarietà per estensione**: La sottoclasse **aggiunge** attributi e/o metodi non presenti nella superclasse. La visibilità degli elementi ereditati **non cambia** (public/protected/private restano tali).
![[Pasted image 20251028110610.png]]
- **Ereditarietà per variazione funzionale**: La sottoclasse **ridefinisce** (override) l’implementazione di un metodo, a **segnatura invariata**. Attenzione: l’override **non è incrementale** — se cambi la regola nella superclasse, **non** si propaga automaticamente alle override; devi aggiornare anche le sottoclassi, altrimenti introduci discrepanze.
![[Screenshot 2025-10-28 110624.png]]
- **Ereditarietà di implementazione***: La sottoclasse **riutilizza il codice** (rappresentazione e metodi) della superclasse per realizzare **un’altra astrazione** con **interfaccia diversa**. Qui si può anche **modificare la visibilità** degli elementi ereditati. **Non** rispetta Liskov/sostituibilità.
![[Pasted image 20251028110806.png]]

#### **Sostituibilità (Liskov) e relazione “is-a”**: 
Il **principio di sostituibilità** (LSP) dice: se un punto del codice vuole un `X`, deve poter ricevere **qualsiasi** istanza di una **sottoclasse di X** senza rompere il comportamento atteso.

### **Struttura della gerarchia: proprietà e risoluzione dei metodi**

- **Proprietà del grafo di ereditarietà**
Le generalizzazioni tra classi formano un **DAG** (grafo orientato aciclico), **transitivo** e **antisimmetrico**: puoi risalire ai **progenitori** (superclassi) o scendere verso i **discendenti** (sottoclassi). Ogni classe ha il proprio grafo di ereditarietà `G(C)` focalizzato sulle sue superclassi.

- **Ereditarietà singola — risoluzione dell’override**
Con una sola superclasse diretta, la risoluzione del metodo è lineare: si considera la **catena** delle superclassi e si prende la **prima** (procedendo dalla sottoclasse verso l’alto) che **definisce/ridefinisce** il metodo. Questo chiarisce quale codice verrà eseguito in caso di overriding.

- **Ereditarietà multipla — cosa succede e perché è difficile**
Con più superclassi dirette, `G(C)` **non è più un albero**. Due problemi tipici:

1. **Conflitto di metodi** con lo stesso nome: una linearizzazione dell’ordine (più d’una possibile) decide da quale superclasse “vince” l’implementazione (quella **più specifica** nella linearizzazione scelta).

2. **Ambiguità reali**: quando la linearizzazione non basta a decidere, servono **criteri euristici**, ad esempio:
    - **Ordine dichiarativo** delle superclassi (la molteplicità di ereditarietà),
    - **Modularità**: evitare di mescolare sottografi concettualmente separati (diversi “punti di vista” sullo stesso oggetto).  
        Queste difficoltà spiegano perché molti sconsigliano l’ereditarietà multipla per le classi concrete: i **benefici sono pochi** rispetto alla complessità semantica che introduce.


## 6. Interfacce
Un’**interfaccia** specifica **quali operazioni** un tipo espone, non **come** le realizza. A differenza di una classe, in UML l’interfaccia non definisce stato (se non eventuali costanti statiche) e non fornisce implementazioni; è concettualmente simile a una **classe astratta con soli metodi astratti**.
![[Pasted image 20251028111924.png]]
La relazione tra **classe** e **interfaccia** è la **realizzazione** (freccia tratteggiata): l’interfaccia esprime **il contratto** (_cosa_), la classe fornisce **l’implementazione** (_come_)
![[Pasted image 20251028111944.png]]
## 7. Aggregazione e Composizione
- **Aggregazione:** relazione “has_a” debole tra oggetti (le parti possono esistere senza l’intero).  
- **Composizione:** relazione forte (dipendenza esistenziale).  
- Notazioni UML (rombo vuoto/pieno).  
- Differenze concettuali e pratiche con l’ereditarietà.

## 8. Ereditarietà vs Aggregazione
- Differenze semantiche e di progetto tra “is_a” e “has_a”.  
- Scelte progettuali e implicazioni sul riuso del codice e sul polimorfismo.

## 9. Organizzazione del modello
- **Package:** raggruppamento logico di classi e interfacce.  
- Visibilità pubblica e privata tra package.  
- Importazione, annidamento e namespace qualificati.  
- **Classi interne:** relazioni tra classe ospitante e inner class.

## 10. Polimorfismo
- Capacità di un’operazione di assumere forme diverse.  
- Classificazione (Cardelli & Wegner):  
  - **Polimorfismo universale:** parametrico e per inclusione.  
  - **Polimorfismo ad hoc:** overloading e coercizione.  
- **Coercizione:** conversione automatica di tipi.  
- **Overloading:** stesso nome per funzioni con comportamenti diversi.  
- **Parametrico:** funzioni o classi generiche (template, generics).  
- **Inclusione:** ereditarietà e sostituibilità.  
- Legame statico e dinamico (binding) e il loro impatto sul polimorfismo.