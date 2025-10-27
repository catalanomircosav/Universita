# Il Paradigma Orientato agli Oggetti

## 1. Introduzione al paradigma OO
- Origini e differenze rispetto al paradigma imperativo.  
- Concetti base: oggetti come cittadini di prima classe, incapsulamento e information hiding.  
- OO come evoluzione e rivoluzione nella progettazione del software.

## 2. Gli Oggetti
- Ogni oggetto ha **stato**, **comportamento** e **identità (OID)**.  
- Stato: valori dei suoi attributi.  
- Comportamento: metodi che operano sullo stato.  
- Identità: riconoscibilità unica, indipendente dallo stato.

## 3. UML e rappresentazione degli oggetti
- UML come linguaggio standard per modellare sistemi OO.  
- Rappresentazione grafica di oggetti e istanze.  
- Stato, attributi e metodi nelle classi UML.

## 4. Le Classi
- Descrizione di famiglie di oggetti con struttura e comportamento comuni.  
- Componenti statiche (attributi) e dinamiche (metodi).  
- Tipi di metodi: costruttori, accessori, trasformatori, distruttori.  
- Visibilità (public, private, protected, package).  
- Attributi statici e derivati, stereotipi UML.  
- Molteplicità di classi e attributi.  
- Proprietà di attributi e operazioni (changeable, frozen, ecc.).  
- Classi attive e template (generiche).

## 5. Ereditarietà
- Relazione fra classi per riuso e specializzazione.  
- Forme di ereditarietà:
  - **Per estensione:** aggiunge nuovi attributi/metodi.  
  - **Per variazione funzionale:** ridefinisce metodi (overriding).  
  - **Di implementazione:** riuso del codice, non compatibile col polimorfismo.  
- Ereditarietà singola e multipla: vantaggi e conflitti.  
- Principio di sostituibilità (Liskov).  
- Proprietà della generalizzazione (transitività, antisimmetria).  
- Classi astratte, finali e polimorfiche.

## 6. Interfacce
- Descrizione del comportamento di una classe senza implementazione.  
- Relazione di realizzazione tra classe e interfaccia.  
- Ereditarietà fra interfacce e implementazioni multiple.  
- Interfacce come strumento di disaccoppiamento (contratto “cosa vs come”).

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