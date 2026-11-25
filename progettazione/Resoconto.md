## Sezione 1

1. Struttura e documentazione dei dati (dati/)
File JSON: Creazione di due sorgenti dati separate:
sedi.json: contiene le 3 sedi del festival (id, nome, indirizzo).
eventi.json: contiene i 6 appuntamenti (id, titolo, data, orario, categoria, descrizione, immagine, immagine_alt, sede_id).
Documentazione (dati/SCHEMA.md): Redazione della scheda tecnica che descrive le entità Evento e Sede, i tipi di campo, le chiavi primarie (id), la relazione uno-a-molti (Evento.sede_id → Sede.id), i volumi dei dati, il flusso di aggiornamento tramite repository e un diagramma relazionale finale in sintassi Mermaid.

2. Generazione dinamica del programma (programma.html)
Caricamento asincrono: Sostituzione delle card statiche HTML con uno script JavaScript che legge eventi.json e sedi.json tramite fetch.
Incrocio dei dati e resilienza: Collegamento automatico tra ogni evento e il nome della rispettiva sede tramite sede_id, con gestione del caso limite in cui l'ID non corrisponda (mostrando il fallback "Sede da definire" senza nascondere l'evento).
Gestione degli stati UI: Visualizzazione di messaggi accessibili (role="status" / role="alert") durante il caricamento, in assenza di eventi o in caso di errore nella lettura dei file.

3. Integrazione meteo in tempo reale (info.html e style.css)
Consumo API esterna: Aggiunta della sezione "Meteo a Torino adesso" collegata tramite fetch all'endpoint pubblico di Open-Meteo per mostrare temperatura, velocità del vento e orario di rilevazione.
Trasparenza e gestione errori: Inserimento della nota esplicativa (condizioni attuali e non previsioni per il festival), del credito con link alla fonte (Open-Meteo, CC BY 4.0) e di un blocco try/catch che isola eventuali errori di rete senza bloccare mappa e carosello.
Layout responsive: Rimozione del vincolo di larghezza massima su .meteo-card e impostazione di una griglia fluida affinché il riquadro occupi il 100% del contenitore e si adatti a desktop, tablet e smartphone.