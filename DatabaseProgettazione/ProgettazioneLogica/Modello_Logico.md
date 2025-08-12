CATEGORIA(ID_Categoria, nomeCategoria, descrizione)

ANNUNCIO(ID_Annuncio, tipoAnnuncio, descrizione, prezzo, dataCreazione, modalitaConsegna, luogoConsegna, statoAnnuncio, dataScadenza, ID_Utente_FK, ID_Categoria_FK)

OFFERTA_VENDITA(ID_Offerta, prezzo, descrizione, dataOfferta, statoOfferta, ID_Annuncio_FK, ID_Utente_FK)

OFFERTA_RIFIUTATA(ID_OffertaRifiutata, dataRifiuto, motivoRifiuto, ID_Offerta_FK)

OFFERTA_ACCETTATA(ID_OffertaAccettata, dataAccettazione, ID_Offerta_FK)

REGALO(ID_Regalo, descrizione, dataOfferta, statoOfferta, ID_Annuncio_FK, ID_Utente_FK)

REGALO_ACCETTATO(ID_RegaloAccettato, dataAccettazione, ID_Regalo_FK)

OFFERTA_SCAMBIO(ID_Scambio, descrizione, dataOfferta, statoOfferta, ID_Annuncio_FK, ID_Utente_FK)

SCAMBIO_ACCETTATO(ID_ScambioAccettato, dataAccettazione, ID_Scambio_FK)

OGGETTO_PROPOSTO(ID_OggettoProposto, descrizione, immagine, ID_Scambio_FK)

UTENTE(ID_Utente, nome, cognome, email, password, indirizzo, dataRegistrazione, statusAccount)

RECENSIONE(ID_Recensione, descrizione, valutazione, commento, dataCreazione, ID_Utente_Recensore_FK, ID_Utente_Recensito_FK)

MESSAGGIO(ID_Messaggio, contenutoMessaggio, dataInvio, ID_Chat_FK)

CHAT(ID_Chat, dataChatCreazione, tipoChat, ID_Utente1_FK, ID_Utente2_FK)

NOTIFICA(ID_Notifica, tipoNotifica, contenuto, isLetta, dataInvio, statoNotifica, ID_Utente_FK)

TRANSAZIONE(ID_Transazione, dataInizio, statoTransazione, ID_Offerta_FK, ID_Utente_Acquirente_FK, ID_Utente_Venditore_FK)

PREFERITI(ID_Preferiti, dataAggiunta, ID_Utente_FK, ID_Annuncio_FK)





# Modello Logico per UninaSwap

---------------------------------------

## Motivazione delle scelte effettuate

### Gestione dell'ereditarietà

1. **Annuncio estende Categoria**
   - Annuncio mantenuto come entità separata con una chiave esterna (ID_Categoria_FK) che referenzia Categoria.

2. **OFFERTA_VENDITA, REGALO e OFFERTA_SCAMBIO estendono Annuncio**
   - Rappresentate queste entità come tabelle separate con una chiave esterna (ID_Annuncio_FK) che referenzia Annuncio.
   - Motivazione: Questa struttura permette di gestire i diversi tipi di offerte come specializzazioni di un annuncio, mantenendo dati specifici per ciascun tipo di offerta mentre si condividono le caratteristiche comuni attraverso il collegamento con la tabella Annuncio.

### Struttura generale rivista

1. **ANNUNCIO**
   - Contiene gli attributi comuni a tutti i tipi di annuncio.
   - Il campo tipoAnnuncio distingue tra VENDITA, SCAMBIO e REGALO.
   - Motivazione: Centralizza le informazioni di base dell'annuncio indipendentemente dalla sua tipologia.

2. **OFFERTA_VENDITA, REGALO, OFFERTA_SCAMBIO**
   - Ogni tipo di offerta è una tabella separata collegata all'annuncio a cui si riferisce.
   - Motivazione: Permette di gestire attributi specifici per ciascun tipo di offerta mantenendo la struttura di ereditarietà.

3. **TRANSAZIONE**
   - Modificata la relazione per riferirsi all'offerta (ID_Offerta_FK) invece che direttamente all'annuncio.
   - Motivazione: Una transazione avviene quando un'offerta viene accettata, non direttamente dall'annuncio.

## Vincoli

1. **Vincoli di Ereditarietà**:
   - Il tipoAnnuncio in ANNUNCIO deve corrispondere al tipo di offerta accettata (se un annuncio è di tipo VENDITA, solo offerte di tipo OFFERTA_VENDITA possono essere accettate).
   - Un annuncio può avere solo un'offerta accettata in totale, indipendentemente dal tipo.

2. **Vincoli di Chiave**:
   - Ogni tabella ha una chiave primaria (ID_X) che identifica univocamente ogni record.
   - Le chiavi esterne (FK) garantiscono l'integrità referenziale tra tabelle.

3. **Vincoli di Dominio**:
   - `valutazione` nella tabella RECENSIONE deve essere un intero compreso tra 1 e 5.
   - `prezzo` nella tabella ANNUNCIO per tipoAnnuncio = "VENDITA" deve essere > 0.
   - `prezzo` nella tabella ANNUNCIO per tipoAnnuncio = "REGALO" deve essere = 0.
   - `statoAnnuncio` può assumere solo i valori: ATTIVO, SCADUTO, RIMOSSO, COMPLETATO.
   - `statoTransazione` può assumere solo i valori: IN_CORSO, COMPLETATA, ANNULLATA.
   - `statusAccount` può assumere solo i valori: ATTIVO, SOSPESO, RIPOSO, IN_VALIDAZIONE, CONGELATO.

4. **Vincoli di Integrità**:
   - Un utente non può fare un'offerta per un proprio annuncio (ID_Utente_FK in OFFERTA_X ≠ ID_Utente_FK in ANNUNCIO).
   - La `dataScadenza` di un annuncio deve essere successiva alla `dataCreazione`.
   - La `dataAccettazione` di un'offerta deve essere successiva alla `dataOfferta`.
   - Una transazione può essere completata solo se l'offerta relativa è stata accettata.
   - Un'offerta di scambio deve avere almeno un oggetto proposto nella tabella OGGETTO_PROPOSTO.

5. **Vincoli di Business**:
   - Un utente con statusAccount diverso da ATTIVO non può creare nuovi annunci.
   - Un annuncio con stato diverso da ATTIVO non può ricevere offerte.
   - Un utente può accettare una sola offerta per ogni annuncio.
   - Le recensioni possono essere lasciate solo a transazione con stato COMPLETATA.
   - Le chat possono essere create solo tra utenti con almeno un'interazione su un annuncio.
   - Una transazione può avvenire solo tra due utenti diversi (ID_Utente_Acquirente_FK ≠ ID_Utente_Venditore_FK).
   - Un utente non può recensire il suo stesso account

6. **Vincoli di Sicurezza**:
   - Le password degli utenti devono essere memorizzate in forma criptata.
   - Solo il proprietario di un annuncio può modificarne lo stato o accettare offerte.
   - Solo gli utenti coinvolti in una chat possono visualizzarne i messaggi.
   - Un utente può modificare o cancellare solo i propri annunci.

