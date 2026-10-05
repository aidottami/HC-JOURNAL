# Mettere alla prova la memoria: cosa abbiamo verificato nell'Hub Cognitivo

**5 ottobre 2026 · HC Engineering Journal · 002**

Una risposta corretta non basta a dimostrare che un sistema di conoscenza funzioni.
Può aver perso una citazione, duplicato un'affermazione dopo un tentativo ripetuto
o cancellato il giudizio precedente di un revisore.

Per questo una parte del nostro lavoro sull'Hub Cognitivo riguarda gli invarianti:
proprietà che devono rimanere vere anche quando cambiano il modo di acquisire i dati,
lo stato della revisione o il processo che legge la memoria.

Questo articolo racconta alcune verifiche concluse fra il 23 e il 30 settembre.
Sono prove locali su un corpus circoscritto, non una certificazione di produzione.

## 1. Acquisire singolarmente o a lotti preserva lo stesso contenuto?

Abbiamo confrontato due percorsi sugli stessi input fissati: acquisizione singola
e acquisizione in lotti di due elementi.

Negli undici punti comuni previsti dal protocollo, inclusi due stati vuoti, non
abbiamo rilevato differenze semantiche. Il confronto ha riguardato i campi dei
record e delle viste, comprese fonti, citazioni, modalità e catene di revisione.
Non ci siamo limitati a contare gli oggetti.

L'atomicità rimane diversa: un lotto viene confermato come unità. Non pretendiamo
che ogni stato intermedio del percorso singolo esista anche nel percorso a lotti.
Tempi e ricevute delle due esecuzioni restano distinguibili.

## 2. Un retry deve creare un secondo effetto?

L'idempotenza serve a evitare che ripetere una richiesta già accettata produca
una copia involontaria dell'informazione.

Nei casi previsti abbiamo verificato che ripetizioni identiche restituissero la
stessa ricevuta senza duplicare gli oggetti canonici. Abbiamo anche controllato
il rifiuto di collisioni e richieste incompatibili.

Attraverso fault applicativi prima del commit abbiamo verificato il rollback:
nessun evento o ricevuta canonica parziale nei casi esaminati. Il tentativo fallito
rimane distinguibile nell'audit.

Queste prove non equivalgono a una garanzia exactly-once distribuita. Non abbiamo
simulato guasti hardware o un crash del sistema operativo.

## 3. I giudizi possono cambiare senza riscrivere il passato?

Uno scenario parte da una relazione proposta e da due valutazioni opposte.
Il sistema conserva il disaccordo senza trasformarlo in un verdetto sulle fonti.

Quando uno dei revisori passa a un giudizio indeterminato, rimangono consultabili
sia il giudizio precedente sia lo stato storico in cui il disaccordo era presente.
L'assenza successiva del flag di disaccordo non viene interpretata come consenso.

Abbiamo inoltre verificato che una nuova versione dell'affermazione non erediti
silenziosamente i giudizi espressi sulla precedente.

Proposte e giudizi di questi scenari sono predisposti per la prova. Il risultato
riguarda la loro gestione, non la qualità di un revisore umano o di un modello linguistico.

## 4. La memoria resta ricostruibile dopo la chiusura?

Nel collegamento fra acquisizione e assessment abbiamo prodotto e confrontato
22 snapshot, 8 replay e 4 riaperture dopo la chiusura dei writer.

Le riaperture corrispondevano agli snapshot finali; i replay ripetuti conservavano
lo stesso payload. Gli undici confronti fra i due percorsi sono risultati conformi
anche in questa fase, con un mapping esplicito degli identificativi.

Le quattro sorgenti storiche sono state aperte in sola lettura e i loro hash sono
rimasti invariati. La verifica del collegamento non ha richiesto nuove chiamate LLM:
una parte degli input proveniva da risposte già registrate, un'altra da dati sintetici.

## I numeri, con il loro significato

| Verifica | Risultato finale | Che cosa misura |
|---|---|---|
| Suite acquisizione a lotti | 12 test superati | Contratti locali, atomicità, retry e ricostruzione |
| Suite assessment | 22 test superati | Giudizi, revisioni, validazione e storia |
| Suite collegamento | 17 test superati | Conservazione e mapping fra acquisizione e assessment |
| Demo del collegamento | 11 confronti conformi; 22 snapshot, 8 replay, 4 riaperture | Coerenza nel corpus e nei punti previsti |

Le righe descrivono verifiche differenti e in parte sovrapposte: non sommiamo test,
snapshot e confronti in un unico numero di “successi”.

## Anche il comparatore deve poter fallire

Un confronto sempre verde può essere un controllo troppo debole.
Abbiamo introdotto alterazioni intenzionali su copie di prova, come perdita di
provenance, modifica della modalità o della citazione: i controlli negativi le
hanno rilevate tramite differenze o rifiuti.

Lo sviluppo ha incluso errori intermedi. In una prima suite del collegamento,
una copia dello stato basata sulla serializzazione canonica riordinava gli oggetti:
abbiamo corretto la copia preservando l'ordine di registrazione. I record persistiti
non erano alterati. Sono stati corretti anche problemi nei test, mantenendo i log
dei tentativi prima della suite finale.

## Che cosa resta da dimostrare

Questi risultati non provano ancora rilevamento automatico delle contraddizioni,
risoluzione generale delle identità, autorizzazioni aziendali, scrittori concorrenti,
resistenza a crash del sistema operativo o prestazioni su larga scala.

Il prossimo passo è confrontare il sistema con domande documentali più realistiche,
partendo da un caso aziendale sintetico e da risposte attese revisionate da una persona.
Prima di misurare se una risposta è corretta, dobbiamo concordare quali evidenze
la sostengano e quando sia corretto dichiarare un'incertezza.
