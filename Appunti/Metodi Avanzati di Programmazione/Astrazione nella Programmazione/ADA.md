___
In Ada, il package è l’unità fondamentale di **modularità, incapsulamento e astrazione**. Il suo scopo è separare ciò che un’unità _offre_ (interfaccia) da come è _implementata_. Questo rende il codice più sicuro, mantenibile ed estensibile.

Un package Ada è diviso in due parti:
1. **Specification (spec)** → _cosa_ viene esposto al mondo esterno
2. **Body (implementazione)** → _come_ è realizzato ciò che viene esposto

Il package spec fornisce un **contratto**, ossia un insieme di operazioni disponibili e di tipi di dato utilizzabili dall’esterno. Il body contiene il codice vero e proprio e può essere modificato senza interferire con il codice client, a patto di mantenere stabile l’interfaccia.

## **Incapsulamento e parte `private`**
In Ada, la parte più potente per l’astrazione di tipo è la parola chiave `private`. Dichiarando un tipo come:

```
type T is private;
```

si comunica che **il tipo esiste**, che può essere usato e passato a funzioni, ma **la sua rappresentazione non è visibile** all’esterno. La vera struttura del tipo viene definita nella sezione `private` della specification o nel body, ma comunque **non è accessibile dal client**. Questo realizza un vero **Tipo Astratto di Dato (TAD)**.
La variante:

```
type T is limited private;
```

impedisce inoltre operazioni automatiche come assegnazione e confronto, nel caso in cui vogliamo controllare completamente tutte le manipolazioni possibili sul tipo.

## **TAD in ADA: costruttori, osservatori e mutatori**
Un Tipo Astratto di Dato è definito non dalla sua rappresentazione, ma dalle sue **operazioni lecite**. 
Per questo un TAD è composto da tre categorie di operazioni:
- **Costruttori** → creano oggetti del tipo
- **Osservatori** → leggono informazioni senza modificarlo
- **Mutatori** → modificano lo stato interno del tipo

Nel caso di uno `Stack`, i costruttori creano stack vuoti, gli osservatori controllano dimensione ed elementi, i mutatori permettono di aggiungere o rimuovere elementi.

Il package è la struttura perfetta per ospitare un TAD: la specification contiene le operazioni, la private part e il body contengono la rappresentazione nascosta.

## **Generic Package**
Se invece di uno stack di `Integer` vogliamo uno stack di _qualunque tipo_, Ada permette di trasformare un package in **generic**, cioè parametrico. Un generic package non produce computazione, ma **genera dichiarazioni**. Fornendo i parametri (come `Element_Type`), otteniamo un nuovo package concreto.

## **Visibilità: `with` e `use`**
Per importare un package, si usa:

```
with Nome_Package;
```

Il nome va poi qualificato:

```
X := Nome_Package.Funzione(...);
```

Se il package è usato spesso, si può aggiungere anche:

```
use Nome_Package;
```

in modo da evitare la qualificazione e rendere più leggibile il codice, con la consapevolezza che può ridurre la chiarezza in progetti molto grandi.