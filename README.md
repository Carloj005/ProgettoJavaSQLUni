# ProgettoJavaSQLUni
2.3 Traccia 3: UninaSwap
2.3.1 Descrizione del dominio
UninaSwap è una piattaforma per la compravendita, lo scambio e il regalo di oggetti tra studenti universitari. 
Gli utenti possono pubblicare annunci relativi a oggetti personali, specificando una descrizione, una categoria (es. libri di testo, materiale informatico, abbigliamento, strumenti musicali), e la tipologia dell’annuncio (vendita, scambio, regalo) e, se necessario, il prezzo richiesto. 
Per ciascun annuncio è possibile indicare testualmente le modalità di consegna, specificando ad esempio la sede universitaria in cui avverrà l’incontro e la fascia oraria preferita. 
Gli utenti interessati possono inviare offerte per qualsiasi tipo di annuncio. 
Nel caso di vendita, l’offerta può consistere nella conferma del prezzo proposto dal venditore oppure in una proposta economica inferiore. 
Nel caso di scambio, chi risponde all’annuncio deve specificare uno o più oggetti che intende offrire in cambio. Anche per gli annunci di regalo è prevista la possibilità di inviare offerte, 
tra tutte quelle ricevute, il proprietario potrà selezionarne una da accettare e aggiornare lo stato dell’annuncio (es. venduto, scambiato, etc). 
Si utilizzino le proprie conoscenze del dominio per definire eventuali dettagli non specificati nella traccia. 
(Extra) Per i soli gruppi da 3 membri: Il sistema prevede al termine di ogni transizione tra utenti dilasciare una recensione.

2.3.2 Specifica delle funzionalità per l’insegnamento di Programmazione Object-Oriented L’applicativo deve consentire l’autenticazione degli utenti tramite credenziali (username e password). 
Una volta effettuato l’accesso, l’utente può visualizzare gli annunci attivi presenti sulla piattaforma, applicando filtri per categoria dell’oggetto e tipologia dell’annuncio (vendita, scambio, regalo). 
Selezionato un annuncio, l’utente ha la possibilità di inviare un’offerta: nel caso di vendita, può accettare il prezzo richiesto oppure proporre un’offerta economica inferiore; nel caso di scambio, può accettare gli oggetti proposti dal venditore oppure specificarne di alternativi; nel caso di regalo, può inviare una richiesta accompagnata da un breve messaggio motivazionale. 
L’utente può consultare lo storico delle offerte inviate, verificarne lo stato (in attesa, accettata, rifiutata) e ha la possibilità di modificarle o ritirarle se non ancora valutate. 
Infine, il sistema deve generare un report sintetico, accessibile in un’apposita sezione, che mostri il numero totale di offerte inviate, suddivise per tipologia, il numero di offerte accettate per ciascuna tipologia e, per gli annunci di vendita accettati, il valore medio, minimo e massimo in euro delle offerte accettate. 
Il report deve includere una rappresentazione grafica dei dati, realizzata con l’ausilio di una libreria come JFreeChart. Per i soli gruppi da 3 membri: il sistema deve permettere all’acquirente, in seguito all’accettazione di un’offerta e della consegna, di inserire una recensione nei confronti del venditore, specificando un commento testuale e un punteggio numerico. 
Tutte le recensioni inviate sono consultabili in un’apposita sezione dell’interfaccia e collegate all’identità del venditore.
.