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
##