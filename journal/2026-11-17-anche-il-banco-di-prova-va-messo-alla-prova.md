# Anche il banco di prova va messo alla prova

17 novembre 2026 · Pubblicato il 17 novembre 2026.

Una memoria aziendale deve conservare fonti e storia, ma deve anche sapere quando
una risposta può essere consegnata e quando deve fermarsi. Oggi abbiamo lavorato
sul collegamento fra questi principi e un servizio interrogabile.

La prima prova della giornata ha attraversato il ciclo di vita della build con
un database reale: avvio, applicazione dei permessi, interrogazione, revoca e
chiusura. I nove controlli previsti sono passati. La consegna della risposta era
ancora osservata attraverso un trasporto controllato: non era una prova completa
attraverso il browser e non attestava che una persona avesse ricevuto i dati.

Il passo successivo era verificare il collegamento HTTP reale. Qui la prova si è
fermata prima della prima richiesta.

## Il difetto era nel banco di prova

Un componente scriveva le credenziali nel formato «utente e password». Quello che
le leggeva si aspettava soltanto la password e rifiutava i campi inattesi. La
validazione ha quindi bloccato l'avvio del percorso applicativo.

La prudenza della validazione era corretta; il contratto fra i due componenti era
stato collegato male. È un errore del nostro banco di prova, non una dimostrazione
che le regole della memoria o dei permessi siano sbagliate. Ma non sarebbe stato
corretto nemmeno liquidarlo come un dettaglio: quel confine non era coperto dai
test precedenti.

Abbiamo conservato il tentativo, fermato le risorse possedute e corretto la
traduzione fra formato su disco e modello interno. Il lettore ora riconosce
esplicitamente il formato previsto, rifiuta dati inattesi e mantiene riservata la
diagnostica. Quattro nuovi test coprono quel confine. La suite risultante conta
144 verifiche offline superate, comprese le regressioni precedenti.

Questo numero non dimostra che la nuova prova HTTP sia riuscita: quella prova è
preparata, ma deve ancora essere autorizzata ed eseguita. Anche i test richiedono
precisione nel raccontare che cosa hanno realmente osservato.

## Un'azienda sintetica non è ancora un benchmark validato

In parallelo abbiamo iniziato la revisione di un corpus aziendale sintetico:
60 documenti dichiarati nel primo lotto, 100 domande e un catalogo di 150 scenari.
Il catalogo comprende casi futuri e prove tecniche, quindi non rappresenta 150
esperimenti già effettuati.

Abbiamo confrontato report e metadati di valutazione con i contratti del sistema,
senza ancora validare i documenti originali. Alcune domande del generatore
riguardavano regole già approvate; altre hanno messo in evidenza limiti reali,
come la possibilità di rispondere usando soltanto una parte delle fonti autorizzate.

Le risposte attese generate da un modello devono essere revisionate. Se il sistema
impara a soddisfare un oracolo sbagliato, un buon punteggio può nascondere un
comportamento scorretto. Per questo teniamo separati documenti, soluzioni del
valutatore e capacità effettivamente verificate.

## La prossima verifica

Il prossimo passo è ripetere il percorso HTTP corretto in una nuova prova isolata,
conservando la precedente. Sul corpus, invece, occorre chiarire gli oracoli e i
tempi delle domande prima di ampliarlo.

Restano aperte le prove su scala aziendale, l'autenticazione produttiva e
l'interfaccia definitiva. L'obiettivo di oggi era più circoscritto: rendere
verificabile il confine fra componenti e raccontare con precisione anche lo stop.
