# Prima del codice: quali promesse deve mantenere una memoria aziendale?

**5 ottobre 2026 · HC Engineering Journal · 003**

*Il percorso, puntata 1 — dai requisiti del 14 settembre alla revisione del 17 settembre 2026.*

Nei primi due articoli abbiamo presentato alcuni principi dell'Hub Cognitivo e le
verifiche locali già concluse. Ora torniamo all'inizio: alle domande che hanno guidato
il progetto prima di quei risultati.

La prima versione della nostra specifica è datata 14 settembre 2026. Il 17 settembre
l'abbiamo rivista, rendendo esplicito che l'architettura doveva essere valutata attraverso
esperimenti. Queste date descrivono la documentazione del percorso: non significano
che tutte le capacità richieste fossero già implementate.

## La domanda iniziale

In un'azienda, la conoscenza arriva attraverso procedure, comunicazioni, verbali e
revisioni. Le fonti possono essere incomplete, riferirsi a periodi diversi o contenere
indicazioni incompatibili.

Volevamo costruire una memoria che permettesse di interrogare questo materiale
conservando le distinzioni necessarie a interpretarlo. Una risposta avrebbe dovuto
rendere riconoscibili la fonte, il contesto temporale e gli eventuali limiti.

Un esempio sintetico basta a mostrare il problema:

> “Il responsabile deve approvare la richiesta prima dell'acquisto.”

Questa frase esprime un obbligo e una condizione. Non prova che il responsabile
abbia approvato qualcosa, né che un acquisto sia avvenuto. Se la trasformazione in
conoscenza strutturata perde queste differenze, una risposta successiva può risultare
plausibile pur sostenendo un evento mai dichiarato.

## Conservare il significato prima di semplificarlo

Abbiamo quindi definito requisiti per preservare negazione, modalità, condizioni e
attribuzione. La distinzione fra affermazione e fatto verificato è centrale:
registrare ciò che una fonte dichiara non equivale a certificarne la verità.

Anche l'assenza richiede attenzione. Una procedura che non menziona un permesso
non ne dimostra automaticamente il divieto. Un nome incompleto non autorizza a
scegliere arbitrariamente la persona più probabile. Una data mancante deve poter
rimanere ignota.

Questo impone al sistema di rappresentare l'incompletezza, invece di colmarla
silenziosamente durante l'estrazione o la normalizzazione.

## Le promesse da mettere alla prova

**Provenance verificabile.** Ogni affermazione deve poter essere ricondotta alle
proprie evidenze. Interpretazioni e inferenze devono rimanere distinguibili dal
contenuto della fonte. Due testi dal significato simile possono avere origini e
storie diverse, che una deduplicazione non deve cancellare.

**Bitemporalità.** Abbiamo richiesto di separare il periodo a cui un'informazione
si riferisce dal momento in cui il sistema la registra. Una correzione appresa oggi
può riguardare il passato, senza rendere falsa la ricostruzione di ciò che il sistema
conosceva ieri.

**Conservazione della storia.** Una nuova versione o una fonte discordante non deve
cancellare automaticamente le affermazioni precedenti. Recenza e verità sono proprietà
diverse. Correzioni e revisioni devono lasciare tracce ricostruibili; le eventuali
cancellazioni amministrative appartengono a un processo distinto e autorizzato.

**Separazione dei giudizi.** Confidenza nell'estrazione, attendibilità della fonte,
valutazione di verità e decisione applicativa non sono lo stesso dato. Un'estrazione
fedele può riportare una dichiarazione errata; una decisione operativa può richiedere
criteri ulteriori rispetto a quanto afferma un documento.

**Operazioni ripetibili.** Ripetere una richiesta non deve creare duplicazioni
tecniche. Acquisire gli stessi input singolarmente o a lotti deve conservare il
significato, secondo criteri di confronto espliciti. Anche il percorso seguito
per produrre una risposta deve poter essere ispezionato.

Erano requisiti da dimostrare. Scriverli nella specifica non costituiva una prova
che il sistema li rispettasse.

## Anche le nostre ipotesi iniziali sono cambiate

All'inizio avevamo formulato alcune preferenze su come adattare componenti esistenti.
Nella revisione del 17 settembre abbiamo riaperto il confronto fra tre possibilità:
estensioni tramite adapter, modifiche circoscritte a un componente riutilizzato,
oppure un kernel autonomo con riuso selettivo.

La correzione metodologica è stata rendere queste alternative confrontabili rispetto
agli stessi invarianti. Il nome dell'architettura non garantisce la conservazione
della storia, l'esattezza temporale o la provenienza.

Il riuso può ridurre lavoro e manutenzione. Può anche richiedere adattamenti profondi
quando le semantiche non coincidono. Un kernel autonomo offre maggiore controllo,
ma comporta responsabilità e costi propri. La scelta doveva essere sostenuta da
riscontri concreti, senza presumere il vincitore prima delle prove.

## Dai requisiti a domande verificabili

La fase successiva avrebbe trasformato quelle promesse in casi controllati:

- Dopo una correzione, possiamo ancora ricostruire lo stato precedente?
- Se due fonti discordano, manteniamo entrambe le evidenze?
- Una prescrizione resta distinguibile da un evento osservato?
- Due percorsi di acquisizione preservano gli stessi contenuti e riferimenti?
- Un tentativo ripetuto o un errore parziale lascia effetti inattesi?

Sono domande abbastanza precise da poter fallire. Questo era il passaggio necessario
per distinguere un'intenzione architetturale da una capacità verificata.

Nella prossima puntata racconteremo come abbiamo preparato gli esperimenti:
input controllati, versioni fissate, risultati attesi e limiti di ciò che ciascuna
prova poteva dimostrare.
