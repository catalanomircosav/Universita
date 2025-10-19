---
tags:
  - map
---
# Information Hiding
- Principio fondamentale dell'**astrazione**. Suggerisce di **occultare l'informazione sulla rappresentazione del dato**.  
  Questo occultamento è giustificato per due ragioni principali:
  - <u>L'informazione nascosta non è necessaria</u> a chi utilizza l'entità astratta.
  - <u>La sua rivelazione creerebbe dipendenze superflue</u>.

## Forme principali di astrazione
- Si possono distinguere due principali forme di **information hiding**:
### 1. Astrazione funzionale
- Il principio suggerisce di **occultare i dettagli del processo di trasformazione**, ovvero il "**come**" viene eseguita un'operazione.
- Per l'utente è importante "**cosa**" fa il codice, non il "**come**" lo fa.
- <u>I dettagli algoritmici del calcolo non sono visibili al consumatore del modulo</u>.
### 2. Astrazione dei dati
- Il principio suggerisce di **occultare la rappresentazione interna del dato**.
- <u>L'accesso al dato non può essere diretto</u>, ma deve avvenire solo attraverso un insieme di **operazioni considerate lecite**.
___
# Encapsulation
L'**incapsulamento** è una tecnica di progettazione che <u>consiste nell'"impacchettare" o "racchiudere in capsule"</u> una collezione di entità, creando una barriera concettuale.

**esempio**:
- una libreria che incapsula diverse funzioni,
- un oggetto che incapsula un dato.

L'incapsulamento non specifica come devono essere le "pareti" del pacchetto, che potranno essere:
- **trasparenti**: permettendo di vedere tutto ciò che e' stato impacchettato;
- **traslucide**: permettendo di vedere in modo parziale il contenuto;
- **opache**: nascondendo tutto il contenuto del pacchetto.

Ovviamente, l'isolamento dei moduli non può essere totale. La specifica, o contratto, descrive come si può interagire con un dato astratto.