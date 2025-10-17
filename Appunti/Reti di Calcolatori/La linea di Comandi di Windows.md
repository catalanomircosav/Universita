#reti 
___
## **Introduzione alla CLI**
La **Command Line Interface (CLI)** o **Prompt dei Comandi** è un'interfaccia testuale che permette di interagire con il sistema operativo tramite comandi digitati da tastiera. A differenza della GUI (Graphical User Interface), la CLI offre un controllo più diretto e potente sul sistema, ed è spesso preferita da utenti esperti e amministratori per la sua velocità e flessibilità.

## **Struttura del File System**
### **Drive**
I drive sono le unità di memorizzazione identificate da una lettera seguita da due punti (es. `C:`, `D:`). Il drive `C:` è tipicamente il disco fisso principale.
### **File**
Un file è l'unità minima di memorizzazione. È composto da:
- **Nome**: fino a 260 caratteri (incluso il percorso)
- **Estensione**: indica il tipo di file (es. `.DOCX` per documenti Word)
**Caratteri consentiti**: lettere, numeri, spazi e alcuni simboli speciali (`{ } ~ $ & @ | { } ' _ ^ - £`)
**Caratteri vietati**: `+ = / : ; ? * \ < > |`
### **Directory**
Le directory (o cartelle) organizzano i file in una **struttura ad albero**. La directory principale è detta **root** (`\`). Le directory figlie sono separate da `\`.
### **Pathname**
Il **pathname** è il percorso completo per localizzare un file o una directory. Può essere:
- **Assoluto**: inizia con `\` e parte dalla root (es. `C:\WORKS\CONS2\PARTE.BAT`)
- **Relativo**: parte dalla directory corrente (es. `CONS2\PARTE.BAT`)

I pathname relativi possono iniziare con:
- Nome del file: `MIO.DOCX` (nella directory corrente)
- Punto singolo: `.\MIO.DOCX` (esplicitamente nella directory corrente)
- Doppio punto: `..\MIO.DOCX` (nella directory genitore)

## **Sintassi dei Comandi**
Un comando è composto da:
1. **Parola chiave**: identifica il comando (obbligatoria)
2. **Parametri**: specificano gli oggetti su cui agire
3. **Opzioni**: modificano il comportamento del comando
Le parti sono separate da spazi. I comandi sono **case insensitive**.
## **Tipi di Comandi**
- **Comandi interni**: residenti in memoria (es. CD, CLS, COPY, DEL, DIR)
- **Comandi esterni**: file eseguibili sul disco (es. XCOPY, TREE, FORMAT)
## **Caratteri Jolly**
- `*` sostituisce uno o più caratteri (es. `GRA*.DOC`)
- `?` sostituisce un singolo carattere (es. `GIANNI?.DOC`)
## **Backup con XCOPY**
Il comando XCOPY è ideale per backup incrementali. Con l'opzione `/D`, copia solo i file modificati dall'ultimo backup, risparmiando tempo.
## **File Batch**
I file batch (estensione `.BAT`) automatizzano sequenze di comandi. Utili per operazioni ripetitive o comandi complessi.

---

## **Tabella Riepilogativa dei Comandi**

| Comando | Descrizione |
|---------|-------------|
| `CD` | Cambia la directory corrente |
| `CLS` | Pulisce lo schermo |
| `MD` | Crea una nuova directory |
| `COPY` | Copia file o directory |
| `DEL` | Elimina file |
| `DIR` | Elenca file e directory |
| `MOVE` | Rinomina o sposta directory |
| `REN` | Rinomina file |
| `XCOPY` | Copia ricorsiva di directory con opzioni avanzate |
### **Backup avanzato con XCOPY**
`XCOPY C:\MIOSITO\*.* H:\BACKUP /S /D /Y /I`
- `/S`: copia sottodirectory non vuote
- `/D`: copia solo file modificati
- `/Y`: sovrascrive senza conferma
- `/I`: crea automaticamente directory destino
### **Utilizzo caratteri jolly**
```
COPY GRA*.DOC \MIOSITO       (copia tutti i file che iniziano con "GRA")
DEL *.TMP                    (elimina tutti i file .TMP)
```
