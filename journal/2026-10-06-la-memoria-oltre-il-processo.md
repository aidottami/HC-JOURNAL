# Una memoria verificabile deve sopravvivere al processo che l’ha creata

**6 ottobre 2026 · HC Engineering Journal · 005**

*Dal laboratorio — seguito della costruzione del ledger documentale.*

Nel precedente articolo abbiamo raccontato la costruzione di un registro locale
capace di conservare documenti, attestazioni e correzioni. Il passo successivo è
stato chiudere il processo che aveva scritto i dati e verificare che altri processi
potessero ricostruire esattamente le stesse viste.

Una risposta corretta durante l’esecuzione iniziale è un buon punto di partenza.
Per una memoria persistente serve anche poterla ritrovare, spiegare e ricostruire.

## Che cosa volevamo ritrovare

La dimostrazione usa tre versioni sintetiche di una procedura, trenta annotazioni
manuali e una fixture separata per una correzione. Le annotazioni conservano
valori, unità, modalità, condizioni e citazioni. Le attese della verifica restano
separate dagli input del sistema.

Abbiamo salvato sei viste: tre mostrano la disponibilità progressiva dei documenti;
le altre mostrano lo stato precedente alla correzione, la storia dopo la correzione
e la vista che seleziona la revisione corrente del mapping.

Il confronto comprende l’intera risposta strutturata: record, evidenze, ricevute,
tempi registrati e informazioni sulla vista richiesta. Ritrovare soltanto lo
stesso numero finale non sarebbe stato sufficiente.

Questa è una parte della **provenance**: poter seguire il percorso fra un risultato,
la fonte che lo sostiene e le trasformazioni che lo hanno prodotto.

## Il primo tentativo si è fermato prima della lettura

La fase di scrittura era riuscita. All’avvio del primo processo di lettura,
però, la guardia del coordinatore ha bloccato il lancio.

La regola consentiva una chiamata di avvio dell’interprete locale, ma ne vietava
il meccanismo sottostante effettivamente usato in quell’ambiente. Il processo
figlio non è mai partito: non aveva ancora interrogato il database.

Era un errore della nostra orchestrazione. Non forniva un risultato sul
comportamento del ledger dopo la chiusura del writer.

Abbiamo fermato la dimostrazione e conservato il tentativo. Le scritture riuscite
sono rimaste evidenze parziali; le letture e i replay mancanti sono rimasti tali.
Non abbiamo completato a posteriori il vecchio tentativo nascondendo lo stop.

## Correggere la guardia e verificare i confini

Abbiamo estratto la policy di lancio in un modulo versionato. Ora i due eventi
di avvio applicano lo stesso elenco esatto di comandi consentiti: interprete,
argomenti, ambiente e directory.

Prima di una nuova demo abbiamo eseguito una verifica isolata, senza database o
corpus. Tredici controlli del coordinatore e dieci controlli nei due processi figli
sono risultati conformi. Abbiamo verificato sia i lanci consentiti sia il rifiuto
di comandi diversi, shell, socket e risoluzione DNS; i figli rifiutano anche
l’avvio di ulteriori processi.

La verifica positiva ha attraversato realmente i due eventi coinvolti nel difetto.
La correzione ha quindi affrontato il percorso che aveva causato lo stop.

Si tratta di controlli Python per codice fidato. Non sono un firewall del sistema
operativo né una sandbox contro codice nativo ostile.

## La nuova demo: chiudere, rileggere, ricostruire

La nuova dimostrazione ha usato due destinazioni nuove e ha completato la sequenza.

| Operazione | Risultato |
|---|---|
| Registrazione | Cinque commit canonici: tre documentali e due sulla fixture |
| Viste salvate | Sei snapshot |
| Consultazione temporale | Tre confronti fra selezione per transazione e istante registrato conformi, salvo il selettore dichiarato |
| Criteri documentali | Otto criteri conformi alle attese revisionate |
| Letture dopo la chiusura del writer | Sei processi nuovi, risposte identiche agli snapshot |
| Ricostruzione dagli eventi | Sei replay in ulteriori processi nuovi, risultati identici alle rispettive viste |

I commit della tabella sono transazioni del registro applicativo. I conteggi
descrivono verifiche differenti e non costituiscono un punteggio aggregato di
affidabilità.

Il **replay deterministico**, nel perimetro verificato, ricostruisce le viste dagli
eventi conservati usando regole fissate. Preserva le ricevute e i tempi originali;
non chiede a un modello linguistico di generare nuovamente una risposta simile.

Sulla fixture, il passaggio da 4 a 6 crea una revisione collegata alla precedente,
con attore e motivazione. La fonte rimane invariata. La vista storica conserva
entrambi i record; quella corrente seleziona la revisione del mapping prevista
dalla policy. Questo non elegge una fonte vincente fra documenti discordanti.

## Rendere verificabile anche il racconto del lavoro

Abbiamo conservato i file del tentativo interrotto e quelli della demo riuscita,
con report e inventari separati. Un inventario elenca percorsi, dimensioni e hash;
il report spiega operazioni, risultati e limiti. Il codice dei test mostra le
asserzioni effettivamente controllate.

Resta un limite di ispezionabilità: la demo completa non dispone ancora di un
unico runner versionato. Le API, la guardia e i comandi dei processi di lettura e
replay sono fissati; parte dell’orchestrazione è stata eseguita nella sessione di
sviluppo. Il prossimo incremento proposto comprende un runner completo, affinché
il procedimento sia leggibile insieme ai risultati.

## Il confine del risultato

Abbiamo verificato un caso locale su dati sintetici e mapping manuale. Non abbiamo
misurato la qualità dell’estrazione LLM né dimostrato resistenza ai crash del sistema
operativo, concorrenza, autorizzazioni aziendali o prestazioni su larga scala.

La validità delle affermazioni nel mondo descritto resta esplicitamente ignota.
Conservare la storia delle registrazioni non completa da solo la bitemporalità.
Anche rilevamento generale delle contraddizioni e chiarificazione umana restano
capacità da costruire e verificare.

Il prossimo collegamento proposto porta dalle attestazioni a una consultazione
di affermazioni documentali qualificate, con accesso alle fonti e alla storia.
Non è ancora un’integrazione dimostrata.

La domanda che questa prova ci permette di affrontare con evidenze concrete è:
**quando il processo termina, quali parti della spiegazione possiamo ancora
ricostruire esattamente?**

---

[Indice del journal](../README.md)
