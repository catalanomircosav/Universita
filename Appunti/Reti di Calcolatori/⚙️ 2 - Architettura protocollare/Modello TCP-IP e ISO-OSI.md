#reti 
___
# **Architettura TCP/IP**
L'<u><b>architettura TCP/IP</b></u> e' una gerarchia di [[Glossario#protocollo|protocolli]] costituita da moduli che interagiscono fra di loro, ciascuno dei quali svolge funzioni specifiche per permettere la comunicazione in una rete.
**E' un'architettura gerarchica, il che significa che ciascun protocollo di livello superiore viene supportato dai livelli inferiori**, e viene definita come **stack protocollare TCP/IP**.
Al giorno d'oggi, questa e' composta di 5 livelli.
![[protocollo tcp-ip.png.png]]

Ciascun dispositivo e' coinvolto con determinati livelli:
- **gli host sono coinvolti in tutti e 5 i livelli**: l'host sorgente crea un messaggio a livello applicazione e lo trasmette ai livelli sottostanti fino al livello fisico affinché possa essere risalito fino al livello applicativo all'host destinatario.
- **il router e' coinvolto solamente per tre livelli**: i livelli trasporto e applicazione non hanno senso di esistere perche' il router e' utilizzato solamente per scopi di instradamento.