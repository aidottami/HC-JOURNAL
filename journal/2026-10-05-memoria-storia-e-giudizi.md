# Una memoria che cambia idea senza cancellare il passato

**5 ottobre 2026 · HC Engineering Journal · 001**

Una procedura aziendale indica un obiettivo di ripristino. Qualche mese dopo arriva
una nuova versione, con un valore diverso. Un revisore considera il cambiamento
una contraddizione; un altro lo interpreta come una revisione legittima.

Che cosa deve ricordare un Hub Cognitivo?

Per noi deve conservare le affermazioni, le evidenze da cui provengono e i giudizi
espressi su di esse. Deve anche permettere di ricostruire come questa conoscenza
è cambiata nel tempo.

## Il problema: “l'ultima risposta” non racconta tutta la storia

Sovrascrivere un valore può sembrare una soluzione semplice. Ma poi diventa difficile
spiegare perché una decisione precedente fosse ragionevole, quale documento fosse
disponibile in quel momento o chi avesse contestato una conclusione.

La nostra scelta progettuale è mantenere gli oggetti invalidati nella storia, insieme
alle evidenze e alle informazioni che motivano il loro cambiamento di stato.
Un'eventuale esclusione da una vista corrente deve essere esplicita e riconoscibile.
Conservare un oggetto non significa continuare a presentarlo come valido.

Anche il termine “invalidato” richiede precisione: un documento corretto, un'affermazione
non più applicabile e un giudizio respinto descrivono situazioni differenti.

## Tre distinzioni che guidano il lavoro

**Provenance.** Vogliamo poter risalire da un'affermazione alla fonte e alla versione
che la sostiene, distinguendo il testo originale dalle trasformazioni e dalle
valutazioni successive. Una citazione deve consentire una verifica.

**Bitemporalità.** La data a cui una prescrizione si riferisce e quella in cui il
sistema la apprende rispondono a domande diverse. “Che cosa sapevamo allora?” può
avere una risposta diversa da “Che cosa sappiamo oggi di quel periodo?”.
Non possiamo sostituire automaticamente una data con l'altra.

**Disaccordo fra valutazioni.** Se due revisori giudicano diversamente una possibile
contraddizione, conserviamo entrambi i giudizi. Quel disaccordo non dimostra, da solo,
che le affermazioni originarie siano incompatibili. E non autorizza il sistema a
cancellarne una o a scegliere autonomamente chi abbia ragione.

## Che cosa abbiamo verificato finora

Nel nostro verticale locale, su un corpus chiuso, abbiamo verificato la conservazione
di giudizi e revisioni e la ricostruzione dello stato tramite replay e riapertura degli
store. Un collegamento fra il percorso di acquisizione e quello di assessment ha
superato undici confronti fra elaborazione singola e a lotti, sui prefissi comuni
previsti dal protocollo.

Sono risultati circoscritti. Non dimostrano che il sistema sappia rilevare automaticamente
qualsiasi contraddizione, risolvere identità ambigue o stabilire la verità aziendale.
Non costituiscono una validazione su carichi di produzione. Le verifiche citate sono
milestone precedenti: oggi abbiamo svolto analisi documentale, senza nuovi run.

## Un caso sintetico che ci ha costretto a essere più precisi

Abbiamo confrontato tre versioni di una procedura di backup. L'obiettivo RPO del
gestionale passa da 24 a 4 e poi a 6 ore. La versione finale spiega il passaggio
da 4 a 6 ore, ma non contiene una clausola generale di revoca delle versioni precedenti.

Questo caso contiene almeno tre domande distinte:

- Quale valore dichiara ciascun documento?
- Quale cambiamento è spiegato esplicitamente nel testo?
- Quale procedura possiamo sostenere che sia applicabile, a una data precisa?

Le prime due hanno evidenze documentali dirette. La terza richiede anche una policy
sulla vigenza e informazioni sufficienti sul contesto. La parola “definitiva” nel
titolo è un'informazione della fonte: da sola non risolve ogni dubbio.

## Il prossimo passo

Abbiamo preparato otto casi candidati per la revisione umana: valori attribuiti alle
fonti, metriche distinte, revisioni esplicite, date discordanti, omissioni, condizioni,
conoscenza ai diversi momenti e possibili conflitti.

Il passo successivo è concordare le risposte ammissibili e le incertezze che devono
rimanere visibili, prima di trasformare questi casi in nuove verifiche del prodotto.

La domanda che ci guida è concreta: **possiamo spiegare una risposta senza perdere
la storia delle fonti e delle valutazioni che l'hanno resa possibile?**

---

[Indice del journal](../README.md)
