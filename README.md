# UninaSwap – ProjettoJavaSqlUni

UninaSwap è una piattaforma progettata per la compravendita, lo scambio e il regalo di oggetti tra studenti universitari. Il progetto è stato sviluppato nell’ambito del corso di Programmazione Object-Oriented e utilizza Java, SQL e librerie grafiche per la generazione di report.

## Descrizione del Dominio

Gli utenti possono pubblicare annunci per oggetti personali, specificando:
- **Descrizione dell’oggetto**
- **Categoria** (es: libri di testo, materiale informatico, abbigliamento, strumenti musicali)
- **Tipologia annuncio**: vendita, scambio, regalo
- **Prezzo** (se applicabile)
- **Modalità di consegna**: sede universitaria, incontro, spedizione ecc...

Gli altri utenti possono inviare offerte:
- **Vendita**: confermare il prezzo o offrire meno
- **Scambio**: proporre oggetti in cambio
- **Regalo**: inviare una richiesta motivazionale

Il proprietario seleziona l’offerta da accettare e aggiorna lo stato dell’annuncio (venduto, scambiato ecc).

> **Extra**: Ogni transazione può essere recensita dall’acquirente.

## Funzionalità

- **Autenticazione**: login tramite username e password
- **Visualizzazione annunci**: ricerca e filtri per categoria e tipologia
- **Gestione offerte**: invio, modifica o ritiro (se non valutate)
- **Storico offerte**: verifica stato (in attesa, accettata, rifiutata)
- **Report sintetico**: 
  - Numero totale offerte inviate (per tipologia)
  - Numero offerte accettate (per tipologia)
  - Valore medio, minimo e massimo delle offerte accettate (solo vendita)
  - **Grafico**: generato con JFreeChart 
- **Recensioni (opzionale)**: l’acquirente lascia una recensione al termine della transazione
  - Punteggio basato su un sistema di emoji e commento testuale
  - Tutte le recensioni sono consultabili e collegate all’identità del venditore

## Tecnologie Utilizzate

- Java
- JDBC/SQL
- JFreeChart (per i grafici) 
- JavaFX (interfaccia grafica)

## Installazione

1. Clona la repository:
   ```bash
   git clone https://github.com/Carloj005/ProjettoJavaSqlUni.git
   ```
2. Configura il database secondo le istruzioni in `/docs` (o aggiungile qui se non esiste una guida separata). # DA VEDERE #
3. Importa il progetto in un IDE Java (es: IntelliJ, Eclipse).
4. Aggiungi le librerie dipendenti (vedi sezione Tecnologie).

## Utilizzo

1. Avvia l’applicazione.
2. Esegui il login o registrati.
3. Naviga tra gli annunci, filtra per categoria o tipologia.
4. Invia, modifica o ritira offerte.
5. Consulta i report e, se previsto, lascia una recensione.

## Contributi

Contributi, segnalazioni di bug o proposte di nuove funzionalità sono benvenuti! Apri una issue o una pull request.

## Licenza

Specificare qui la licenza del progetto (es: MIT, GPL, ecc.) # NON SO ANCORA COSA METTERE #

---

**Progetto sviluppato per lo studio e l'apprendimento pratico di Programmazione Object-Oriented e Basi di Dati – Università degli Studi di Napoli Federico II**
