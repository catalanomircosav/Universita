---
tags:
  - map
---
___
<u>Gestione delle Eccezioni</u>: I linguaggi di programmazione moderni offrono meccanismi sofisticati per la gestione delle eccezioni, che rappresentano una forma avanzata di **astrazione di controllo**. 
Questi meccanismi permettono di gestire situazioni anomale come <u>errori aritmetici</u>, <u>errori di I/O</u>, <u>fallimento di precondizioni</u> o <u>condizioni imprevedibili</u>. Quando viene sollevata un'eccezione, **il sistema cerca un gestore nel blocco corrente**, risalendo la **gerarchia delle unità chiamanti** se necessario. A seconda del modello, dopo la gestione dell'eccezione, l'esecuzione può ripartire dall'unità contenente il gestore (<u>modello di terminazione</u>, es. Ada) o tornare al comando che ha generato l'eccezione (<u>modello di ripresa</u>, es. PL/I)