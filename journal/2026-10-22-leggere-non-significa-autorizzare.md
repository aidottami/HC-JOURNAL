# Leggere un documento non significa eseguirlo

22 ottobre 2026 · Pubblicato il 5 novembre 2026. Resoconto della fase indicata.

Un documento arriva nella memoria aziendale e contiene una frase apparentemente
semplice: «Concedere a Elena l'accesso alla risorsa X».

Che cosa deve fare il sistema? Conservare la frase? Bloccarla perché sembra
un'istruzione? Modificare davvero i permessi?

Questa domanda ci ha portato a un confine fondamentale del nostro lavoro:
comprendere una richiesta e avere l'autorità di eseguirla sono due cose diverse.

## La forma della frase non basta

La stessa istruzione può comparire in un manuale, in una richiesta legittima o
in un documento malevolo. Un filtro che blocca ogni imperativo rischia di impedire
il lavoro; un sistema che esegue ogni frase convincente rischia di concedere
poteri a chi non li possiede.

Neppure la firma di un responsabile nel testo basta. Il sistema deve verificare
chi sta chiedendo, in quale contesto e con quale mandato. È anche una difesa
contro l'authority bias: attribuire credibilità o potere a qualcosa soltanto
perché sembra provenire da una figura autorevole.

## Dalla frase a una proposta verificabile

Stiamo valutando un percorso in cui il documento produce una richiesta pendente,
con destinatario, risorsa, azione e durata espliciti. Un responsabile identificato
attraverso un canale fidato riceve una notifica e conferma nella dashboard,
autenticandosi e vedendo esattamente che cosa sta approvando.

La conferma deve riguardare quella precisa versione della richiesta. Se cambia
la risorsa o il destinatario, non può valere la vecchia approvazione. Aprire un
link non deve eseguire l'operazione. E l'autorità del responsabile deve essere
ancora valida quando la modifica viene applicata.

È una proposta da confrontare con altre opzioni: non abbiamo ancora scelto né
implementato questo flusso di conferma.

## Visibile soltanto quando è pronto

Abbiamo invece approvato il requisito di visibilità: una modifica entra nella
conoscenza consultabile soltanto come operazione completa. Se una componente
non ha terminato, non deve apparire una metà della nuova situazione.

Ogni interrogazione deve usare una vista coerente, mentre il sistema dichiara i
limiti di ciò che ha consultato. Una fonte pubblicata correttamente non significa
che la risposta copra tutto il patrimonio aziendale.

Questi sono contratti progettuali. La loro realizzazione attraverso più backend
richiede ancora prove: crash, timeout, aggiornamenti concorrenti e recupero.

## La scala deve essere provata

Stiamo preparando anche il confronto tra due collocazioni del registro di
pubblicazione: nel database a grafo oppure in un database relazionale separato.
Le prove previste partiranno da casi piccoli controllabili e cresceranno verso
carichi sintetici rappresentativi, includendo revisioni, email ed eventi aziendali.

Non abbiamo ancora risultati di questa campagna. Il numero di documenti da solo
non basta: contano collegamenti, revisioni, distribuzione delle query e guasti.
La velocità non compensa una concessione di accesso errata o una storia perduta.

La domanda aperta è come conciliare conferme sicure e operatività quotidiana,
soprattutto quando una revoca è urgente. Il prossimo lavoro riguarda temporalità,
copertura delle risposte e recupero dai guasti, per poi chiudere il modello dei
permessi e verificare i contratti scelti.

## Aggiornamento alla pubblicazione — 5 novembre 2026

Il testo precedente racconta le scelte ancora aperte il 22 ottobre. Nel frattempo
abbiamo approvato il contratto dei permessi e verificato offline la conferma
esplicita della richiesta esatta, il controllo del mandato e l'ordinamento fra
revoca e consegna. Il percorso con email e dashboard resta da realizzare;
le verifiche offline non dimostrano ancora il comportamento del sistema reale.
Gli esiti e i limiti sono raccontati in [Quando l'esito di una revoca è incerto](2026-11-04-addendum-permessi.md).
