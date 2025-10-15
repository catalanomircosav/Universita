#reti
___
# **Le reti**
Una rete è un'interconnessione di dispositivi in grado di scambiarsi informazioni, quali <u><b>sistemi terminali</b></u>, *router*, *switch* e *modem*.
Un <u><b>sistema terminale</b></u> può essere di due tipi:
- <u>host</u>: macchina di proprietà degli utenti che esegue applicazioni.
- <u>server</u>: computer ad altissime prestazioni che esegue programmi che offrono un servizio a diverse applicazioni utente (es. posta elettronica).
Tutti i dispositivi sono collegati utilizzando mezzi trasmissivi **cablati** o **wireless**.
## **LAN - Local Area Network**
Una <u><b>LAN</b></u> (*rete locale*) è solitamente una rete privata che collega pochi computer (es. ufficio aziendale).
Qualsiasi sistema terminale connesso a una LAN deve essere univocamente identificato tramite un **indirizzo**.
In passato i dispositivi di una LAN veniva collegati tramite un cavo condiviso (*broadcast*): ogni informazione inviata da un sistema terminale ad un altro veniva inviato a tutti gli altri sistemi terminali, anche se non erano i destinatari. I non destinatari poi dovevano rifiutare l'informazione.
Oggi la maggior parte delle reti utilizza uno <u><b>switch</b></u>, ovvero un dispositivo in grado di riconoscere il destinatario e inviare l'informazione solamente a quest'ultimo. Questo meccanismo **riduce il traffico della rete**.
## **WAN - Wide Area Network**
Una <u><b>WAN</b></u> è un'interconnessione di dispositivi in grado di comunicare su scala decisamente più grande rispetto alle **LAN**. Queste ultime infatti hanno un'estensione limitata.
Differenze principali tra LAN e WAN sono:

| **LAN**                                          | **WAN**                                                             |
| ------------------------------------------------ | ------------------------------------------------------------------- |
| estensione molto limitata                        | estensione quasi illimitata                                         |
| connette prevalentemente sistemi terminali       | connette sistemi terminali, switch, modem, router...                |
| di proprietà dell'organizzazione che la utilizza | di proprietà (generalmente) di un ISP (*Internet Service Provider*) |
### **WAN punto - punto**
Una <u><b>WAN punto - punto</b></u> è una rete che collega due dispositivi di comunicazione attraverso un mezzo trasmissivo (wireless o cablato che sia).
### **WAN a commutazione**
Una <u><b>WAN a commutazione</b></u> è una rete con più di due punti di terminazione. In una rete del genere, ci possono essere moltissimi sistemi terminali (ovvero *nodi* in cui la rete può stabilire o cambiare un percorso).
___
# **Commutazione (switching)**
I *sistemi terminali* appartenenti a una **internet** comunicano tramite switch o router che si trovano tra il sistema di partenza e quello di destinazione. In base al metodo che si utilizza, si possono distinguere due tipi di reti:
- <u>rete a commutazione di circuito</u>: Una rete a commutazione di circuito è sempre disponibile tramite un collegamento dedicato chiamato circuito; Lo switch che collega i due dispositivi può abilitare o disabilitare questo circuito. (es. reti telefoniche)
- <u>rete a commutazione di pacchetto</u>: Una rete a commutazione di pacchetto è una rete in cui non esiste un collegamento continuo tra due dispositivi, ma i due comunicano inviandosi pacchetti; gli switch sono in grado di memorizzare i pacchetti (inserirli in una coda) ed elaborarli uno ad uno; questo comporta però problemi di **latenza**.
___
# **Capacità e Prestazioni delle Reti**
Il concetto di *velocita' di rete* e' molto ampio e coinvolge vari fattori che influiscono sulle *performance* di una rete. Nel caso di una **rete a commutazione di pacchetto**, le metriche che ne determinano le prestazioni sono: l'<u><b>ampiezza di banda</b></u>, il <u><b>bit rate</b></u>, <u><b>throughput</b></u> e <u><b>perdita di pacchetti</b></u>.
## **Ampiezza di banda e bit rate**
Con il termine <u><b>ampiezza di banda</b></u> si indicano due concetti leggermente diversi ma comunque correlati:
- Se si intende caratterizzare un sistema trasmissivo, l'ampiezza di banda e' la quantità in *Hz (Hertz)* che indica l'intervallo massimo (in frequenza) che un mezzo fisica consente di trasportare senza danneggiare il segnale in maniera irrecuperabile.
- Se invece si vuole caratterizzare la velocita' di trasmissione, essa viene espressa in bit al secondo (*bps*, *bit per second*) e rappresenta il *transmission rate*, ovvero la quantità di bit al secondo che un certo link garantisce di trasmettere. Il bit rate dipende sia dalla banda che dalla **tecnica di trasmissione**. In generale e' comunque proporzionale alla banda in hertz.
## **Throughput**
Il <u><b>Throughput</b></u> indica quanto velocemente si riescono ad inviare i dati tramite una rete. **Il bit rate e il throughput non sono la stessa cosa**: il primo e' una misura **potenziale** della velocita', il secondo la velocita' **effettiva**.
> [!example] Esempio
> Se il link a un rate di 1Mbps, ma i dispositivi connessi possono gestire al massimo 200kbps, il link non andra' oltre i 200kbps.

La formula per calcolare il **throughput** sarà quindi:
$$\text{Throughput} = min\{T_1, T_2, \dots, T_n\}$$
## **Latenza**
La latenza definisce quanto tempo serve affinché un intero messaggio arrivi completamente a destinazione dal momento in cui il primo bit parte dalla sorgente. Esistono 4 tipi di ritardi:
- <u><b>ritardo di trasmissione</b></u>: il ritardo di trasmissione e' il tempo che ci mette ad arrivare l'ultimo pacchetto rispetto al primo: $\text{ritardo} = \text{(lunghezza del pacchetto)} / \text{(rate)}$
- <u><b>ritardo di propagazione</b></u>: il ritardo di propagazione e' il tempo che serve ad un bit per viaggiare dal punto A al punto B nel mezzo di trasmissione: $\text{ritardo = (distanza) / (velocita' di propagazione)}$. **Maggiore e' il throughput, minore sara' il ritardo**.
- <u><b>ritardo di elaborazione</b></u>: il ritardo di elaborazione e' il tempo che serve ad un router o a un sistema terminale perche' un router completi l'elaborazione di un pacchetto.
- <u><b>ritardo di accodamento</b></u>: anche questo e' un ritardo del router e rappresenta il tempo in cui il pacchetto e' in coda in attesa di essere mandato.
## **Perdita di pacchetti**
Il numero di pacchetti persi durante la trasmissione influisce pesantemente sulle prestazioni della rete. Quando un router riceve un pacchetto mentre ne sta elaborando un altro, il pacchetto ricevuto deve essere memorizzato in un buffer di input, che ha però dimensioni limitate. Se in un determinato momento il buffer e' pieno, tutti i pacchetti inviati a quel router vengono persi.