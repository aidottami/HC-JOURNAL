# Dai documenti alla memoria verificabile: una giornata di costruzione dell’HC

**6 ottobre 2026 · HC Engineering Journal · 004**

*Dal laboratorio — resoconto del lavoro corrente. La serie cronologica “Il percorso” proseguirà separatamente.*

Oggi abbiamo lavorato su una domanda che attraversa tutto il nostro Hub Cognitivo:
come trasformare documenti aziendali in conoscenza interrogabile, conservando le
distinzioni necessarie per spiegare e correggere una risposta?

La giornata ha unito revisione umana, preparazione documentale, implementazione,
test e confronto architetturale. Il risultato centrale è un nuovo ledger locale:
un registro persistente di fonti, attestazioni e correzioni. Attorno a questo
risultato abbiamo chiarito il ruolo futuro del Clarificatore e aggiornato la
continuità del progetto.

## Prima del codice: concordare che cosa possiamo affermare

Il caso di lavoro comprende tre versioni sintetiche di una procedura di backup.
L’obiettivo RPO del gestionale passa da 24 a 4 e poi a 6 ore. RPO indica la perdita
massima di dati che la procedura intende tollerare, espressa come intervallo temporale.

Conservare quei tre valori è semplice. Interpretarli richiede più attenzione.
Una prescrizione non è una misura di ciò che accade davvero; una revisione esplicita
di una frequenza non dimostra la revoca generale di tutte le indicazioni precedenti.
Una riga assente dalla nuova tabella non autorizza a inventare uno zero o a ereditare
silenziosamente il vecchio valore.

Abbiamo quindi sottoposto a revisione umana otto criteri documentali: valori
attribuiti alle fonti, metriche distinte, revisioni, date, omissioni, condizioni,
disponibilità delle informazioni e limiti delle conclusioni sui possibili conflitti.
La loro approvazione ha preceduto l’implementazione.

## Un pacchetto documentale prima del ledger

Abbiamo preparato tre documenti, i relativi testi e metadati, e trenta annotazioni
manuali con citazioni verificabili. Le risposte attese per il confronto restano
separate dagli input documentali.

Questo ci permette di verificare la conservazione del significato senza confonderla
con la qualità di un modello di estrazione. Le verifiche di questo incremento
sono state eseguite offline, senza nuove chiamate a modelli linguistici.

La **provenance** è il percorso che consente di risalire da un record alla fonte,
alla sua versione, al passaggio citato e alla trasformazione applicata. Abbiamo
verificato questo percorso preservando anche modalità, condizioni e unità ignote.

## Correggere un’interpretazione senza riscrivere la fonte

Dopo l’approvazione del pacchetto e del contratto tecnico, abbiamo costruito il
ledger. Ogni importazione registra insieme contenuti, evento e ricevuta. Ripetere
una richiesta identica restituisce la stessa ricevuta senza duplicare i record.

Una nuova fonte può dichiarare un valore diverso. Una correzione del mapping,
invece, modifica il modo in cui abbiamo rappresentato una fonte già acquisita.
Sono operazioni con significati differenti.

Su una fixture sintetica separata abbiamo verificato che la correzione produca
una nuova revisione con predecessore, autore e motivazione. Il record precedente
e il documento restano consultabili. La vista corrente può selezionare la revisione
corretta, mentre una vista storica ricostruisce lo stato precedente.

Questo non sceglie una fonte vincente e non trasforma una correzione in un verdetto
universale di verità.

## Il tempo che conosciamo e quello che manca

Il ledger può ricostruire quali informazioni erano registrate dopo una transazione
o a un determinato istante del sistema.

La validità nel mondo descritto può invece restare ignota. La data stampata su una
procedura, quella presente nei metadati del PDF e quella di registrazione non sono
intercambiabili. Non abbiamo inventato intervalli di efficacia per colmare questa lacuna.

La bitemporalità completa resta un requisito più ampio. Oggi abbiamo verificato la
storia transazionale di questo perimetro, conservando esplicitamente l’incertezza
sulla validità temporale.

## I risultati e gli errori trovati

| Verifica | Risultato finale | Perimetro |
|---|---|---|
| Preparazione documentale | 20 test superati | Pacchetto, citazioni, validazione e ricostruzione |
| Ledger documentale | 18 test superati | Persistenza, correzioni, ricevute, query e replay |
| Riaperture del ledger | Cinque controlli in processi nuovi conformi | Letture dopo chiusura, inclusi errore precommit e successivo tentativo su nuova risorsa |
| Criteri documentali | Otto criteri ricontrollati sulle nuove viste | Attese revisionate da una persona, separate dal writer |

Sono verifiche complementari e in parte sovrapposte: non le sommiamo in un unico
punteggio di affidabilità.

Abbiamo anche alterato citazioni e ricevute su copie di prova, verificando che i
controlli rilevassero le incoerenze. Un errore applicativo prima del commit non ha
lasciato record canonici parziali nei casi esaminati.

I tentativi intermedi hanno trovato problemi reali di sviluppo: una guardia di
esecuzione troppo restrittiva nella preparazione, un errore SQL nel registro degli
esiti e un’attesa sbagliata nel test di una revisione documentale. Abbiamo corretto
codice e test conservando gli esiti precedenti, senza cambiare le fonti per far
passare le verifiche.

## Dove entra il Clarificatore

Abbiamo confrontato una proposta del co-founder con ciò che esiste già nell’HC.
L’orientamento condiviso è un modulo con responsabilità proprie, integrato nel
ciclo della conoscenza e inizialmente collocabile nella stessa applicazione.

Il Clarificatore potrà individuare ambiguità rilevanti, formulare domande e raccogliere
risposte attribuite a chi le fornisce. L’HC dovrà conservarle e controllare gli effetti
sulle interpretazioni. Il dubbio potrà riaprirsi anche dopo l’acquisizione, quando
una nuova fonte o una domanda lo rende evidente.

Se un documento menziona “Carlo”, un chiarimento dovrà riferirsi a quell’occorrenza:
non dovrà trasformarsi nella regola secondo cui ogni Carlo è la stessa persona.
E una risposta autorevole dovrà restare una risposta attribuita, distinta da una
verifica indipendente. È una precauzione contro l’**authority bias**: dare più peso
a un’affermazione per il ruolo di chi la sostiene che per le evidenze disponibili.
Non abbiamo ancora misurato questo bias né implementato il Clarificatore completo.

## Riuso e continuità fanno parte del lavoro

Abbiamo riesaminato segnalazioni su componenti esterni rispetto al passo corrente:
cancellazioni che lasciano tracce nelle rappresentazioni derivate, scope vuoti
instradati su un default e modifiche che combinano backend e routing.

Le abbiamo distinte dalle capacità necessarie ora e dalle prove richieste prima
di un eventuale riuso. Non abbiamo incorporato automaticamente patch o cambiato
le dipendenze. Il registro consultato è stato verificato; non abbiamo potuto
verificare la copertura degli eventuali aggiornamenti nella conversazione del monitoraggio.

Abbiamo inoltre riallineato documentazione operativa, riferimenti e checkpoint,
conservando materiali e risultati precedenti. L’obiettivo è poter riprendere il
lavoro sapendo che cosa è stato approvato, che cosa è stato verificato e che cosa
rimane soltanto una proposta.

## Che cosa resta aperto

Questo risultato riguarda dati sintetici, un ledger locale e un solo writer.
Restano da dimostrare rilevamento automatico delle contraddizioni, identità generali,
autorizzazioni aziendali, valid time completo, concorrenza, resistenza ai crash del
sistema operativo e prestazioni su larga scala.

Il prossimo passo operativo è la revisione della consegna e la definizione di
un’eventuale demo circoscritta. Il Clarificatore seguirà un contratto dedicato.

La domanda che portiamo avanti è: **quando una risposta cambia, possiamo mostrare
quali evidenze, interpretazioni o decisioni hanno prodotto quel cambiamento?**

---

[Indice del journal](../README.md)
