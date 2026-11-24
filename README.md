# 🎯 IndovinaMI
"Chi mi conosce meglio di tutti?"

**IndovinaMI** è un party game web da tavolo in tempo reale in cui i partecipanti devono indovinare la classifica segreta e le preferenze personali di un giocatore alla volta (il *Leader* di turno). 

---

## 🚀 Caratteristiche Principali

* 📱 **Multi-dispositivo in Tempo Reale**: I giocatori si collegano da smartphone inserendo un semplice codice stanza a 4 lettere o scansionando il **QR Code**.
* 🎯 **Rotazione Equa dei Turni**: Il sistema seleziona casualmente il *Leader* del turno assicurandosi che tutti i partecipanti giocino prima di iniziare un nuovo ciclo.
* ✋ **Drag & Drop con effetto Trello**: Ordinamento delle 5 opzioni fluido da mobile (tramite ancora grafica `⋮⋮` e slot visivo tratteggiato) o con frecce direzionali.
* 📚 **Banco Domande Cloud + CSV personalizzabile**: 
  * Include una libreria di domande predefinite su Firebase.
  * Consente all'Host di caricare al volo file CSV con mazzi di domande personalizzati (con supporto al testo dinamico della domanda adattato per il Leader e per i giocatori).
* ⏱️ **Timer Sincronizzato di 60s**: Quando il Leader invia la propria classifica segreta, parte un conteggio alla rovescia di 1 minuto per sollecitare la risposta degli altri partecipanti.
* 🏆 **Classifica e Podio Stilizzato**:
  * Risultati trasparenti con dettaglio dei punti guadagnati per singola posizione, bonus e malus.
  * Schermata finale della classifica generale ordinata in ordine decrescente con podio stilizzato per i primi 3 posti (🥇 oro, 🥈 argento, 🥉 bronzo) ed evidenziazione visiva del proprio nome.

---

## 📜 Regole del Gioco e Calcolo dei Punteggi

In ogni turno, un giocatore viene scelto come **Leader**. Il Leader sceglie e ordina in modo segreto 5 opzioni (dalla sua preferita al 1° posto, fino alla meno preferita al 5° posto). Contemporaneamente, tutti gli altri giocatori cercano di indovinare la classifica esatta ordinata dal Leader.

### Punteggio per i Giocatori che indovinano:
* **+2 punti** per ciascuna posizione estrema indovinata (1ª o 5ª opzione).
* **+1 punto** per ciascuna posizione intermedia indovinata (2ª, 3ª o 4ª opzione).
* **+3 punti Bonus** se un giocatore indovina la sequenza perfetta (5/5 posizioni).
* **-1 punto Malus** se un giocatore non indovina nessuna posizione (0/5 posizioni).

### Punteggio per il Leader di turno:
* **0 punti** di base.
* **+3 punti Bonus Leader** se **ogni singola opzione (tutte e 5)** della sua classifica viene indovinata da almeno un partecipante al tavolo.

---

## 📁 Formato File CSV Personalizzato

Se desideri caricare un mazzo di domande personalizzato tramite file `.csv`, organizza le colonne nel seguente formato (UTF-8):

```csv
domanda,domanda_giocatori,risp1,risp2,risp3,risp4,risp5
Quali sono i tuoi gusti di gelato preferiti?,Quali sono i gusti di gelato preferiti di {leader}?,Cioccolato,Fragola,Pistacchio,Limone,Stracciatella
Dove vorresti passare la tua vacanza ideale?,Dove {leader} vorrebbe passare la sua vacanza ideale?,Spiaggia tropicale,Montagna in inverno,Città d'arte,Campeggio nella natura,Crociera nei Caraibi
