---
tags:
  - map
---
## polimorfismo per inclusione
Data una dichiarazione di una variabile o di un parametro il cui tipo è dichiarato come `X`, una qualunque istanza di una classe che è discendente di `X` può essere usato come valore effettivo senza violare la **semantica della dichiarazione e il suo uso**.
In altri termini, l’istanza di un **discendente** può essere sostituita all’istanza di un **ascendente**.

- La conseguenza del principio di sostituibilità è che una sottoclasse  non può rimuovere o rinunciare a proprietà/metodi della superclasse. Altrimenti una istanza della sottoclasse non sarà sostituibile in una situazione in cui si dichiara l’uso di istanze della superclasse.

- In effetti, preservando la visibilità degli attributi e dei metodi ereditati, così come accade nelle tre forme di ereditarietà viste, si garantisce che gli oggetti della sottoclasse offrano quanto meno gli stessi servizi degli oggetti della superclasse