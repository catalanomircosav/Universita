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

I modelli di retrieval possono essere classificati in:
- <u>modelli booleani</u>: *theroetic set*, *extended boolean*,
- <u>modelli vector space</u>: *statistical/algebric*,
- <u>modelli probabilistici</u>.
## **Pre-processing**
Prima che i documenti possano essere indicizzati, e' necessaria una serie di passaggi di *pre-elaborazione*, essenziali per **normalizzare** il testo:
1. **Strip unwanted characters/markup**: Rimozione di caratteri indesiderati, punteggiatura, numeri, ecc.
2. **tokenization**: Il testo viene diviso in **token** (parole chiave), basandosi sugli spazi. Si creano qui due sfide: gestione dei termini ipotetici e dei numeri, che i **sistemi IR** meno recenti tendevano a non indicizzare. Inoltre, alcune lingue asiatiche non utilizzano spazi tra le parole, richiedendo algoritmi specifici.
3. **normalization to terms**: l'obiettivo di questa fase e' di portare le parole indicizzate e i termini della query alla stessa forma standard.
   Si definiscono in questa fase le **classi di equivalenza**.