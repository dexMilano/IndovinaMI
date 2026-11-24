# 🎯 IndovinaMI

**"Chi mi conosce meglio di tutti?"**

**IndovinaMI** è un party game web da tavolo in tempo reale in cui i partecipanti devono indovinare la classifica segreta e le preferenze personali di un giocatore alla volta (il **bersaglio** di turno).

Progettato con un'architettura **mobile-first**, l'applicazione gira interamente all'interno di un sito statico (come **GitHub Pages**) ed è sincronizzata in tempo reale per tutti i telefoni grazie all'integrazione con **Firebase Realtime Database**.

---

## 🚀 Caratteristiche Principali

* 📱 **Multi-dispositivo in Tempo Reale**: I giocatori si collegano da smartphone inserendo un semplice codice stanza a 4 lettere o scansionando il **QR Code**.
* 🎯 **Rotazione Equa dei Turni**: Il sistema seleziona casualmente il **bersaglio** del turno assicurandosi che tutti i partecipanti diventino bersaglio prima di iniziare un nuovo ciclo.
* ✋ **Drag & Drop con effetto Trello**: Ordinamento delle 5 opzioni fluido da mobile (tramite ancora grafica `⋮⋮` e slot visivo tratteggiato) o con frecce direzionali.
* 📚 **Banco Domande Cloud + CSV personalizzabile**:
  * Include una libreria di domande predefinite su Firebase.
  * Consente all'Host di caricare al volo file CSV con mazzi di domande personalizzati, mostrando il nome del mazzo (senza estensione) e il numero di domande, con possibilità di svuotare e aggiornare il DB.
* ⏱️ **Timer Sincronizzato di 60s**: Quando il **bersaglio** invia la propria classifica segreta, parte un conteggio alla rovescia di 1 minuto per sollecitare la risposta degli altri partecipanti.
* 🏆 **Risultati Mirati e Classifica Generale**:
  * Ogni giocatore (non bersaglio) vede le scelte del bersaglio, se ha indovinato ogni posizione, il dettaglio del calcolo del proprio punteggio del turno e il totale del turno, senza vedere i punteggi degli altri giocatori.
  * Il **bersaglio** vede per ciascuna propria risposta quanti giocatori hanno indovinato e se ha preso o meno il bonus del bersaglio (se attivato all'avvio della partita), senza vedere i punteggi dei giocatori.
  * Schermata classifica generale ordinata in ordine decrescente con podio stilizzato per i primi 3 posti (🥇 oro, 🥈 argento, 🥉 bronzo) ed evidenziazione visiva del proprio nome.

---

## 📜 Regole del Gioco e Calcolo dei Punteggi

In ogni turno, un giocatore viene scelto come **bersaglio**. Il **bersaglio** ordina in modo segreto 5 opzioni (dalla preferita al 1° posto, fino alla meno preferita al 5° posto). Contemporaneamente, tutti gli altri giocatori cercano di indovinare l'ordine scelto dal **bersaglio**.

### Punteggio per i Giocatori che indovinano:
* **+2 punti** per ciascuna posizione estrema indovinata (1ª o 5ª opzione).
* **+1 punto** per ciascuna posizione intermedia indovinata (2ª, 3ª o 4ª opzione).
* **+3 punti Bonus** se un giocatore indovina la sequenza perfetta (5/5 posizioni).
* **-1 punto Malus** se un giocatore non indovina nessuna posizione (0/5 posizioni).

### Punteggio per il Bersaglio di turno (opzionale all'avvio della partita):
* L'Host può attivare o disattivare il **bonus del bersaglio** prima di creare la stanza.
* Se abilitato, assegna **+3 punti** al **bersaglio** se **ogni singola opzione (tutte e 5)** viene indovinata da almeno un giocatore al tavolo.

---

## 📁 Formato File CSV Personalizzato

Se desideri caricare un mazzo di domande personalizzato tramite file `.csv`, organizza le colonne nel seguente formato (UTF-8):

```csv
domanda,domanda_giocatori,risp1,risp2,risp3,risp4,risp5
Quali sono i tuoi gusti di gelato preferiti?,Quali sono i gusti di gelato preferiti di {bersaglio}?,Cioccolato,Fragola,Pistacchio,Limone,Stracciatella
Dove vorresti passare la tua vacanza ideale?,Dove {bersaglio} vorrebbe passare la sua vacanza ideale?,Spiaggia tropicale,Montagna in inverno,Città d'arte,Campeggio nella natura,Crociera nei Caraibi