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