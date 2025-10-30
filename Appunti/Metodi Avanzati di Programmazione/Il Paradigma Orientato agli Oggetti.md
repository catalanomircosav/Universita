# **Cosa è il Paradigma Orientato agli Oggetti**
Il paradigma orientato agli oggetti è un paradigma che permette di definire **oggetti** in grado di interagire gli uni con gli altri attraverso lo scambio di messaggi (*per scambio di messaggi si intende la capacità degli oggetti di richiamare **metodi** pubblici di altri oggetti*).
## **Classi**
Una **classe** permette di definire tipi di dati e permettono la creazione di **oggetti** secondo caratteristiche definite nella classe stessa, che quindi saranno comuni a tutti gli oggetti di quella classe. Grazie poi alle relazioni di ereditarietà, è possibile creare **sotto-classi** a partire da quelle esistenti, estendendole con caratteristiche aggiuntive.

Una classe è composta da:
- un insieme di **attributi**, ossia *variabili*/*costanti* che definiscono le caratteristiche degli oggetti di quella classe.
- un insieme di **metodi**, ossia *procedure* che operano sugli attributi.

![](../../resources/map/UML/UML%20-%20Classe.png)
### **Oggetti**
Un oggetto e' una istanza di una classe. Esso e' dotato di tutti gli attributi e metodi definiti dalla classe e agisce come un *fornitore* di "*messaggi*", che il codice eseguibile del programma può attivare su richiesta. Inviare un messaggio significa invocare un metodo su quell'oggetto.
Ogni oggetto ha una sua **identità**, rappresentata da un **identificatore di oggetto (*OID*)**, che lo identifica univocamente e nella maggior parte dei casi e' rappresentato dal primo indirizzo di memoria su cui risiede l'oggetto.

![gay](../../resources/map/UML/UML%20-%20Istanza.png)
### **Attributi**
Gli **attributi** si distinguono in base al loro *scope* (ambito d'azione):
- **attributi d'istanza**: sono associati a un oggetto e hanno vita pari a quella dell'oggetto;
- **attributi di classe**: sono associati alla classe e condivisi tra tutti gli oggetti di quella classe.

![](../../resources/map/UML/UML%20-%20Attributo.png)
### **Metodi**
Anche i metodi si distinguono in base al loro scope:
- **metodi di istanza**: operano su un attributo dell'oggetto, pertanto devono essere invocati solo specificando l'oggetto.
- **metodi di classe**: operano sugli attributi condivisi tra gli oggetti, pertanto possono essere specificati **anche** solo specificando la classe, e non l'oggetto.

I **metodi** possono essere ulteriormente classificati in:
- **metodi costruttori**: invocati per creare gli oggetti e inizializzare gli attributi.
- **metodi di accesso**: restituiscono gli attributi dell'oggetto in forma di informazione.
- **metodi di trasformazione**: modificano gli attributi dell'oggetto.
- **metodi distruttori**: invocati per distruggere (e quindi *rimuovere dalla memoria*) un oggetto.

![](../../resources/map/UML/UML%20-%20Metodi.png)
### **Visibilità e Molteplicità'**
Gli attributi e i metodi di una classe possono avere diversi livelli di visibilità:
- **attributo / metodo pubblico** (`+`): quando può essere **visto** (*utilizzato, invocato, modificato, ecc.*) anche da altre classi;
- **attributo / metodo protetto** (`#`): quando può essere **visto** solo dalle sue **sotto-classi** e da classi visibili all'interno dello stesso ***package***.
- **attributo / metodo package** (`~`): quando può essere visto solo agli elementi dello stesso ***package***.
- **attributo / metodo privato** (`-`): quando non può essere visto all'esterno della classe.

Con il termine ***molteplicità di classe*** si intende il numero di oggetti che possono essere del tipo di classe. Generalmente non vi è imposto un limite, tuttavia si possono distinguere:
- **classi singleton (*singoletto*)**: classi con molteplicità `1`, ovvero classi che non permettono di avere più di un oggetto istanziato.
- **classi con molteplicità $n$**: classi che possono avere esattamente $n$ oggetti contemporaneamente.

![](../../resources/map/UML/UML%20-%20Molteplicita'.png)

Con il termine di **molteplicità di attributo** si indica il numero massimo di attributi di un determinato tipo che una classe può avere.

![](../../resources/map/UML/UML%20-%20Molteplicita%20di%20attributi.png)
### **Classi attive**
Una classe si attiva quando gli oggetti di quella classe sono attivi. Un oggetto si dice **attivo** quando esso ha un thread e può far partire un thread concorrente. Una classe attiva è simile ad una classe classica con l'eccezione che le sue istanze rappresentano elementi il cui comportamento è concorrente con gli altri.

![](../../resources/map/UML/UML%20-%20Classe%20Attiva.png)
### **Classi template**
Una classe template definisce una **famiglia di classi parametrizzate**. Una classe di questo tipo non è utilizzabile direttamente, ma va prima specificato il tipo. (`generic` in **Java**)

![](../../resources/map/UML/UML%20-%20Classe%20Template.png)
### **Classi astratte**
Una classe astratta e' una classe non completamente specificata, vale a dire che almeno un metodo di quella classe non ha specificato l'implementazione, ma solo la firma. Per questo motivo, una classe astratta non può essere istanziata.

![](../../resources/map/UML/UML%20-%20Classe%20Astratta.png)
#### **Interfacce**
Una interfaccia è la descrizione del comportamento degli oggetti senza specificare alcuna implementazione. E' una collezione di operazioni, ovvero di servizi che possono essere richiesti.
- Similmente ad una classe, può avere un numero qualsiasi di operazioni;
- Diversamente da una classe, non specifica né la struttura né l'implementazione dei metodi.

**Simile ad una classe astratta in cui i metodi sono tutti astratti e non dispone di attributi**.

Poiché non possono sorgere conflitti tra interfacce, a una classe è permesso di realizzare più interfacce.
Infine, più classi possono implementare la stessa interfaccia.

![](../../resources/map/UML/UML%20-%20Interfaccia.png)
### **Classi finali**
Una classe finale è una classe che non può essere ulteriormente specializzata. Si definisce una classe di questo tipo quando il comportamento della classe stessa deve essere ben stabilito per ragioni di **affidabilità**.

![](../../resources/map/UML/UML%20-%20Classe%20Finale.png)
### **Classi interne**
Una classe interna è una classe la cui dichiarazione si trova all'interno di un'altra classe ospite.
- Una classe di questo tipo non può essere privata.
- Può accedere a tutti i metodi e i campi della classe ospitante, mentre la classe ospitante può vedere solo la parte pubblica della *inner class*.
- Un oggetto di una classe inner non può esistere se non esiste un oggetto della classe ospitante. 
- Non può avere campi statici.

![](../../resources/map/UML/UML%20-%20Classe%20Interna.png)

### **Ereditarietà**
Il meccanismo dell'ereditarietà permette di definire una nuova classe (_sottoclasse_) a partire da una classe esistente (_superclasse_), ereditandone attributi e metodi. Permette di riutilizzare il codice e specializzare comportamenti.

- **Principio di sostituibilità di Liskov** Il principio di sostituibilità di Liskov stabilisce che un tipo `S` è un sottotipo di `T` quando è possibile sostituire tutti gli oggetti di `T` con gli oggetti di `S`, mantenendo intatto il funzionamento del programma.

Il meccanismo si può suddividere in tre tipi:
- **ereditarietà per estensione**: la sottoclasse aggiunge nuovi attributi e metodi, ereditando tutti quelli della superclasse. _Questo meccanismo è compatibile con il principio di sostituibilità di Liskov_.

  ![](../../resources/map/UML/UML%20-%20Generalizzazione.png)

- **ereditarietà per variazione funzionale**: la sottoclasse ridefinisce (effettua l'_overriding_) di alcuni metodi ereditati dalla superclasse. _Anche questo tipo è compatibile con il principio di sostituibilità di Liskov.

  ![](../../resources/map/UML/UML%20-%20Ereditarieta'%20funzionale.png)

- **ereditarietà per implementazione**: la sottoclasse riutilizza l'implementazione della superclasse ma non ne condivide l'interfaccia pubblica. _Permettendo quindi un **riuso** solo **parziale** del codice questo terzo tipo non è compatibile con il principio di sostituibilità di Liskov._

  ![](../../resources/map/UML/UML%20-%20implementation%20Inheritance.png)

Inoltre, anche l'ereditarietà permette di definire una molteplicità:
- **ereditarietà singola**: Il grafo di ereditarietà è in realtà un albero in cui ogni classe ha una sola superclasse diretta.
    - Quando una classe eredita un metodo da più livelli di superclassi, **la versione più vicina** (cioè quella definita nella prima superclasse che la ridefinisce) è quella effettivamente ereditata.

- **ereditarietà multipla**: Il grafo di ereditarietà non è più un albero ma un grafo aciclico orientato.
    - In caso di ereditarietà multipla, se più superclassi definiscono lo stesso metodo, si sceglie la versione della **classe più vicina** nella linearizzazione del grafo. **Tutte le altre versioni vengono ignorate (shadowing).**
    
      ![](../../resources/map/UML/UML%20-%20Ereditarieta'%20Multipla.png)

La relazione di ereditarietà corrisponde a una relazione di **generalizzazione tra classi (_is_a_)**. Ciò perché ogni istanza della sottoclasse va considerata come una istanza della superclasse.

### **Polimorfismo**
Il **polimorfismo** è la capacità di associare a un’unica operazione o metodo **diverse implementazioni**, a seconda del **tipo dell’oggetto** o dei **parametri** su cui agisce.  
Consente di scrivere codice più flessibile e riutilizzabile, in cui le stesse istruzioni possono operare su oggetti di tipi differenti.

Il polimorfismo può essere classificato in diversi modi:

- **polimorfismo parametrico**: si ha **polimorfismo parametrico** quando una funzione o classe lavora in modo uniforme su più tipi di dati, purché questi rispettino una struttura comune. È tipico delle funzioni o classi **template** in C++ o **generiche** in Java.
    
- **polimorfismo per inclusione**: Si ha **polimorfismo per inclusione** quando un oggetto di una sottoclasse può essere usato ovunque sia previsto un oggetto della superclasse. (_principio di sostituibilità di Liskov_).
    
    - Il **binding** (o _legame_) indica il momento in cui viene stabilito **quale implementazione** di un metodo sarà eseguita.
        - **Binding statico** → avviene **a compile-time**: L’associazione tra nome del metodo e implementazione è determinata dal **tipo statico** (dichiarato) dell’oggetto.
        - **Binding dinamico** → avviene **a run-time**: L’associazione dipende dal **tipo reale dell’oggetto** (cioè dalla classe effettiva dell’istanza).
        
    - Il **binding dinamico** è ciò che rende possibile il polimorfismo di inclusione: il metodo corretto viene scelto al momento dell’esecuzione, in base alla classe concreta dell’oggetto.
        
- **polimorfismo ad hoc**: si ha **polimorfismo ad hoc** quando una funzione o metodo lavora su tipi diversi, ma in modi potenzialmente non correlati. Si suddivide in due forme principali:
    
    - **overloading**: Si usa lo stesso nome per più metodi che differiscono per tipo o numero di parametri. La scelta del metodo corretto avviene **a compile-time**.
    - **coercizione**: È un meccanismo che converte automaticamente un tipo in un altro compatibile per applicare un’operazione.

## **Relazioni UML**
Nel paradigma orientato agli oggetti, le **relazioni** descrivono come le **classi** e gli **oggetti** interagiscono e sono legati tra loro.
### **Relazione `instance-of`**
La relazione **`instance-of`** lega un **oggetto concreto** alla **classe di cui è istanza**.  
In altre parole, afferma che:
> “Questo oggetto è un’istanza di quella classe”.

In UML può essere rappresentata in due modi:
- **forma esplicita**: Lo stereotipo `<<instanceOf>>` viene utilizzato per indicare la relazione diretta tra oggetto e classe.
- **forma abbreviata**: Il nome dell'oggetto è seguito dai due punti e dal nome della classe.

Questa relazione è asimmetrica, poiché un oggetto è istanza di una classe, ma una classe non è istanza di un oggetto.
### **Relazione `is_a`**
La relazione `is_a` esprime un legame di generalizzazione fra due classi. Indica che una **sottoclasse** (_classe specializzata_) eredita attributi e comportamenti da una **superclasse** (_classe generalizzata_).
> Se `B is_a A`, allora ogni istanza di `B` è anche un’istanza di `A`.

In UML si rappresenta con una **freccia con triangolo vuoto** che punta verso la superclasse. (vedi sopra)

**Caratteristiche principali**:
- È una relazione **asimmetrica** e **transitiva**.
- È alla base del **principio di sostituibilità di Liskov**, secondo cui una sottoclasse può essere utilizzata ovunque sia previsto un oggetto della superclasse.
- Consente il **polimorfismo di inclusione**, in cui la stessa operazione può comportarsi in modo diverso a seconda della classe concreta dell’oggetto.
### **Relazione `has_a`**
La relazione **`has_a`** rappresenta un legame di **contenimento o appartenenza** fra due classi. Descrive un oggetto che è **composto da** o **contiene** altri oggetti.
> Se `A has_a B`, significa che un oggetto di tipo `A` contiene o utilizza uno o più oggetti di tipo `B`.

Questo tipo di relazione si suddivide in due categorie:

- **aggregazione**: È una relazione **debole di contenimento** (_“parte-tutto”_), in cui le parti **possono esistere indipendentemente** dall’intero.
  In UML si rappresenta con una **linea piena** e un **rombo bianco** dal lato del contenitore.
	- **Caratteristiche**:
		- Le parti hanno **vita propria**.
		- La relazione indica un **collegamento logico o funzionale**, non necessariamente fisico.
		- Si usa per esprimere un legame del tipo “contiene” o “utilizza”.

	![](../../resources/map/UML/UML%20-%20Aggregazione.png)

- **composizione**: È una relazione **forte di contenimento**, in cui le parti **non possono esistere senza l’intero**: la loro vita dipende da quella del contenitore.
  In UML si rappresenta con un **rombo nero** (pieno) accanto al contenitore.
	- **Caratteristiche**:
		- Le parti vengono **create e distrutte insieme** all’intero.
		- Non è ammessa la **condivisione**: un oggetto componente può appartenere a un solo contenitore.
		- Si usa per rappresentare una **dipendenza esistenziale**.

	![](../../resources/map/UML/UML%20-%20Composizione.png)

|Caratteristica|`is_a` (Generalizzazione)|`has_a` (Aggregazione / Composizione)|
|---|---|---|
|Tipo di relazione|Ereditarietà (specializzazione)|Contenimento (parte–tutto)|
|Direzione|Dalla sottoclasse alla superclasse|Dal contenitore alla parte|
|Dipendenza|La sottoclasse dipende dalla superclasse solo concettualmente|Nella composizione, la parte dipende dall’intero anche fisicamente|
|Polimorfismo|Permesso (principio di sostituibilità)|Non applicabile|
|Esempio|`Studente is_a Persona`|`Automobile has_a Motore`|