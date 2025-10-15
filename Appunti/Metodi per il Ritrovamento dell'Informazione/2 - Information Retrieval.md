#mri 
___
# **Modello di retrieval**
L'**information retrieval** intelligente si basa sulla definizione di un **modello di retrieval**. 
Un modello di questo tipo specifica i dettagli della rappresentazione di un documento, della rappresentazione della query e della funzione di retrieval. Determina anche la **rilevanza**, che può essere *binaria* oppure *continua*. <u><b>La funzione di ranking assegna punteggi ai documenti a una data query</b></u>

Un modello di Information Retrieval e' definito come una quadrupla:
$$[D,Q,F,R(q_i,d_j)]$$
dove:
- $D$ e' l'insieme delle viste logiche dei **documenti**,
- $Q$ e' l'insieme delle viste logiche delle **query utente**
- $F$ e' il **framework utilizzato per modellare i documenti e le query**,
- $R(q_i, d_j)$ e' la **funzione di ranking**.

