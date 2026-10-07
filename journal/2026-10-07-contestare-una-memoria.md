# Una memoria deve poter essere contestata, anche quando sembra coerente

**7 ottobre 2026 · HC Engineering Journal · 006**

*Scelte di progetto — un nuovo requisito approvato per la roadmap, ancora da implementare.*

Un documento contiene un’informazione sbagliata. Nessun’altra fonte la contraddice,
il testo è chiaro e il sistema lo rappresenta correttamente. Per mesi, tutto sembra
funzionare. Poi una persona segnala l’errore.

Questo caso pone un requisito preciso al nostro Hub Cognitivo: una persona deve
poter aprire una contestazione anche quando il sistema non ha rilevato alcuna
ambiguità o contraddizione. La coerenza fra le fonti disponibili non basta a
garantirne la correttezza.

## Due modi diversi di dire «è sbagliato»

Prendiamo un esempio interamente sintetico. Un verbale attribuisce a Paolo
l’approvazione di una consegna. In seguito arriva una segnalazione.

| Segnalazione | Che cosa vogliamo rappresentare |
|---|---|
| «Paolo non l’ha approvata: l’ha approvata Giulia.» | Una contestazione dell’affermazione originale e una nuova affermazione, da valutare separatamente |
| «Paolo non l’ha approvata, ma non sappiamo ancora chi sia stato.» | Una contestazione con ricostruzione alternativa esplicitamente sconosciuta |

Sapere che una ricostruzione è errata non implica conoscere quella corretta.
Chiedere sempre un valore sostitutivo spingerebbe a riempire il vuoto con una
supposizione. Vogliamo poter conservare quel vuoto e renderlo visibile.

Anche la prima segnalazione richiede cautela: respingere l’attribuzione a Paolo
non dimostra automaticamente quella a Giulia. Sono due giudizi distinti.

## La segnalazione deve avere un bersaglio preciso

«Quel documento è sbagliato» può indicare una frase, una data o una singola
attribuzione. La contestazione deve essere collegata all’affermazione pertinente,
alla sua versione, alla citazione e all’ambito interessato.

Se il bersaglio è ambiguo, il percorso previsto conserva la segnalazione e chiede
un chiarimento prima di associarla. Contestare una frase non respinge l’intero
documento. Correggere una versione non trasferisce silenziosamente il giudizio
a tutte le versioni successive.

È un requisito di **provenance**: poter ricostruire da dove proviene un giudizio
e a quale contenuto si riferisce esattamente.

## Ricevere, valutare e decidere

Il percorso da costruire distingue tre passaggi:

1. Ricevere la segnalazione, conservando autore, testo, motivazione ed evidenze disponibili.
2. Valutare la correttezza dell’affermazione contestata, registrando anche incertezze e dissensi.
3. Stabilire come quel giudizio influisce sull’uso operativo dell’informazione, secondo una policy e un mandato pertinenti.

Una persona può segnalare un errore anche senza allegare subito una prova.
L’assenza di prove deve restare visibile; la ricezione non equivale ad accettazione.

Qui entra il rischio di **authority bias**: attribuire maggiore credibilità a
un’affermazione soltanto per il ruolo di chi la pronuncia. Un manager può avere
l’autorità per adottare una decisione entro un progetto, ma quel mandato non
rende infallibile la sua ricostruzione dei fatti.

Per questo vogliamo conservare separatamente il contenuto della risposta,
le evidenze e l’autorità esercitata, con il relativo ambito e periodo. Anche il
giudizio accettato deve poter essere contestato successivamente.

## Correggere senza riscrivere il passato

Supponiamo che il verbale riguardi una consegna di marzo e che l’errore venga
segnalato a giugno. Il periodo descritto e il momento in cui il sistema apprende
la contestazione sono due informazioni differenti.

La **bitemporalità** serve a distinguere questi assi. Vogliamo poter chiedere sia
che cosa riteniamo sostenibile oggi riguardo a marzo, sia quali informazioni
fossero disponibili al sistema quando aveva risposto in aprile.

Il documento originale rimane intatto. «Il verbale attribuiva l’approvazione a
Paolo» può restare una descrizione corretta della fonte anche dopo che tale
attribuzione è stata respinta. Una risposta storica deve poter essere ricostruita
senza introdurvi conoscenze arrivate mesi dopo.

Occorre inoltre distinguere un’informazione giudicata falsa da una non supportata,
indeterminata, ritirata o semplicemente non più valida. Un cambio di incarico,
per esempio, non rende falso l’incarico precedente.

## Quali altre conclusioni vanno riesaminate?

L’attribuzione a Paolo potrebbe essere stata usata in un riepilogo o come premessa
di una decisione. La correzione interessa quindi anche le derivazioni note.

Vogliamo seguire la **lineage**, cioè il percorso dalle evidenze alle conclusioni,
per individuare i contenuti che dipendono dalla specifica affermazione contestata.
Quei contenuti devono essere segnalati per riesame, con una spiegazione del legame.

Non prevediamo un’invalidazione indiscriminata a cascata: una conclusione potrebbe
avere anche supporti indipendenti. E quando le dipendenze non sono completamente
tracciate, il sistema deve dichiarare il limite della verifica.

Nella consultazione ordinaria, un giudizio negativo adottato dovrà essere visibile:
l’affermazione respinta non potrà continuare a essere usata come premessa affidabile
senza qualificazione. Il trattamento delle contestazioni ancora pendenti resta
una scelta di policy da definire.

## Dove siamo e che cosa verificheremo

Abbiamo approvato questo requisito nella roadmap. Questo articolo non annuncia
una dashboard funzionante, un nuovo rilevatore o test già superati sulla
contestazione spontanea.

Il prossimo passo è delimitare il contratto e il percorso di verifica: segnalazioni
senza allarmi preesistenti, alternative note o ignote, bersagli ambigui, giudizi
discordanti, mandati contestuali e consultazione prima e dopo una rettifica.
Andrà verificato anche il riesame delle derivazioni con evidenze indipendenti.

La domanda aperta più immediata riguarda l’attesa: **come deve rispondere l’HC
quando un’informazione è contestata, ma la revisione non si è ancora conclusa?**
Conservare la segnalazione è il primo passo; definirne gli effetti sull’uso della
conoscenza richiede una scelta esplicita e verificabile.

---

[Indice del journal](../README.md)
