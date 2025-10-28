#map 
___
# **Cosa e' il Paradigma Orientato agli Oggetti**
Il paradigma orientato agli oggetti e' un paradigma che permette di definire **oggetti** in grado di interagire gli uni con gli altri attraverso lo scambio di messaggi (*per scambio di messaggi si intende la capacita' degli oggetti di richiamare **metodi** pubblici di altri oggetti*).

## **Classi**
Una **classe** permette di definire tipi di dati e permettono la creazione di **oggetti** secondo caratteristiche definite nella classe stessa, che quindi saranno comuni a tutti gli oggetti di quella classe. Grazie poi alle relazioni di ereditarieta', e' possibile creare **sotto-classi** a partire da quelle esistenti, estendendole con caratteristiche aggiuntive.

Una classe e' composta da:
- un insieme di **attributi**, ossia *variabili*/*costanti* che definiscono le caratteristiche degli oggetti di quella classe.
- un insieme di **metodi**, ossia *procedure* che operano sugli attributi.

### **Oggetti**
Un oggetto e' una istanza di una classe. Esso e' dotato di tutti gli attributi e metodi definiti dalla classe e agisce come un *fornitore* di "*messaggi*", che il codice eseguibile del programma puo' attivare su richiesta. Inviare un messaggio significa invocare un metodo su quell'oggetto.
Ogni oggetto ha una sua **identità**, rappresentata da un **identificatore di oggetto (*OID*)**, che lo identifica univocamente e nella maggior parte dei casi e' rappresentato dal primo indirizzo di memoria su cui risiede l'oggetto.

### **Attributi**
Gli **attributi** si distinguono in base al loro *scope* (ambito d'azione):
- **attributi d'istanza**: sono associati a un oggetto e hanno vita pari a quella dell'oggetto;
- **attributi di classe**: sono associati alla classe e condivisi tra tutti gli oggetti di quella classe.
### **Metodi**
Anche i metodi si distinguono in base al loro scope:
- **metodi di istanza**: operano su un attributo dell'oggetto, pertanto devono essere invocati solo specificando l'oggetto.
- **metodi di classe**: operano sugli attributi condivisi tra gli oggetti, pertanto possono essere specificati **anche** solo specificando la classe, e non l'oggetto.

I **metodi** possono essere ulteriormente classificati in:
- **metodi costruttori**: invocati per creare gli oggetti e inizializzare gli attributi.
- **metodi di accesso**: restituiscono gli attributi dell'oggetto in forma di informazione.
- **metodi di trasformazione**: modificano gli attributi dell'oggetto.
- **metodi distruttori**: invocati per distruggere (e quindi *rimuovere dalla memoria*) un oggetto.

### **Visibilita' e Molteplicita'**
Gli attributi e i metodi di una classe possono avere diversi livelli di visibilita':
- **attributo / metodo pubblico**: quando puo' essere **visto** (*utilizzato, invocato, modificato, ecc.*) anche da altre classi;
- **attributo / metodo protetto**: quando puo' essere **visto** solo dalle sue **sotto-classi** e da classi visibili all'interno dello stesso ***package***.
- **attributo / metodo package**: quando puo' essere visto solo agli elementi dello stesso ***package***.
- **attributo / metodo privato**: quando non puo' essere visto all'esterno della classe.

Con il termine ***molteplicita' di classe*** si intende il numero di oggetti che possono essere del tipo di classe. Generalmente non vi e' imposto un limite, tuttavia si possono distinguere:
- **classi singleton (*singoletto*)**: classi con molteplicita' `1`, ovvero classi che non permettono di avere piu' di un oggetto istanziato.
- **classi con molteplicita' $n$**: classi che possono avere esattamente $n$ oggetti contemporaneamente.

Con il termine di **molteplicita' di attributo** si indica il numero massimo di attributi di un determinato tipo che una classe puo' avere.

### **Classi attive**
Una classe si attiva quando gli oggetti di quella classe sono attivi. Un oggetto si dice **attivo** quando esso ha un thread e puo' far partire un thread concorrente. Una classe attiva e' simile ad una classe classica con l'eccezione che le sue istanze rappresentano elementi il cui comportamento e' concorrente con gli altri.

### **Classi template**
Una classe template definisce una **famiglia di classi parametrizzate**. Una classe di questo tipo non e' utilizzabile direttamente, ma va prima specificato il tipo. (`generic` in **Java**)

### **Classi astratte**
Una classe astratta e' una classe non completamente specificata, vale a dire che almeno un metodo di quella classe non ha specificato l'implementazione, ma solo la firma. Per questo motivo, una classe astratta non puo' essere istanziata.
#### **Interfacce**
Una interfaccia e' la descrizione del comportamento degli oggetti senza specificare alcuna implementazione. E' una collezione di operazioni, ovvero di servizi che possono essere richiesti.
- Similmente ad una classe, puo' avere un numero qualsiasi di operazioni;
- Diversamente da una classe, non specifica ne' la struttura ne' l'implementazione dei metodi.

**Simile ad una classe astratta in cui i metodi sono tutti astratti e non dispone di attributi**.

Poiche' non possono sorgere conflitti tra interfacce, a una classe e' permesso di realizzare piu' interfacce.
Infine, piu' classi possono implementare la stessa interfaccia.
### **Classi finali**
Una classe finale e' una classe che non puo' essere ulteriormente specializzata. Si definisce una classe di questo tipo quando il comportamento della classe stessa deve essere ben stabilito per ragioni di **affidabilità**.

### **Classi interne**
Una classe interna e' una classe la cui dichiarazione si trova all'interno di un'altra classe ospite.
- Una classe di questo tipo non puo' essere privata.
- Puo' accedere a tutti i metodi e i campi della classe ospitante, mentre la classe ospitante puo' vedere solo la parte pubblica della *inner class*.
- Un oggetto di una classe inner non puo' esistere se non esiste un oggetto della classe ospitante. 
- Non puo' avere campi statici.
____
### **Ereditarietà**
Il meccanismo dell'ereditarietà permette di definire una nuova classe (*sottoclasse*) a partire da una classe esistente (*superclasse*), ereditandone attributi e metodi.
Permette di riutilizzare il codice e specializzare comportamenti.

- **Principio di sostituibilita' di Liskov**
	Il principio di sostituibilita' di Liskov stabilisce che un tipo `S` e' un sottotipo di `T` quando e' possibile sostituire tutti gli oggetti di `T` con gli oggetti di `S`, mantenendo intatto il funzionamento del programma. 

Il meccanismo si puo' suddividere in tre tipi:
- **ereditarieta' per estensione**: la sottoclasse aggiunge nuovi attributi e metodi, ereditando tutti quelli della superclasse. *Questo meccanismo e' compatibile con il principio di sostituibilita' di Liskov.*
- **ereditarieta' per variazione funzionale**: la sottoclasse ridefinisce (effettua l'*overriding*) di alcuni metodi ereditati dalla superclasse. *Anche questo tipo e' compatibile con il principio di sostituibilita' di Liskov.*
- **ereditarieta' per implementazione**: la sottoclasse riutilizza l'implementazione della superclasse ma non ne condivide l'interfaccia pubblica. *Permettendo quindi un **riuso** solo **parziale** del codice questo terzo tipo non e' compatibile con il principio di sostituibilita' di Liskov.*

Inoltre, anche l'ereditarieta' permette di definire una molteplicita':
- **ereditarieta' singola**: Il grafo di ereditarieta' e' in realta' un albero in cui ogni classe ha una sola superclasse diretta.
	- Quando una classe eredita un metodo da più livelli di superclassi, **la versione più vicina** (cioè quella definita nella prima superclasse che la ridefinisce) è quella effettivamente ereditata.

- **ereditarieta' multipla**: Il grafo di ereditarieta' non e' piu' un albero ma un grafo aciclico orientato.
	- In caso di ereditarietà multipla, se più superclassi definiscono lo stesso metodo,   si sceglie la versione della **classe più vicina** nella linearizzazione del grafo. **Tutte le altre versioni vengono ignorate (shadowing).**

La relazione di ereditarieta' corrisponde a una relazione di **generalizzazione tra classi (*is_a*)**. Cio' perche' ogni istanza della sottoclasse va considerata come una istanza della superclasse.

### **Polimorfismo**
Il **polimorfismo** è la capacità di associare a un’unica operazione o metodo **diverse implementazioni**, a seconda del **tipo dell’oggetto** o dei **parametri** su cui agisce.  
Consente di scrivere codice più flessibile e riutilizzabile, in cui le stesse istruzioni possono operare su oggetti di tipi differenti.

Il polimorfismo può essere classificato in diversi modi:
- **polimorfismo parametrico**: si ha **polimorfismo parametrico** quando una funzione o classe lavora in modo uniforme su più tipi di dati, purché questi rispettino una struttura comune. È tipico delle funzioni o classi **template** in C++ o **generiche** in Java.

- **polimorfismo per inclusione**: Si ha **polimorfismo per inclusione** quando un oggetto di una sottoclasse può essere usato ovunque sia previsto un oggetto della superclasse. (*principio di sostituibilita' di Liskov*).
	- Il **binding** (o _legame_) indica il momento in cui viene stabilito **quale implementazione** di un metodo sarà eseguita.
		- **Binding statico** → avviene **a compile-time**: L’associazione tra nome del metodo e implementazione è determinata dal **tipo statico** (dichiarato) dell’oggetto.
		- **Binding dinamico** → avviene **a run-time**: L’associazione dipende dal **tipo reale dell’oggetto** (cioè dalla classe effettiva dell’istanza).
		
	- Il **binding dinamico** è ciò che rende possibile il polimorfismo di inclusione: il metodo corretto viene scelto al momento dell’esecuzione, in base alla classe concreta dell’oggetto.

- **polimorfismo ad hoc**: si ha **polimorfismo ad hoc** quando una funzione o metodo lavora su tipi diversi, ma in modi potenzialmente non correlati. Si suddivide in due forme principali:
	- **overloading**: Si usa lo stesso nome per più mePtodi che differiscono per tipo o numero di parametri. La scelta del metodo corretto avviene **a compile-time**.
	- **coercizione**: È un meccanismo che converte automaticamente un tipo in un altro compatibile per applicare un’operazione.